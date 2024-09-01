2024-09-02T01:33:59.514+05:30 DEBUG 7228 --- [commonReportsService] [nio-8081-exec-1] org.hibernate.SQL                        : 
    select
        co1_0.crs_oth_assests_id,
        co1_0.oth_asts_addition,
        co1_0.oth_asts_branch,
        co1_0.oth_asts_date,
        co1_0.crs_oth_assests_sq,
        co1_0.crs_oth_assests_name,
        co1_0.oth_asts_cur_yr,
        co1_0.oth_asts_lst_yr,
        co1_0.oth_asts_provi_req,
        co1_0.oth_asts_provi_rate,
        co1_0.oth_asts_reduction,
        co1_0.report_master_list_id_fk,
        co1_0.oth_asts_write_off 
    from
        crs_oth_assests co1_0 
    where
        co1_0.oth_asts_date=? 
        and co1_0.oth_asts_branch=? 
        and co1_0.crs_oth_assests_id=?
Hibernate: 
    select
        co1_0.crs_oth_assests_id,
        co1_0.oth_asts_addition,
        co1_0.oth_asts_branch,
        co1_0.oth_asts_date,
        co1_0.crs_oth_assests_sq,
        co1_0.crs_oth_assests_name,
        co1_0.oth_asts_cur_yr,
        co1_0.oth_asts_lst_yr,
        co1_0.oth_asts_provi_req,
        co1_0.oth_asts_provi_rate,
        co1_0.oth_asts_reduction,
        co1_0.report_master_list_id_fk,
        co1_0.oth_asts_write_off 
    from
        crs_oth_assests co1_0 
    where
        co1_0.oth_asts_date=? 
        and co1_0.oth_asts_branch=? 
        and co1_0.crs_oth_assests_id=?
2024-09-02T01:33:59.574+05:30 DEBUG 7228 --- [commonReportsService] [nio-8081-exec-1] org.hibernate.SQL                        : 
    update
        crs_oth_assests 
    set
        oth_asts_addition=?,
        oth_asts_branch=?,
        oth_asts_date=?,
        crs_oth_assests_sq=?,
        crs_oth_assests_name=?,
        oth_asts_cur_yr=?,
        oth_asts_lst_yr=?,
        oth_asts_provi_req=?,
        oth_asts_provi_rate=?,
        oth_asts_reduction=?,
        report_master_list_id_fk=?,
        oth_asts_write_off=? 
    where
        crs_oth_assests_id=?
Hibernate: 
    update
        crs_oth_assests 
    set
        oth_asts_addition=?,
        oth_asts_branch=?,
        oth_asts_date=?,
        crs_oth_assests_sq=?,
        crs_oth_assests_name=?,
        oth_asts_cur_yr=?,
        oth_asts_lst_yr=?,
        oth_asts_provi_req=?,
        oth_asts_provi_rate=?,
        oth_asts_reduction=?,
        report_master_list_id_fk=?,
        oth_asts_write_off=? 
    where
        crs_oth_assests_id=?
2024-09-02T01:33:59.586+05:30  WARN 7228 --- [commonReportsService] [nio-8081-exec-1] o.h.engine.jdbc.spi.SqlExceptionHelper   : SQL Error: 1, SQLState: 23000
2024-09-02T01:33:59.586+05:30 ERROR 7228 --- [commonReportsService] [nio-8081-exec-1] o.h.engine.jdbc.spi.SqlExceptionHelper   : ORA-00001: unique constraint (FNSONLI.CRS_OTH_ASSESTS_PK) violated

2024-09-02T01:33:59.593+05:30  INFO 7228 --- [commonReportsService] [nio-8081-exec-1] c.c.c.services.RW04ServiceImpl           : Unique constraint violation while updating ID: 2
