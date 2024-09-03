This is my Modal/ Entity 
package com.crs.commonReportsService.models;


import jakarta.persistence.*;
import lombok.Getter;
import lombok.Setter;

import java.util.Date;


@Getter
@Setter
@Entity
@Table(name = "CRS_LEASE")
public class CrsLease {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY, generator = "CRS_LEASE_SEQ")
    @SequenceGenerator(name = "CRS_LEASE_SEQ", sequenceName = "CRS_LEASE_SEQ", allocationSize = 1)
    @Column(name = "LEASE_ID")
    private Integer leaseId;

    @Column(name = "LEASE_PROPERTY")
    private String leaseProperty; //0

    @Column(name = "LEASE_CITY")
    private String leaseCity; //1

    @Column(name = "LEASE_OWNER")
    private String leaseOwner;  //2

    @Column(name = "LEASE_RENT_START_DATE")
    private Date leaseRentStartDate;  //3

    @Column(name = "LEASE_TOTAL_PERIOD_OF_RENT")
    private Integer leaseTotalPeriodOfRent; //4

    @Column(name = "LEASE_MONTHLY_RENT")
    private Double leaseMonthlyRent; //5

    @Column(name = "LEASE_RENT_BEFORE_TDS")
    private Double leaseRentBeforeTds; //6

    @Column(name = "LEASE_PERIOD_OF_RENT_PAID")
    private String leasePeriodOfRentPaid; //7

    @Column(name = "LEASE_SECURITY_DEPOSIT")
    private Double leaseSecurityDeposit; //8

    @Column(name = "LEASE_ISDEPOSIT_ADJUSTABLE")
    private String leaseIsDepositAdjustable; //9

    @Column(name = "LEASE_ISESCALATION_CLAUSE")
    private String leaseIsEscalationClause; //10

    @Column(name = "LEASE_1ST_INCREASE")
    private Date lease1stIncrease; //11

    @Column(name = "LEASE_1ST_RENT_INCREASE")
    private Integer lease1stRentIncrease; //12

    @Column(name = "LEASE_2ND_INCREASE")
    private Date lease2ndIncrease; // 13

    @Column(name = "LEASE_2ND_RENT_INCREASE")
    private Integer lease2ndRentIncrease; //14

    @Column(name = "LEASE_3RD_INCREASE")
    private Date lease3rdIncrease; //15

    @Column(name = "LEASE_3RD_RENT_INCREASE")
    private Integer lease3rdRentIncrease; //16

    @Column(name = "LEASE_RENEWAL_OPTION")
    private String leaseRenewalOption;  //17

    @Column(name = "LEASE_ESCALTED_NEWRENATL")
    private Integer leaseEscalatedNewRental; //18

    /////////////////////issue/////////////////////////
    @Column(name = "LEASE_RENEWAL_PERIOD")
    private Double leaseRenewalPeriod; //19
    ///////////////////////////////////////////////////////////////////////////////////////////////////

    @Column(name = "LEASE_CANCELLED_BY_BOTH")
    private String leaseCancelledByBoth; //20

    @Column(name = "LEASE_CANCELLED_BY_LESSEE")
    private String leaseCancelledByLessee; //21

    @Column(name = "LEASE_REMARKS")
    private String leaseRemarks; //22

    @Column(name = "REPORT_MASTER_LIST_ID_FK")
    private String reportMasterListIdFk;

    @Column(name = "LEASE_DATE")
    private Date leasedate;

    @Column(name = "LEASE_BRANCH")
    private String leasebranch;

}

