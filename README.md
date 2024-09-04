@Query(value = "select ax.LEASE_PROPERTY," +
            "ax.LEASE_CITY,LEASE_OWNER," +
            "nvl(to_char(ax.LEASE_RENT_START_DATE,'yyyy-mm-dd'),0) as LEASE_RENT_START_DATE," +
            "ax.LEASE_TOTAL_PERIOD_OF_RENT," +
            "ax.LEASE_MONTHLY_RENT , " +
            "ax.LEASE_RENT_BEFORE_TDS," +
            "ax.LEASE_PERIOD_OF_RENT_PAID," +
            "ax.LEASE_SECURITY_DEPOSIT,\n" +
            "ax.LEASE_ISDEPOSIT_ADJUSTABLE," +
            "ax.LEASE_ISESCALATION_CLAUSE," +
            "nvl(to_char(ax.LEASE_1ST_INCREASE,'yyyy-mm-dd'),0) as LEASE_1ST_INCREASE," +
            "ax.LEASE_1ST_RENT_INCREASE ,\n" +
            "nvl(to_char(ax.LEASE_2ND_INCREASE,'yyyy-mm-dd'),0) as LEASE_2ND_INCREASE," +
            "ax.LEASE_2ND_RENT_INCREASE," +
            "nvl(to_char(ax.LEASE_3RD_INCREASE,'yyyy-mm-dd'),0) as LEASE_3RD_INCREASE,\n" +
            "ax.LEASE_3RD_RENT_INCREASE," +
            "ax.LEASE_RENEWAL_OPTION," +
            "ax.LEASE_ESCALTED_NEWRENATL," +
            "ax.LEASE_RENEWAL_PERIOD," +
            "ax.LEASE_CANCELLED_BY_BOTH,\n" +
            "ax.LEASE_CANCELLED_BY_LESSEE," +
            "ax.LEASE_REMARKS , " +
            "ax.LEASE_ID as ROWNUMDATA, " +
            "ax.LEASE_ID,'false' " +
            "from CRS_LEASE ax \n" +
            "where ax.REPORT_MASTER_LIST_ID_FK =:submissionId and ax.LEASE_DATE =:quarterEndDate and ax.LEASE_BRANCH =:branch_code order by ax.LEASE_ID", nativeQuery = true)


            In above query i wanted to add the case for 
            LEASE_CANCELLED_BY_LESSEE,
            LEASE_ISDEPOSIT_ADJUSTABLE
LEASE_ISESCALATION_CLAUSE,
LEASE_CANCELLED_BY_BOTH,
LEASE_RENEWAL_OPTION this columns if the data inside this column is YES then sent as Y if result/data inside this column is No sent N
