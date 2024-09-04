@Query(value = "select ax.LEASE_PROPERTY," +
            "ax.LEASE_CITY,LEASE_OWNER," +
            "nvl(to_char(ax.LEASE_RENT_START_DATE,'yyyy-mm-dd'),0) as LEASE_RENT_START_DATE," +
            "ax.LEASE_TOTAL_PERIOD_OF_RENT," +
            "ax.LEASE_MONTHLY_RENT , " +
            "ax.LEASE_RENT_BEFORE_TDS," +
            "ax.LEASE_PERIOD_OF_RENT_PAID," +
            "ax.LEASE_SECURITY_DEPOSIT," +
            "CASE WHEN ax.LEASE_ISDEPOSIT_ADJUSTABLE = 'YES' THEN 'Y' WHEN ax.LEASE_ISDEPOSIT_ADJUSTABLE = 'NO' THEN 'N' ELSE ax.LEASE_ISDEPOSIT_ADJUSTABLE END as LEASE_ISDEPOSIT_ADJUSTABLE," +
            "CASE WHEN ax.LEASE_ISESCALATION_CLAUSE = 'YES' THEN 'Y' WHEN ax.LEASE_ISESCALATION_CLAUSE = 'NO' THEN 'N' ELSE ax.LEASE_ISESCALATION_CLAUSE END as LEASE_ISESCALATION_CLAUSE," +
            "nvl(to_char(ax.LEASE_1ST_INCREASE,'yyyy-mm-dd'),0) as LEASE_1ST_INCREASE," +
            "ax.LEASE_1ST_RENT_INCREASE ," +
            "nvl(to_char(ax.LEASE_2ND_INCREASE,'yyyy-mm-dd'),0) as LEASE_2ND_INCREASE," +
            "ax.LEASE_2ND_RENT_INCREASE," +
            "nvl(to_char(ax.LEASE_3RD_INCREASE,'yyyy-mm-dd'),0) as LEASE_3RD_INCREASE," +
            "ax.LEASE_3RD_RENT_INCREASE," +
            "CASE WHEN ax.LEASE_RENEWAL_OPTION = 'YES' THEN 'Y' WHEN ax.LEASE_RENEWAL_OPTION = 'NO' THEN 'N' ELSE ax.LEASE_RENEWAL_OPTION END as LEASE_RENEWAL_OPTION," +
            "ax.LEASE_ESCALTED_NEWRENATL," +
            "ax.LEASE_RENEWAL_PERIOD," +
            "CASE WHEN ax.LEASE_CANCELLED_BY_BOTH = 'YES' THEN 'Y' WHEN ax.LEASE_CANCELLED_BY_BOTH = 'NO' THEN 'N' ELSE ax.LEASE_CANCELLED_BY_BOTH END as LEASE_CANCELLED_BY_BOTH," +
            "CASE WHEN ax.LEASE_CANCELLED_BY_LESSEE = 'YES' THEN 'Y' WHEN ax.LEASE_CANCELLED_BY_LESSEE = 'NO' THEN 'N' ELSE ax.LEASE_CANCELLED_BY_LESSEE END as LEASE_CANCELLED_BY_LESSEE," +
            "ax.LEASE_REMARKS , " +
            "ax.LEASE_ID as ROWNUMDATA, " +
            "ax.LEASE_ID,'false' " +
            "from CRS_LEASE ax " +
            "where ax.REPORT_MASTER_LIST_ID_FK =:submissionId and ax.LEASE_DATE =:quarterEndDate and ax.LEASE_BRANCH =:branch_code " +
            "order by ax.LEASE_ID", 
            nativeQuery = true)