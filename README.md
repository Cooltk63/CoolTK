This is the JSON data i have received :

{
    "user": {
        "quarterEndDate": "30/06/2020",
        "branch_code": "64654"

    },
    "data": {
    
        "value":["444.2564","88888.2546","21","21","true"],
        "submissionId":"555451"
    }
}


below is function for saving data to DB 
 
 // For Saving SBLC ::: HEDGE_INV
    public ResponseEntity saveSblc(Map<String, Object> map) {

        //For getting additional Details other than User Details
        Map<String, Object> data = (Map<String, Object>) map.get("data");

        //For Logged User Data
        Map<String, String> loginUserData = (Map<String, String>) map.get("user");

        String submissionId = String.valueOf(data.get("submissionId"));
        try {

            //List of ROW Data
            List<String> dataList = (List<String>) data.get("value");

            log.info("dataList Recieved :"+dataList);


            SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
            Date parsedDate = dateFormat.parse(loginUserData.get("quarterEndDate"));


            Date SBLCDate = dateFormat.parse(dataList.get(0));
            CRS_HedgeInv entity = new CRS_HedgeInv();


            // Assign form data to Bean for Save
            entity.setHedgeinv_branch(loginUserData.get("branch_code"));
            entity.setHedgeinv_date(parsedDate);


            // "hedgeInvDate"
            entity.setHedgeinv_invdate(SBLCDate); //0

            // "hedgePan"
            entity.setHedgeinv_pan(dataList.get(1)); //1

            // "hedgeCustomer"
            entity.setHedgeinv_customer(dataList.get(2)); //2

            // "hedgeAmount"
            entity.setHedgeinv_amount(dataList.get(3)); //3

            // "submissionId"
            entity.setHedgeInvReporMastertFK(Integer.parseInt(submissionId));

            // Check if ROW -ID is empty or null for insert scenario
            if (dataList.get(4).trim().isEmpty() || dataList.get(5) == null) {
                log.info("Entity Data for Insert: " + entity);

                CRS_HedgeInv crsHedgeInv = crsHedgeInvRepository.save(entity);
                log.info("CRSHedgeInv saved to database" + crsHedgeInv.getHedgeinvId());
                // Sending data to response MAP
                Map<String, Object> resultDataMap = new HashMap<>();
                resultDataMap.put("status", true);
                resultDataMap.put("newRowNum", crsHedgeInv.getHedgeinvId());
                resultDataMap.put("newId", crsHedgeInv.getHedgeinvId());

                ResponseVO<Map<String, Object>> responseVO = new ResponseVO();
                responseVO.setStatusCode(HttpStatus.OK.value());
                responseVO.setMessage("Data Inserted successfully");
                responseVO.setResult(resultDataMap);
//                responseVO.setResult(String.valueOf(savedEntity.getStndassetsseq()));
                return new ResponseEntity<>(responseVO, HttpStatus.OK);
            } else {
                // ID is provided, check for existence and update
                int id = Integer.parseInt(dataList.get(5));
                log.info("Received ID for Update: " + id + " Is ID Existed :" + crsHedgeInvRepository.existsByhedgeinvId(id));
                ResponseVO<Map<String, Object>> responseVO = new ResponseVO();
                Map<String, Object> resultDataMap = new HashMap<>();
                if (crsHedgeInvRepository.existsByhedgeinvId(id)) {

                    // Update existing row
                    entity.setHedgeinvId(id);  // Set the ID for update

                    CRS_HedgeInv crsHedgeInv = crsHedgeInvRepository.save(entity);
                    log.info("Data Updated successfully: " + crsHedgeInv);

                    resultDataMap.put("status", true);
                    resultDataMap.put("newRowNum", entity.getHedgeinvId());
                    resultDataMap.put("newId", entity.getHedgeinvId());

                    responseVO.setStatusCode(HttpStatus.OK.value());
                    responseVO.setMessage("Data Updated successfully");
                    responseVO.setResult(resultDataMap);
                    return new ResponseEntity<>(responseVO, HttpStatus.OK);
                } else {
                    // ID not found, handle error
                    log.info("ID " + id + " not found for update");
                    responseVO.setStatusCode(HttpStatus.BAD_REQUEST.value());
                    responseVO.setMessage("Invalid ID provided. Record not found.");
                    resultDataMap.put("status", false);
                    responseVO.setResult(resultDataMap);
                    return new ResponseEntity<>(responseVO, HttpStatus.BAD_REQUEST);
                }
            }

        } catch (RuntimeException e) {
            ResponseVO<String> responseVO = new ResponseVO();
            log.info("Exception Occurred :" + e.getCause());
            responseVO.setResult("false");
            responseVO.setStatusCode(HttpStatus.INTERNAL_SERVER_ERROR.value());
            responseVO.setMessage("Exception Occurred: " + e.getMessage());
            return new ResponseEntity<>(responseVO, HttpStatus.INTERNAL_SERVER_ERROR);
        } catch (ParseException e) {
            throw new RuntimeException(e);
        }

    }


I am facing the issue that this is the single static row save functionality but whenever i trying to edit and save every time new row inserted in db insted of updating same row how can i solve this issue by using the quarterEndDate and branch_code to identiry the data  is alredy existed in db if present then update that row else insert the new row but make sure do not make any changes related to any keys which i am getting from json data and comment each and every line with proper explantion
