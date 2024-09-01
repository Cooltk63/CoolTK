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
            // Check if the dataList has at least 10 elements
            if (dataList.size() < 10) {
                log.info("Insufficient data in list: " + dataList);
                continue; // Skip to the next list
            }

            String branchCode = (String) loginUserData.get("branch_code");
            String serialAssetsId = dataList.get(9); // 9th index (10th element)

            // Fetch existing entity based on composite key: quarterEndDate, branchCode, serialAssetsId
            CRS_Othassests entity = crsOthassestsRepository.findByAssestsdateAndAssestsbranchAndSerialassestsid(
                    parsedDate, branchCode, serialAssetsId);

            if (entity != null) {
                // Update the entity with new data from the current list
                entity.setParticulars(dataList.get(0));
                entity.setProvisionableamount(dataList.get(1));
                entity.setWriteoffduring3months(dataList.get(2));
                entity.setAddinprovamount3months(dataList.get(3));
                entity.setReductioninprovamount3months(dataList.get(4));
                entity.setProvamtresult(dataList.get(5));
                entity.setRateofprovision(dataList.get(6));
                entity.setProvisionrequirement(dataList.get(7));
                entity.setOthassestssq(dataList.get(8));
                entity.setSerialassestsid(dataList.get(9));

                // Set additional user data fields
                entity.setAssestsbranch(branchCode);
                entity.setAssestsdate(parsedDate);
                entity.setReportmasteridfk(Integer.parseInt(submissionId));

                // Check if the entity with the serialAssetsId exists in the database
                if (crsOthassestsRepository.existsByserialassestsid(serialAssetsId)) {
                    // Save the updated entity
                    CRS_Othassests updatedEntity = crsOthassestsRepository.save(entity);
                    log.info("Data updated successfully for ID: " + serialAssetsId);

                    // Set response details for a successful update
                    resultDataMap.put("status", true);
                    resultDataMap.put("newRowNum", updatedEntity.getSerialassestsid());
                    responseVO.setStatusCode(HttpStatus.OK.value());
                    responseVO.setMessage("Data updated successfully");
                    responseVO.setResult(resultDataMap);
                    return new ResponseEntity<>(responseVO, HttpStatus.OK);
                } else {
                    // Handle case where ID is not found for update
                    log.info("ID " + serialAssetsId + " not found for update");
                    responseVO.setMessage("Invalid ID provided. Record not found.");
                    resultDataMap.put("status", false);
                    responseVO.setResult(resultDataMap);
                    responseVO.setStatusCode(HttpStatus.BAD_REQUEST.value());
                    return new ResponseEntity<>(responseVO, HttpStatus.BAD_REQUEST);
                }
            } else {
                // Entity not found for the given key combination
                log.info("Entity not found for Date: " + parsedDate + ", Branch: " + branchCode + ", ID: " + serialAssetsId);
            }
        }

        // If no valid records were processed for update
        responseVO.setMessage("No valid records to update.");
        resultDataMap.put("status", false);
        responseVO.setResult(resultDataMap);
        responseVO.setStatusCode(HttpStatus.BAD_REQUEST.value());

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