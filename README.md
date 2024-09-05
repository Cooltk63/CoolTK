public ResponseEntity<ResponseVO<Map<String, Object>>> saveStaticDetails(Map<String, Object> map) {

    // Extracting additional details from the input map
    Map<String, Object> data = (Map<String, Object>) map.get("data");

    // Extracting logged user data
    Map<String, String> loginUserData = (Map<String, String>) map.get("user");

    // Getting submission ID from the data map
    String submissionId = String.valueOf(data.get("submissionId"));

    // Initializing response object
    ResponseVO<Map<String, Object>> responseVO = new ResponseVO<>();
    Map<String, Object> resultDataMap = new HashMap<>();

    // List of ROW data (List<List<String>> format)
    List<List<String>> mainList = (List<List<String>>) data.get("value");

    try {
        // Parse the quarterEndDate from user data
        SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
        Date liabilityDate = dateFormat.parse(loginUserData.get("quarterEndDate"));

        log.info("Liability Date: " + liabilityDate);
        log.info("Main List Data: " + mainList);

        // Process each list (row) inside the main list
        for (List<String> dataList : mainList) {

            // Set the ROW-ID (Liability ID)
            String crsLiabilityId = String.valueOf(Integer.parseInt(dataList.get(7)));
            log.info("crsLiabilityId: " + crsLiabilityId);

            // Check if an entity with the given params exists in the database
            CrsLiability existingEntity = crsLiabilityRepository.findByLiabilityDateAndLiabilityBranchAndCrsLiabilityId(
                    liabilityDate, loginUserData.get("branch_code"), crsLiabilityId);

            // If no existing entity, create a new one
            if (existingEntity == null) {
                log.info("No existing entity found. Inserting new record.");
                CrsLiability newEntity = setEntity(dataList, loginUserData.get("quarterEndDate"), 
                        loginUserData.get("branch_code"), submissionId);
                crsLiabilityRepository.save(newEntity);

            } else {
                // Update existing entity if it exists
                log.info("Existing entity found. Updating record.");

                // Update fields
                existingEntity.setLiabilityLstYs(dataList.get(1));  // Opening provision
                existingEntity.setLiabilityAddition(dataList.get(2));  // Additions during the period
                existingEntity.setLiabilityReversal(dataList.get(3));  // Reversals during the period
                existingEntity.setLiabilityCurYr(dataList.get(4));  // Provision as of 30/06/2024
                existingEntity.setLiabilityDiff(dataList.get(5));  // Difference to be provided/written back
                existingEntity.setLiabilityBranch(loginUserData.get("branch_code"));
                existingEntity.setLiabilityDate(liabilityDate);

                // Save the updated entity
                crsLiabilityRepository.save(existingEntity);
            }
        }

        // If all records processed successfully
        responseVO.setMessage("All data updated successfully.");
        resultDataMap.put("status", true);
        responseVO.setResult(resultDataMap);
        responseVO.setStatusCode(HttpStatus.OK.value());

    } catch (ParseException e) {
        // Handle date parsing errors
        log.error("Error parsing date: " + e.getMessage());
        responseVO.setMessage("Invalid date format provided.");
        resultDataMap.put("status", false);
        responseVO.setResult(resultDataMap);
        responseVO.setStatusCode(HttpStatus.BAD_REQUEST.value());

    } catch (RuntimeException e) {
        // Handle unexpected runtime exceptions
        log.error("Exception occurred: " + e.getMessage(), e);
        responseVO.setMessage("An unexpected error occurred.");
        resultDataMap.put("status", false);
        responseVO.setResult(resultDataMap);
        responseVO.setStatusCode(HttpStatus.INTERNAL_SERVER_ERROR.value());
    }

    // Return response in the specified format
    return new ResponseEntity<>(responseVO, HttpStatus.valueOf(responseVO.getStatusCode()));
}

// Helper method to create a new CrsLiability entity from the row data
public CrsLiability setEntity(List<String> dataList, String quarterEndDate, String branchCode, String submissionId) {
    CrsLiability entity = new CrsLiability();

    try {
        SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
        Date parsedDate = dateFormat.parse(quarterEndDate);

        // Setting entity fields based on the row data
        entity.setLiabilityParticulars(dataList.get(0));  // Particulars
        entity.setLiabilityLstYs(dataList.get(1));  // Opening provision
        entity.setLiabilityAddition(dataList.get(2));  // Additions during the period
        entity.setLiabilityReversal(dataList.get(3));  // Reversals during the period
        entity.setLiabilityCurYr(dataList.get(4));  // Provision as of 30/06/2024
        entity.setLiabilityDiff(dataList.get(5));  // Difference to be provided/written back
        entity.setCrsLiabilityId(dataList.get(7));  // ROW ID

        // User data
        entity.setReportMasterListIdfk(submissionId);
        entity.setLiabilityBranch(branchCode);
        entity.setLiabilityDate(parsedDate);

    } catch (ParseException e) {
        throw new RuntimeException(e);
    }

    return entity;
}