// This is my delete method 

 @Transactional
    @Override
    public ResponseEntity deleteById(Map<String,Object> map){

        //For getting additional Details other than User Details
        Map<String, String> data = (Map<String, String>) map.get("data");
        ResponseVO<Integer> responseVO = new ResponseVO<>();

        int isDeleted = 0;

        try {
            int deleteId = Integer.parseInt(data.get("uniqueId"));

            // Check before ID is Existed or Not
            int exits = crsLeaseRepository.countByleaseId(deleteId);
            log.info("Is ID Exits :" + exits);

            if (exits > 0) {
                //If ID exists deleting Data
                isDeleted = crsLeaseRepository.deleteByleaseId(deleteId);
                log.info("Result for isDeleted :" + isDeleted);
            }


            // Setting Up Success & Response Data
            responseVO.setStatusCode(HttpStatus.OK.value());
            responseVO.setMessage("Data Deleted successfully");
            responseVO.setResult(isDeleted);

        } catch (Exception e){
            e.printStackTrace();
            log.info("exception Occurred");
            responseVO.setStatusCode(HttpStatus.INTERNAL_SERVER_ERROR.value());
            responseVO.setMessage("Exception Occurred" + e.getMessage());
        }
        return new ResponseEntity<>(responseVO, HttpStatus.OK);
    }


This is the error we get

2024-09-03T19:29:01.264+05:30 DEBUG 22044 --- [commonReportsService] [nio-8081-exec-1] org.hibernate.SQL                        : 
    select
        count(cl1_0.lease_id) 
    from
        crs_lease cl1_0 
    where
        cl1_0.lease_id=?
Hibernate: 
    select
        count(cl1_0.lease_id) 
    from
        crs_lease cl1_0 
    where
        cl1_0.lease_id=?
2024-09-03T19:29:01.298+05:30  INFO 22044 --- [commonReportsService] [nio-8081-exec-1] c.c.c.services.RW46ServiceImpl           : Is ID Exits :1
2024-09-03T19:29:01.307+05:30 DEBUG 22044 --- [commonReportsService] [nio-8081-exec-1] org.hibernate.SQL                        : 
    select
        cl1_0.lease_id,
        cl1_0.lease_1st_increase,
        cl1_0.lease_1st_rent_increase,
        cl1_0.lease_2nd_increase,
        cl1_0.lease_2nd_rent_increase,
        cl1_0.lease_3rd_increase,
        cl1_0.lease_3rd_rent_increase,
        cl1_0.lease_cancelled_by_both,
        cl1_0.lease_cancelled_by_lessee,
        cl1_0.lease_city,
        cl1_0.lease_escalted_newrenatl,
        cl1_0.lease_isdeposit_adjustable,
        cl1_0.lease_isescalation_clause,
        cl1_0.lease_monthly_rent,
        cl1_0.lease_owner,
        cl1_0.lease_period_of_rent_paid,
        cl1_0.lease_property,
        cl1_0.lease_remarks,
        cl1_0.lease_renewal_option,
        cl1_0.lease_renewal_period,
        cl1_0.lease_rent_before_tds,
        cl1_0.lease_rent_start_date,
        cl1_0.lease_security_deposit,
        cl1_0.lease_total_period_of_rent,
        cl1_0.lease_branch,
        cl1_0.lease_date,
        cl1_0.report_master_list_id_fk 
    from
        crs_lease cl1_0 
    where
        cl1_0.lease_id=?
Hibernate: 
    select
        cl1_0.lease_id,
        cl1_0.lease_1st_increase,
        cl1_0.lease_1st_rent_increase,
        cl1_0.lease_2nd_increase,
        cl1_0.lease_2nd_rent_increase,
        cl1_0.lease_3rd_increase,
        cl1_0.lease_3rd_rent_increase,
        cl1_0.lease_cancelled_by_both,
        cl1_0.lease_cancelled_by_lessee,
        cl1_0.lease_city,
        cl1_0.lease_escalted_newrenatl,
        cl1_0.lease_isdeposit_adjustable,
        cl1_0.lease_isescalation_clause,
        cl1_0.lease_monthly_rent,
        cl1_0.lease_owner,
        cl1_0.lease_period_of_rent_paid,
        cl1_0.lease_property,
        cl1_0.lease_remarks,
        cl1_0.lease_renewal_option,
        cl1_0.lease_renewal_period,
        cl1_0.lease_rent_before_tds,
        cl1_0.lease_rent_start_date,
        cl1_0.lease_security_deposit,
        cl1_0.lease_total_period_of_rent,
        cl1_0.lease_branch,
        cl1_0.lease_date,
        cl1_0.report_master_list_id_fk 
    from
        crs_lease cl1_0 
    where
        cl1_0.lease_id=?
