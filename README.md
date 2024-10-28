This is repository interface using JPA
@Query(nativeQuery = true,value = "update REPORT_SUBMISSION set CURRENT_STATUS=:CURRENT_STATUS where SUBMISSION_ID=:SUBMISSION_ID")
   Boolean acceptAndRejectReport(
                        @Param("CURRENT_STATUS") String CURRENT_STATUS,
                        @Param("SUBMISSION_ID") int SUBMISSION_ID);


                        This is mail service impl function

                        // Accepting Report & Change RMl Status
    @Override
    public ResponseEntity acceptReport(Map<String, Object> map) {

        Map<String, String> loginUserData = (Map<String, String>) map.get("user");
        Map<String, String> data = (Map<String, String>) map.get("data");

        log.info("loginUserData Map Values :"+loginUserData);
        log.info("data Map Values :"+data);

        ResponseVO<Boolean> responseVO = new ResponseVO();
        Boolean getAcceptStatus=false;
        try {

            String status = "50";

            log.info("Status :"+status +"  "+"submissionId :"+data.get("submissionId"));

            getAcceptStatus = reportSubRepo.acceptAndRejectReport(
                     status,
                    Integer.parseInt(data.get("submissionId")));

            log.info("Status of Accept & Reject :"+getAcceptStatus);


            /*Workflow entity=new Workflow();

            SimpleDateFormat dateFormat = new SimpleDateFormat("dd/MM/yyyy");
            Date date=new Date();
            dateFormat.format(date);

            log.info("Date of Last Action :"+dateFormat.parse(dateFormat.format(date)));

            entity.setSubmissionIdFK(Integer.parseInt(data.get("submissionId")));
            entity.setPendingWith(" ");
            entity.setLastAction(" ");
            entity.setStatus("Accepted");
            entity.setActionBy(loginUserData.get("pf_number"));
            entity.setRemarks(" ");
            entity.setLastActionDate(dateFormat.parse(dateFormat.format(date)));

             // Update WorkFlow Table
//            workflowRepository.save(entity);*/

            responseVO.setStatusCode(HttpStatus.OK.value());
            responseVO.setMessage("data updated successfully");
            responseVO.setResult(getAcceptStatus);

        } catch (Exception e) {
            log.info("exception Occurred while accepting report");
            responseVO.setStatusCode(HttpStatus.INTERNAL_SERVER_ERROR.value());
            responseVO.setMessage("Exception Occurred" + e.getMessage());
            responseVO.setResult(getAcceptStatus);
        }
        return new ResponseEntity<>(responseVO, HttpStatus.OK);
    }

    getting error as per below

    2024-10-28T17:15:33.905+05:30  WARN 22488 --- [roWorklistService] [nio-8083-exec-1] o.h.engine.jdbc.spi.SqlExceptionHelper   : SQL Error: 1002, SQLState: 24000
2024-10-28T17:15:33.905+05:30 ERROR 22488 --- [roWorklistService] [nio-8083-exec-1] o.h.engine.jdbc.spi.SqlExceptionHelper   : ORA-01002: fetch out of sequence

2024-10-28T17:15:33.919+05:30  INFO 22488 --- [roWorklistService] [nio-8083-exec-1] c.c.r.services.roWorklistServiceImpl     : exception Occurred while accepting report
2024-10-28T17:17:34.025+05:30  INFO 22488 --- [roWorklistService] [   File Watcher] rtingClassPathChangeChangedEventListener : Restarting due to 1 class path change (0 additions, 1 deletion, 0 modifications)
2024-10-28T17:17:34.046+05:30  INFO 22488 --- [roWorklistService] [       Thread-7] j.LocalContainerEntityManagerFactoryBean : Closing JPA EntityManagerFactory for persistence unit 'default'
2024-10-28T17:17:34.053+05:30  INFO 22488 --- [roWorklistService] [       Thread-7] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2024-10-28T17:17:34.111+05:30  INFO 22488 --- [roWorklistService] [       Thread-7] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
  .   ____          _            __ _ _
