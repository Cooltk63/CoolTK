SELECT \n" +
            "TAB_ADD_ROW_FLAG ," +
            "TAB_FOOTER_FLAG ," +
            "TAB_FOOTER_VALUE ," +
            "TAB_NAME ," +
            "TAB_VALUE_FK AS TAB_VALUE  "+
            "FROM COMMON_TAB_PARAM WHERE REPORT_ID_FK =:reportId


            for avoce query if any column data is null i want to sent or get the query result as 0 or empty string