2024-09-03T19:29:01.312+05:30  WARN 22044 --- [commonReportsService] [nio-8081-exec-1] o.h.engine.jdbc.spi.SqlExceptionHelper   : SQL Error: 17026, SQLState: 99999
2024-09-03T19:29:01.313+05:30 ERROR 22044 --- [commonReportsService] [nio-8081-exec-1] o.h.engine.jdbc.spi.SqlExceptionHelper   : Numeric Overflow
2024-09-03T19:29:01.318+05:30  INFO 22044 --- [commonReportsService] [nio-8081-exec-1] c.c.c.services.RW46ServiceImpl           : exception Occurred
org.springframework.orm.jpa.JpaSystemException: Could not extract column [3] from JDBC ResultSet [Numeric Overflow] [n/a]
	at org.springframework.orm.jpa.vendor.HibernateJpaDialect.convertHibernateAccessException(HibernateJpaDialect.java:341)
	at org.springframework.orm.jpa.vendor.HibernateJpaDialect.translateExceptionIfPossible(HibernateJpaDialect.java:241)
	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.translateExceptionIfPossible(AbstractEntityManagerFactoryBean.java:550)
	at org.springframework.dao.support.ChainedPersistenceExceptionTranslator.translateExceptionIfPossible(ChainedPersistenceExceptionTranslator.java:61)
	at org.springframework.dao.support.DataAccessUtils.translateIfNecessary(DataAccessUtils.java:335)
	at org.springframework.dao.support.PersistenceExceptionTranslationInterceptor.invoke(PersistenceExceptionTranslationInterceptor.java:152)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.data.jpa.repository.support.CrudMethodMetadataPostProcessor$CrudMethodMetadataPopulatingMethodInterceptor.invoke(CrudMethodMetadataPostProcessor.java:136)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:97)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:223)
	at jdk.proxy4/jdk.proxy4.$Proxy157.deleteByleaseId(Unknown Source)
	at com.crs.commonReportsService.services.RW46ServiceImpl.deleteById(RW46ServiceImpl.java:90)
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
	at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:354)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:196)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:163)
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.proceed(CglibAopProxy.java:768)
	at org.springframework.transaction.interceptor.TransactionInterceptor$1.proceedWithInvocation(TransactionInterceptor.java:123)
	at org.springframework.transaction.interceptor.TransactionAspectSupport.invokeWithinTransaction(TransactionAspectSupport.java:392)
	at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:119)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.proceed(CglibAopProxy.java:768)
	at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:720)
	at com.crs.commonReportsService.services.RW46ServiceImpl$$SpringCGLIB$$0.deleteById(<generated>)
	at com.crs.commonReportsService.controllers.RW46Controller.deleteById(RW46Controller.java:36)
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
	at org.springframework.web.method.support.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:255)
	at org.springframework.web.method.support.InvocableHandlerMethod.invokeForRequest(InvocableHandlerMethod.java:188)
	at org.springframework.web.servlet.mvc.method.annotation.ServletInvocableHandlerMethod.invokeAndHandle(ServletInvocableHandlerMethod.java:118)
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.invokeHandlerMethod(RequestMappingHandlerAdapter.java:926)
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.handleInternal(RequestMappingHandlerAdapter.java:831)
	at org.springframework.web.servlet.mvc.method.AbstractHandlerMethodAdapter.handle(AbstractHandlerMethodAdapter.java:87)
	at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:1089)
	at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:979)
	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1014)
	at org.springframework.web.servlet.FrameworkServlet.doPost(FrameworkServlet.java:914)
	at jakarta.servlet.http.HttpServlet.service(HttpServlet.java:590)
	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:885)
	at jakarta.servlet.http.HttpServlet.service(HttpServlet.java:658)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:195)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140)
	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:51)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140)
	at org.springframework.web.filter.RequestContextFilter.doFilterInternal(RequestContextFilter.java:100)
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140)
	at org.springframework.web.filter.FormContentFilter.doFilterInternal(FormContentFilter.java:93)
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140)
	at org.springframework.web.filter.ServerHttpObservationFilter.doFilterInternal(ServerHttpObservationFilter.java:109)
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140)
	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:201)
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116)
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164)
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140)
	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:167)
	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:90)
	at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:482)
	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:115)
	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:93)
	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:74)
	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:344)
	at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:389)
	at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:63)
	at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:896)
	at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1741)
	at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:52)
	at org.apache.tomcat.util.threads.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1190)
	at org.apache.tomcat.util.threads.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:659)
	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:63)
	at java.base/java.lang.Thread.run(Thread.java:1570)
