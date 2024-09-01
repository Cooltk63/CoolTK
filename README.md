public ResponseEntity<ResponseVO<Map<String, Object>>> saveStaticData(Map<String, Object> map) {
    // Extract data from the incoming request map
    Map<String, Object> data = (Map<String, Object>) map.get("data");
    Map<String, Object> loginUserData = (Map<String, Object>) map.get("user");

    // Retrieve submission ID from data map
    String submissionId = String.valueOf(data.get("submissionId"));

    // Initialize the response object
    ResponseVO<Map<String, Object>> responseVO = new ResponseVO<>();
    Map<String, Object> resultDataMap = new HashMap<>();

    try {
        // List of ROW Data from the incoming request
        List<List<String>> mainList = (List<List<String>>) data.get("value");

        // Parse the quarterEndDate from the user data
        SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
        Date parsedDate = dateFormat.parse((String) loginUserData.get("quarterEndDate"));

        // Process each list (row) inside the main list
        for (List<String> dataList : mainList) {
            if (dataList.size() < 10) {
                log.info("Insufficient data in list: " + dataList);
                continue; // Skip to the next list
            }

            String branchCode = (String) loginUserData.get("branch_code");
            String serialAssetsId = dataList.get(9); // 9th index (10th element)

            // Fetch existing entity based on composite key: quarterEndDate, branchCode, serialAssetsId
            CRS_Othassests existingEntity = crsOthassestsRepository.findByAssestsdateAndAssestsbranchAndSerialassestsid(
                    parsedDate, branchCode, serialAssetsId);

            if (existingEntity != null) {
                // Update the existing entity
                existingEntity.setParticulars(dataList.get(0));
                existingEntity.setProvisionableamount(dataList.get(1));
                existingEntity.setWriteoffduring3months(dataList.get(2));
                existingEntity.setAddinprovamount3months(dataList.get(3));
                existingEntity.setReductioninprovamount3months(dataList.get(4));
                existingEntity.setProvamtresult(dataList.get(5));
                existingEntity.setRateofprovision(dataList.get(6));
                existingEntity.setProvisionrequirement(dataList.get(7));
                existingEntity.setOthassestssq(dataList.get(8));
                existingEntity.setSerialassestsid(dataList.get(9));

                // Set additional user data fields
                existingEntity.setAssestsbranch(branchCode);
                existingEntity.setAssestsdate(parsedDate);
                existingEntity.setReportmasteridfk(Integer.parseInt(submissionId));

                // Save the updated entity in the database
                try {
                    crsOthassestsRepository.save(existingEntity);
                    log.info("Data updated successfully for ID: " + serialAssetsId);
                } catch (DataIntegrityViolationException e) {
                    log.error("Unique constraint violation while updating ID: " + serialAssetsId, e);
                    responseVO.setMessage("Unique constraint violation. Unable to update record.");
                    resultDataMap.put("status", false);
                    responseVO.setResult(resultDataMap);
                    responseVO.setStatusCode(HttpStatus.BAD_REQUEST.value());
                    return new ResponseEntity<>(responseVO, HttpStatus.BAD_REQUEST);
                }

            } else {
                // If no entity is found, log the error and set response message accordingly
                log.info("No existing record found for ID: " + serialAssetsId + ", branchCode: " + branchCode + ", quarterEndDate: " + parsedDate);
                responseVO.setMessage("No existing record found for the provided details.");
                resultDataMap.put("status", false);
                responseVO.setResult(resultDataMap);
                responseVO.setStatusCode(HttpStatus.BAD_REQUEST.value());
                return new ResponseEntity<>(responseVO, HttpStatus.BAD_REQUEST);
            }
        }

        // If all records processed successfully
        responseVO.setMessage("All data updated successfully.");
        resultDataMap.put("status", true);
        responseVO.setResult(resultDataMap);
        responseVO.setStatusCode(HttpStatus.OK.value());

    } catch (ParseException e) {
        // Handle date parsing errors
        log.error("Error parsing date: " + e.getMessage(), e);
        responseVO.setMessage("Invalid date format provided.");
        resultDataMap.put("status", false);
        responseVO.setResult(resultDataMap);
        responseVO.setStatusCode(HttpStatus.BAD_REQUEST.value());
    } catch (RuntimeException e) {
        // Handle unexpected runtime exceptions
        log.error("Exception occurred: " + e.getMessage(), e);
        resultDataMap.put("status", false);
        responseVO.setResult(resultDataMap);
        responseVO.setStatusCode(HttpStatus.INTERNAL_SERVER_ERROR.value());
        responseVO.setMessage("An unexpected error occurred.");
    }

    // Common return statement for all cases
    return new ResponseEntity<>(responseVO, HttpStatus.valueOf(responseVO.getStatusCode()));
}