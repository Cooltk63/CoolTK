SELECT STND_ASTS_NAME_OF_BORROWER, STND_ASTS_INFRA_NON_INFRA,\n" +
            " \n" +
            "        CASE WHEN STND_ASTS_INFRA_NON_INFRA = 'INFRA'\n" +
            "        THEN \n" +
            "        STND_ASTS_INFRA_WITHIN2YRS ELSE STND_ASTS_NONINFRA_WITHIN1YR \n" +
            "        END AS \n" +
            "        STND_ASTS_WITHIN_1_OR_2_YRS, \n" +
            "        CASE WHEN STND_ASTS_INFRA_NON_INFRA = 'INFRA'\n" +
            "        THEN \n" +
            "        STND_ASTS_INFRA_ACCTS2YRS ELSE STND_ASTS_NONINFRA_ACCTS1YR \n" +
            "        END AS \n" +
            "        STND_ASTS_ACCTS_1_OR_2_YRS, \n" +
            "        STND_ASSETS_SEQ AS ROWSEQ, STND_ASSETS_SEQ,'false' \n" +
            "        FROM CRS_STND_ASSETS \n" +
            "        WHERE REPORT_MASTER_LIST_ID_FK =:submissionId  \n" +
            "        ORDER BY STND_ASSETS_SEQ

            if any columns value is null then show either empty string or 0 there but not null values