Caused by: org.hibernate.exception.GenericJDBCException: Could not extract column [3] from JDBC ResultSet [Numeric Overflow] [n/a]
	at org.hibernate.exception.internal.StandardSQLExceptionConverter.convert(StandardSQLExceptionConverter.java:63)
	at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:108)
	at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:94)
	at org.hibernate.sql.results.jdbc.internal.JdbcValuesResultSetImpl.getCurrentRowValue(JdbcValuesResultSetImpl.java:387)
	at org.hibernate.sql.results.internal.RowProcessingStateStandardImpl.getJdbcValue(RowProcessingStateStandardImpl.java:120)
	at org.hibernate.sql.results.graph.basic.BasicResultAssembler.extractRawValue(BasicResultAssembler.java:52)
	at org.hibernate.sql.results.graph.basic.BasicResultAssembler.assemble(BasicResultAssembler.java:59)
	at org.hibernate.sql.results.graph.DomainResultAssembler.assemble(DomainResultAssembler.java:35)
	at org.hibernate.sql.results.graph.entity.AbstractEntityInitializer.extractConcreteTypeStateValues(AbstractEntityInitializer.java:1037)
	at org.hibernate.sql.results.graph.entity.AbstractEntityInitializer.initializeEntityInstance(AbstractEntityInitializer.java:794)
	at org.hibernate.sql.results.graph.entity.AbstractEntityInitializer.initializeEntity(AbstractEntityInitializer.java:769)
	at org.hibernate.sql.results.graph.entity.AbstractEntityInitializer.initializeInstance(AbstractEntityInitializer.java:761)
	at org.hibernate.sql.results.internal.InitializersList.initializeInstance(InitializersList.java:73)
	at org.hibernate.sql.results.internal.StandardRowReader.coordinateInitializers(StandardRowReader.java:113)
	at org.hibernate.sql.results.internal.StandardRowReader.readRow(StandardRowReader.java:87)
	at org.hibernate.sql.results.spi.ListResultsConsumer.consume(ListResultsConsumer.java:205)
	at org.hibernate.sql.results.spi.ListResultsConsumer.consume(ListResultsConsumer.java:33)
	at org.hibernate.sql.exec.internal.JdbcSelectExecutorStandardImpl.doExecuteQuery(JdbcSelectExecutorStandardImpl.java:211)
	at org.hibernate.sql.exec.internal.JdbcSelectExecutorStandardImpl.executeQuery(JdbcSelectExecutorStandardImpl.java:83)
	at org.hibernate.sql.exec.spi.JdbcSelectExecutor.list(JdbcSelectExecutor.java:76)
	at org.hibernate.sql.exec.spi.JdbcSelectExecutor.list(JdbcSelectExecutor.java:65)
	at org.hibernate.query.sqm.internal.ConcreteSqmSelectQueryPlan.lambda$new$2(ConcreteSqmSelectQueryPlan.java:139)
	at org.hibernate.query.sqm.internal.ConcreteSqmSelectQueryPlan.withCacheableSqmInterpretation(ConcreteSqmSelectQueryPlan.java:382)
	at org.hibernate.query.sqm.internal.ConcreteSqmSelectQueryPlan.performList(ConcreteSqmSelectQueryPlan.java:302)
	at org.hibernate.query.sqm.internal.QuerySqmImpl.doList(QuerySqmImpl.java:526)
	at org.hibernate.query.spi.AbstractSelectionQuery.list(AbstractSelectionQuery.java:423)
	at org.hibernate.query.Query.getResultList(Query.java:120)
	at org.springframework.data.jpa.repository.query.JpaQueryExecution$DeleteExecution.doExecute(JpaQueryExecution.java:295)
	at org.springframework.data.jpa.repository.query.JpaQueryExecution.execute(JpaQueryExecution.java:92)
	at org.springframework.data.jpa.repository.query.AbstractJpaQuery.doExecute(AbstractJpaQuery.java:152)
	at org.springframework.data.jpa.repository.query.AbstractJpaQuery.execute(AbstractJpaQuery.java:140)
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker.doInvoke(RepositoryMethodInvoker.java:170)
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker.invoke(RepositoryMethodInvoker.java:158)
	at org.springframework.data.repository.core.support.QueryExecutorMethodInterceptor.doInvoke(QueryExecutorMethodInterceptor.java:164)
	at org.springframework.data.repository.core.support.QueryExecutorMethodInterceptor.invoke(QueryExecutorMethodInterceptor.java:143)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.data.projection.DefaultMethodInvokingMethodInterceptor.invoke(DefaultMethodInvokingMethodInterceptor.java:70)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.transaction.interceptor.TransactionInterceptor$1.proceedWithInvocation(TransactionInterceptor.java:123)
	at org.springframework.transaction.interceptor.TransactionAspectSupport.invokeWithinTransaction(TransactionAspectSupport.java:392)
	at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:119)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.dao.support.PersistenceExceptionTranslationInterceptor.invoke(PersistenceExceptionTranslationInterceptor.java:137)
	... 74 more
