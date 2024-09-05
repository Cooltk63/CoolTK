public String getQuarterYear() {
        String quarterFinancialQuery = " SELECT ( " + "   CASE " + "     WHEN TO_CHAR(sysdate, 'MM') IN(1,2,3) "
                + "     THEN 'Q3' " + "       ||'~' " + "       ||to_number(TO_CHAR(sysdate,'YYYY')-1) "
                + "       ||'-' " + "       ||to_number(TO_CHAR(sysdate,'YYYY')) " + "       ||'~' "
                + "       ||TO_CHAR(to_date('31/12/' "
                + "       ||(TO_CHAR(sysdate,'YYYY') -1),'dd/mm/yyyy'),'dd/mm/yyyy') " + "       ||'~' "
                + "       ||TO_CHAR(to_date('31/12/' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY') -2),'dd/mm/yyyy'),'dd/mm/yyyy') " + "       ||'~' "
                + "       ||TO_CHAR(to_date('30/09/' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY')-1),'dd/mm/yyyy'),'dd/mm/yyyy') "
                + "     WHEN TO_CHAR(sysdate, 'MM') IN(4,5,6) " + "     THEN 'Q4' " + "       ||'~' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY')-1) " + "       ||'-' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY')) " + "       ||'~' "
                + "       ||TO_CHAR(to_date('31/03/' "
                + "       ||(TO_CHAR(sysdate,'YYYY')),'dd/mm/yyyy'),'dd/mm/yyyy') " + "       ||'~' "
                + "       ||TO_CHAR(to_date('31/03/' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY') -1),'dd/mm/yyyy'),'dd/mm/yyyy') " + "       ||'~' "
                + "       ||TO_CHAR(to_date('31/12/' "
                + "       ||(TO_CHAR(sysdate,'YYYY') -1),'dd/mm/yyyy'),'dd/mm/yyyy') "
                + "     WHEN TO_CHAR(sysdate, 'MM') IN(7,8,9) " + "     THEN 'Q1' " + "       ||'~' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY')) " + "       ||'-' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY')+1) " + "       ||'~' "
                + "       ||TO_CHAR(to_date('30/06/' "
                + "       ||(TO_CHAR(sysdate,'YYYY')),'dd/mm/yyyy'),'dd/mm/yyyy') " + "       ||'~' "
                + "       ||TO_CHAR(to_date('30/06/' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY')-1),'dd/mm/yyyy'),'dd/mm/yyyy') " + "       ||'~' "
                + "       ||TO_CHAR(to_date('31/03/' "
                + "       ||(TO_CHAR(sysdate,'YYYY')),'dd/mm/yyyy'),'dd/mm/yyyy') "
                + "     WHEN TO_CHAR(sysdate, 'MM') IN(10,11,12) " + "     THEN 'Q2' " + "       ||'~' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY')) " + "       ||'-' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY')+1) " + "       ||'~' "
                + "       ||TO_CHAR(to_date('30/09/' "
                + "       ||(TO_CHAR(sysdate,'YYYY')),'dd/mm/yyyy'),'dd/mm/yyyy') " + "       ||'~' "
                + "       ||TO_CHAR(to_date('30/09/' "
                + "       ||to_number(TO_CHAR(sysdate,'YYYY')-1),'dd/mm/yyyy'),'dd/mm/yyyy') " + "       ||'~' "
                + "       ||TO_CHAR(to_date('30/06/' "
                + "       ||(TO_CHAR(sysdate,'YYYY')),'dd/mm/yyyy'),'dd/mm/yyyy') " + "   END )AS QuarterFinancialYear "
                + " FROM dual ";

        String QuarterFinancialYear = jdbcTemplate.queryForObject(quarterFinancialQuery, new RowMapper<String>() {

            @Override
            public String mapRow(ResultSet rs, int rowNum) throws SQLException {
                // TODO Auto-generated method stub
                String QuarterFinancialYear = rs.getString("QuarterFinancialYear");
                log.info("QuarterFinancialYear " + QuarterFinancialYear);
                return QuarterFinancialYear;
            }

        });
        log.info("date:" + QuarterFinancialYear);
        /*The return should be in "Quarter~FinancialYear~CurrentQuarterDate~PreviousYearDate~PreviousQuarterDate"*/
        return QuarterFinancialYear;
        //return "Q4~2023-2024~31/03/2024~31/03/2023~31/12/2023";
    }
