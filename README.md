  public ResponseEntity saveStaticDetails(Map<String,Object> map) {

        //For getting additional Details other than User Details
        Map<String, Object> data = (Map<String, Object>) map.get("data");

        //For Logged User Data
        Map<String, String> loginUserData = (Map<String, String>) map.get("user");

        String submissionId = String.valueOf(data.get("submissionId"));

        // Initialize the response object
        ResponseVO<Map<String, Object>> responseVO = new ResponseVO<>();
        Map<String, Object> resultDataMap = new HashMap<>();
        CrsLiability crsLiability =new CrsLiability();


        //List of ROW Data
        List<List<String>> mainList = (List<List<String>>) data.get("value");

        try {

            // Parse the quarterEndDate from the user data
            SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
            Date libalitydate = dateFormat.parse(loginUserData.get("quarterEndDate"));


            log.info("LibalityDate: "+libalitydate);

            log.info("Main List Data: "+mainList);
            // Process each list (row) inside the main list
            for (List<String> dataList : mainList) {

                // Here we set the ROW-ID
                String crsLiabilityId = String.valueOf(Integer.parseInt(dataList.get(7)));

                log.info("crsLiabilityId: "+crsLiabilityId);


                // Find Existing Entity Data
                CrsLiability existingentity = crsLiabilityRepository.findByLiabilityDateAndLiabilityBranchAndCrsLiabilityId(libalitydate, loginUserData.get("branch_code"),crsLiabilityId);

                if (existingentity == null) {
                    log.info("Inside existing entity == null");
                    crsLiability = setEntity( dataList, (String) loginUserData.get("quarterEndDate"), (String) loginUserData.get("branch_code"), (String) data.get("submissionId"));
                    // update the data for existing entity in the database
                        crsLiabilityRepository.save(crsLiability);

                } else {
                    log.info("Inside Else Block");
                    //Opening Provision as on 01-04-2023
                    existingentity.setLiabilityLstYs(dataList.get(1));

                    //Additions during the period
                    existingentity.setLiabilityAddition(dataList.get(2));

                    // Reversals during the Period
                    existingentity.setLiabilityReversal(dataList.get(3));


                    //Provision as on 30/06/2024 (6)={(3+4)-(5)}
                    existingentity.setLiabilityCurYr(dataList.get(4));

                    // Difference to be Provided/ written back (7)={(6)-(3)}
                    existingentity.setLiabilityDiff(dataList.get(5));

                    // User Data
//                    entity.setReportMasterListIdfk(submissionId);

                    existingentity.setLiabilityBranch(loginUserData.get("branch_code"));

                    existingentity.setLiabilityDate(libalitydate);

                    // update the data for existing entity in the database
                    crsLiabilityRepository.save(existingentity);
                    resultDataMap.put("status", true);
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
        log.info("Error parsing date: " + e.getMessage());
        responseVO.setMessage("Invalid date format provided.");
        resultDataMap.put("status", false);
        responseVO.setResult(resultDataMap);
        responseVO.setStatusCode(HttpStatus.BAD_REQUEST.value());
    }
    catch (RuntimeException e) {
        // Handle unexpected runtime exceptions
        log.info("Exception occurred: " + e.getMessage());
        e.printStackTrace();
        resultDataMap.put("status", false);
        responseVO.setResult(resultDataMap);
        responseVO.setStatusCode(HttpStatus.INTERNAL_SERVER_ERROR.value());
        responseVO.setMessage("An unexpected error occurred.");
    }

    // Common return statement for all cases
        return new ResponseEntity<>(responseVO, HttpStatus.valueOf(responseVO.getStatusCode()));
    }

    // This is SetENtity Method 
     public CrsLiability setEntity(List<String> dataList, String quarterEndDate,String branch_code,String submissionId ) {

        CrsLiability entity=new CrsLiability();

        try {
            SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
            Date parsedDate = dateFormat.parse(quarterEndDate);

            //Particulars
            entity.setLiabilityParticulars(dataList.get(0));

            //Opening Provision as on 01-04-2023
            entity.setLiabilityLstYs(dataList.get(1));

            //Additions during the period
            entity.setLiabilityAddition(dataList.get(2));

            // Reversals during the Period
            entity.setLiabilityReversal(dataList.get(3));

            //Provision as on 30/06/2024 (6)={(3+4)-(5)}
            entity.setLiabilityCurYr(dataList.get(4));

            // Difference to be Provided/ written back (7)={(6)-(3)}
            entity.setLiabilityDiff(dataList.get(5));

            // User ROW ID
            entity.setCrsLiabilityId(dataList.get(7));

            // User Data
            entity.setReportMasterListIdfk(submissionId);
            entity.setLiabilityBranch(branch_code);
            entity.setLiabilityDate(parsedDate);
        } catch (ParseException e) {
            throw new RuntimeException(e);
        }

        return entity;
    }


    I wanted the code for saveStaticDetails method to perform the operation on db where 
    CrsLiability existingentity = crsLiabilityRepository.findByLiabilityDateAndLiabilityBranchAndCrsLiabilityId(libalitydate, loginUserData.get("branch_code"),crsLiabilityId);

    using this entity object i waned to check if any exitsing data in db with given input param if that return some data then update that entity with my given values while is values contains 
    //List of ROW Data
        List<List<String>> mainList = (List<List<String>>) data.get("value");

        I am alredy using the for loop for iterating list but my code wont work or insert multiple list i am passing inside List of List only insert single lis.

        after that if existingentity return null or empty that means no data present in db against my ven param then insert the data which i am getting inside the list or list. given me code with proper comments.
