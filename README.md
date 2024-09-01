2024-09-02T01:11:09.357+05:30  WARN 5160 --- [commonReportsService] [nio-8081-exec-4] o.h.engine.jdbc.spi.SqlExceptionHelper   : SQL Error: 1, SQLState: 23000
2024-09-02T01:11:09.357+05:30 ERROR 5160 --- [commonReportsService] [nio-8081-exec-4] o.h.engine.jdbc.spi.SqlExceptionHelper   : ORA-00001: unique constraint (FNSONLI.CRS_OTH_ASSESTS_PK) violated

2024-09-02T01:11:09.365+05:30  INFO 5160 --- [commonReportsService] [nio-8081-exec-4] c.c.c.services.RW04ServiceImpl           : Exception occurred: could not execute statement [ORA-00001: unique constraint (FNSONLI.CRS_OTH_ASSESTS_PK) violated
] [update crs_oth_assests set oth_asts_addition=?,oth_asts_branch=?,oth_asts_date=?,crs_oth_assests_sq=?,crs_oth_assests_name=?,oth_asts_cur_yr=?,oth_asts_lst_yr=?,oth_asts_provi_req=?,oth_asts_provi_rate=?,oth_asts_reduction=?,report_master_list_id_fk=?,oth_asts_write_off=? where crs_oth_assests_id=?]; SQL [update crs_oth_assests set oth_asts_addition=?,oth_asts_branch=?,oth_asts_date=?,crs_oth_assests_sq=?,crs_oth_assests_name=?,oth_asts_cur_yr=?,oth_asts_lst_yr=?,oth_asts_provi_req=?,oth_asts_provi_rate=?,oth_asts_reduction=?,report_master_list_id_fk=?,oth_asts_write_off=? where crs_oth_assests_id=?]; constraint [FNSONLI.CRS_OTH_ASSESTS_PK]

this is the error i am getting after try to insert the record in db

and this is my table sql


  CREATE TABLE "FNSONLI"."CRS_OTH_ASSESTS" 
   (	"OTH_ASTS_BRANCH" VARCHAR2(5 BYTE) NOT NULL ENABLE, 
	"OTH_ASTS_DATE" DATE NOT NULL ENABLE, 
	"OTH_ASTS_LST_YR" VARCHAR2(20 BYTE), 
	"OTH_ASTS_WRITE_OFF" VARCHAR2(20 BYTE), 
	"OTH_ASTS_ADDITION" VARCHAR2(20 BYTE), 
	"OTH_ASTS_REDUCTION" VARCHAR2(20 BYTE), 
	"OTH_ASTS_CUR_YR" VARCHAR2(20 BYTE), 
	"OTH_ASTS_PROVI_RATE" VARCHAR2(20 BYTE), 
	"OTH_ASTS_PROVI_REQ" VARCHAR2(20 BYTE), 
	"REPORT_MASTER_LIST_ID_FK" VARCHAR2(10 BYTE) NOT NULL ENABLE, 
	"CRS_OTH_ASSESTS_NAME" VARCHAR2(200 BYTE), 
	"CRS_OTH_ASSESTS_ID" VARCHAR2(20 BYTE) NOT NULL ENABLE, 
	"CRS_OTH_ASSESTS_SQ" VARCHAR2(20 BYTE), 
	 CONSTRAINT "CRS_OTH_ASSESTS_PK" PRIMARY KEY ("OTH_ASTS_BRANCH", "OTH_ASTS_DATE", "CRS_OTH_ASSESTS_ID")
  USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
  BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "TSDATA"  ENABLE
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 
 NOCOMPRESS LOGGING
  STORAGE(INITIAL 262144 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
  BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "TSDATA" ;

  CREATE INDEX "FNSONLI"."CRS_OTH_ASSESTS_INDX" ON "FNSONLI"."CRS_OTH_ASSESTS" ("REPORT_MASTER_LIST_ID_FK") 
  PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 131072 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
  BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "TSDATA" ;

