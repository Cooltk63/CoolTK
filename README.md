 public ResponseEntity saveStaticData(Map<String, Object> map) {


        // Data Receive here
        Map<String, Object> data = (Map<String, Object>) map.get("data");
        Map<String, Object> loginUserData = (Map<String, Object>) map.get("user");


        String submissionId = String.valueOf(data.get("submissionId"));
        HttpStatus StatusCode =HttpStatus.BAD_REQUEST;
        ResponseVO<Map<String, Object>> responseVO = new ResponseVO<>();
        Map<String, Object> resultDataMap = new HashMap<>();

        try {
            //List of ROW Data
            List<List<String>> mainList = (List<List<String>>) data.get("value");
//            CRS_Othassests entity = new CRS_Othassests();

            SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
            Date parsedDate = dateFormat.parse((String) loginUserData.get("quarterEndDate"));



            for (List<String> dataList : mainList) {

                CRS_Othassests entity = crsOthassestsRepository.findByAssestsdateAndAssestsbranchAndSerialassestsid(parsedDate,
                        (String) loginUserData.get("branch_code"),
                        dataList.get(9));

                if (entity!=null) {
                    //List Data
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

                    //User Data
                    entity.setAssestsbranch((String) loginUserData.get("branch_code"));
                    entity.setAssestsdate(parsedDate);
                    entity.setReportmasteridfk(Integer.parseInt(submissionId));

                    // ID is provided, check for existence and update
                    String id = dataList.get(9);
                    log.info("Received ID for Update: " + id + " Is ID Existed :" + crsOthassestsRepository.existsByserialassestsid(String.valueOf(id)));

                    if (crsOthassestsRepository.existsByserialassestsid(id)) {
                        // Update existing row
                        entity.setSerialassestsid(String.valueOf(id));  // Set the ID for update

                        CRS_Othassests updatedEntity = crsOthassestsRepository.save(entity);
                        log.info("Data Updated successfully: " + updatedEntity);

                        resultDataMap.put("status", true);
                        resultDataMap.put("newRowNum", updatedEntity.getSerialassestsid());

                        responseVO.setStatusCode(HttpStatus.OK.value());
                        responseVO.setMessage("Data Updated successfully");
                        responseVO.setResult(resultDataMap);
                        StatusCode = HttpStatus.OK;
                        return new ResponseEntity<>(responseVO, HttpStatus.OK);
                    } else {
                        // ID not found, handle error
                        log.info("ID " + id + " not found for update");
                        responseVO.setStatusCode(HttpStatus.BAD_REQUEST.value());
                        responseVO.setMessage("Invalid ID provided. Record not found.");
                        resultDataMap.put("status", false);
                        responseVO.setResult(resultDataMap);
                        StatusCode = HttpStatus.BAD_REQUEST;
                    }

                }
            }
        } catch(RuntimeException e){
            log.info("Exception Occurred :" + e.getCause());
            log.info("Exception Occurred :" + e.getMessage());
            resultDataMap.put("status", false);
            responseVO.setResult(resultDataMap);
            StatusCode=HttpStatus.INTERNAL_SERVER_ERROR;
            responseVO.setStatusCode(HttpStatus.INTERNAL_SERVER_ERROR.value());
        }
        catch(ParseException e){
            throw new RuntimeException(e);
        }
        return new ResponseEntity<>(responseVO,StatusCode);
    }
