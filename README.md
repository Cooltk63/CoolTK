// For Saving SBLC ::: HEDGE_INV
public ResponseEntity saveSblc(Map<String, Object> map) {

    // Extracting data map from input JSON
    Map<String, Object> data = (Map<String, Object>) map.get("data");

    // Extracting user details from input JSON
    Map<String, String> loginUserData = (Map<String, String>) map.get("user");

    // Parsing submissionId from data map
    String submissionId = String.valueOf(data.get("submissionId"));

    try {
        // List of data values (assuming "value" array is always provided)
        List<String> dataList = (List<String>) data.get("value");

        log.info("dataList Received: " + dataList);

        // Date format for parsing date values
        SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");

        // Parsing quarterEndDate from user data
        Date parsedQuarterEndDate = dateFormat.parse(loginUserData.get("quarterEndDate"));

        // Setting entity data with parsed details
        CRS_HedgeInv entity = new CRS_HedgeInv();
        entity.setHedgeinv_branch(loginUserData.get("branch_code"));
        entity.setHedgeinv_date(parsedQuarterEndDate);

        // Parsing additional date from data list (index 0)
        Date SBLCDate = dateFormat.parse(dataList.get(0));
        entity.setHedgeinv_invdate(SBLCDate); // hedgeInvDate

        entity.setHedgeinv_pan(dataList.get(1));      // hedgePan
        entity.setHedgeinv_customer(dataList.get(2)); // hedgeCustomer
        entity.setHedgeinv_amount(dataList.get(3));   // hedgeAmount
        entity.setHedgeInvReporMastertFK(Integer.parseInt(submissionId)); // submissionId

        // Check if a row with the same quarterEndDate and branch_code already exists
        Optional<CRS_HedgeInv> existingEntity = crsHedgeInvRepository
                .findByHedgeinv_branchAndHedgeinv_date(loginUserData.get("branch_code"), parsedQuarterEndDate);

        if (existingEntity.isPresent()) {
            // Row exists, so perform an update
            entity.setHedgeinvId(existingEntity.get().getHedgeinvId()); // Set ID to update
            CRS_HedgeInv updatedEntity = crsHedgeInvRepository.save(entity);
            log.info("Data Updated successfully: " + updatedEntity);

            // Prepare response with updated entity details
            Map<String, Object> resultDataMap = new HashMap<>();
            resultDataMap.put("status", true);
            resultDataMap.put("newRowNum", updatedEntity.getHedgeinvId());
            resultDataMap.put("newId", updatedEntity.getHedgeinvId());

            ResponseVO<Map<String, Object>> responseVO = new ResponseVO<>();
            responseVO.setStatusCode(HttpStatus.OK.value());
            responseVO.setMessage("Data Updated successfully");
            responseVO.setResult(resultDataMap);
            return new ResponseEntity<>(responseVO, HttpStatus.OK);
        } else {
            // Row doesn't exist, so perform an insert
            CRS_HedgeInv newEntity = crsHedgeInvRepository.save(entity);
            log.info("CRSHedgeInv saved to database: " + newEntity.getHedgeinvId());

            // Prepare response with new entity details
            Map<String, Object> resultDataMap = new HashMap<>();
            resultDataMap.put("status", true);
            resultDataMap.put("newRowNum", newEntity.getHedgeinvId());
            resultDataMap.put("newId", newEntity.getHedgeinvId());

            ResponseVO<Map<String, Object>> responseVO = new ResponseVO<>();
            responseVO.setStatusCode(HttpStatus.OK.value());
            responseVO.setMessage("Data Inserted successfully");
            responseVO.setResult(resultDataMap);
            return new ResponseEntity<>(responseVO, HttpStatus.OK);
        }

    } catch (ParseException e) {
        throw new RuntimeException(e);
    } catch (RuntimeException e) {
        ResponseVO<String> responseVO = new ResponseVO<>();
        log.info("Exception Occurred: " + e.getCause());
        responseVO.setResult("false");
        responseVO.setStatusCode(HttpStatus.INTERNAL_SERVER_ERROR.value());
        responseVO.setMessage("Exception Occurred: " + e.getMessage());
        return new ResponseEntity<>(responseVO, HttpStatus.INTERNAL_SERVER_ERROR);
    }
}