Caused by: java.sql.SQLException: Numeric Overflow
	at oracle.jdbc.driver.NumberCommonAccessor.throwOverflow(NumberCommonAccessor.java:4161)
	at oracle.jdbc.driver.NumberCommonAccessor.getInt(NumberCommonAccessor.java:111)
	at oracle.jdbc.driver.GeneratedStatement.getInt(GeneratedStatement.java:171)
	at oracle.jdbc.driver.GeneratedScrollableResultSet.getInt(GeneratedScrollableResultSet.java:269)
	at com.zaxxer.hikari.pool.HikariProxyResultSet.getInt(HikariProxyResultSet.java)
	at org.hibernate.type.descriptor.jdbc.IntegerJdbcType$2.doExtract(IntegerJdbcType.java:87)
	at org.hibernate.type.descriptor.jdbc.BasicExtractor.extract(BasicExtractor.java:44)
	at org.hibernate.sql.results.jdbc.internal.JdbcValuesResultSetImpl.getCurrentRowValue(JdbcValuesResultSetImpl.java:379)
	... 113 more
2024-09-03T19:29:01.326+05:30 ERROR 22044 --- [commonReportsService] [nio-8081-exec-1] o.a.c.c.C.[.[.[/].[dispatcherServlet]    : Servlet.service() for servlet [dispatcherServlet] in context with path [] threw exception [Request processing failed: org.springframework.transaction.UnexpectedRollbackException: Transaction silently rolled back because it has been marked as rollback-only] with root cause

org.springframework.transaction.UnexpectedRollbackException: Transaction silently rolled back because it has been marked as rollback-only
	at org.springframework.transaction.support.AbstractPlatformTransactionManager.processCommit(AbstractPlatformTransactionManager.java:804) ~[spring-tx-6.1.8.jar:6.1.8]
	at org.springframework.transaction.support.AbstractPlatformTransactionManager.commit(AbstractPlatformTransactionManager.java:758) ~[spring-tx-6.1.8.jar:6.1.8]
	at org.springframework.transaction.interceptor.TransactionAspectSupport.commitTransactionAfterReturning(TransactionAspectSupport.java:676) ~[spring-tx-6.1.8.jar:6.1.8]
	at org.springframework.transaction.interceptor.TransactionAspectSupport.invokeWithinTransaction(TransactionAspectSupport.java:426) ~[spring-tx-6.1.8.jar:6.1.8]
	at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:119) ~[spring-tx-6.1.8.jar:6.1.8]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.proceed(CglibAopProxy.java:768) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:720) ~[spring-aop-6.1.8.jar:6.1.8]
	at com.crs.commonReportsService.services.RW46ServiceImpl$$SpringCGLIB$$0.deleteById(<generated>) ~[classes/:na]
	at com.crs.commonReportsService.controllers.RW46Controller.deleteById(RW46Controller.java:36) ~[classes/:na]
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
	at org.springframework.web.method.support.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:255) ~[spring-web-6.1.8.jar:6.1.8]
	at org.springframework.web.method.support.InvocableHandlerMethod.invokeForRequest(InvocableHandlerMethod.java:188) ~[spring-web-6.1.8.jar:6.1.8]
	at org.springframework.web.servlet.mvc.method.annotation.ServletInvocableHandlerMethod.invokeAndHandle(ServletInvocableHandlerMethod.java:118) ~[spring-webmvc-6.1.8.jar:6.1.8]
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.invokeHandlerMethod(RequestMappingHandlerAdapter.java:926) ~[spring-webmvc-6.1.8.jar:6.1.8]
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter.handleInternal(RequestMappingHandlerAdapter.java:831) ~[spring-webmvc-6.1.8.jar:6.1.8]
	at org.springframework.web.servlet.mvc.method.AbstractHandlerMethodAdapter.handle(AbstractHandlerMethodAdapter.java:87) ~[spring-webmvc-6.1.8.jar:6.1.8]
	at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:1089) ~[spring-webmvc-6.1.8.jar:6.1.8]
	at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:979) ~[spring-webmvc-6.1.8.jar:6.1.8]
	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1014) ~[spring-webmvc-6.1.8.jar:6.1.8]
	at org.springframework.web.servlet.FrameworkServlet.doPost(FrameworkServlet.java:914) ~[spring-webmvc-6.1.8.jar:6.1.8]
	at jakarta.servlet.http.HttpServlet.service(HttpServlet.java:590) ~[tomcat-embed-core-10.1.24.jar:6.0]
	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:885) ~[spring-webmvc-6.1.8.jar:6.1.8]
	at jakarta.servlet.http.HttpServlet.service(HttpServlet.java:658) ~[tomcat-embed-core-10.1.24.jar:6.0]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:195) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:51) ~[tomcat-embed-websocket-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.springframework.web.filter.RequestContextFilter.doFilterInternal(RequestContextFilter.java:100) ~[spring-web-6.1.8.jar:6.1.8]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar:6.1.8]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.springframework.web.filter.FormContentFilter.doFilterInternal(FormContentFilter.java:93) ~[spring-web-6.1.8.jar:6.1.8]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar:6.1.8]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.springframework.web.filter.ServerHttpObservationFilter.doFilterInternal(ServerHttpObservationFilter.java:109) ~[spring-web-6.1.8.jar:6.1.8]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar:6.1.8]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:201) ~[spring-web-6.1.8.jar:6.1.8]
	at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116) ~[spring-web-6.1.8.jar:6.1.8]
	at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:164) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:140) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:167) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:90) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:482) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:115) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:93) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:74) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:344) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:389) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:63) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:896) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1741) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:52) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.tomcat.util.threads.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1190) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.tomcat.util.threads.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:659) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:63) ~[tomcat-embed-core-10.1.24.jar:10.1.24]
	at java.base/java.lang.Thread.run(Thread.java:1570) ~[na:na]

