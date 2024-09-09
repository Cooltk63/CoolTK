2024-09-09T11:44:41.258+05:30  INFO 26252 --- [commonReportsService] [nio-8081-exec-2] c.c.c.r.RW46CustomRepositoryImpl         : QuarterFinancialYear Q1~2024-2025~30/06/2024~30/06/2023~31/03/2024
2024-09-09T11:44:41.261+05:30  INFO 26252 --- [commonReportsService] [nio-8081-exec-2] c.c.c.r.RW46CustomRepositoryImpl         : date:Q1~2024-2025~30/06/2024~30/06/2023~31/03/2024
2024-09-09T11:44:41.261+05:30  INFO 26252 --- [commonReportsService] [nio-8081-exec-2] c.c.c.services.RW05ServiceImpl           : getQuarterYear: Q1
2024-09-09T11:44:41.261+05:30  INFO 26252 --- [commonReportsService] [nio-8081-exec-2] c.c.c.services.RW05ServiceImpl           : getFinancialYear: 2024-2025
2024-09-09T11:44:41.261+05:30  INFO 26252 --- [commonReportsService] [nio-8081-exec-2] c.c.c.services.RW05ServiceImpl           : getCurrentQuarterEndDate: 30/06/2024
2024-09-09T11:44:41.261+05:30  INFO 26252 --- [commonReportsService] [nio-8081-exec-2] c.c.c.services.RW05ServiceImpl           : getPreviousYearDate: 30/06/2023
2024-09-09T11:44:41.261+05:30  INFO 26252 --- [commonReportsService] [nio-8081-exec-2] c.c.c.services.RW05ServiceImpl           : getPreviousQuarterDate: 31/03/2024
2024-09-09T11:44:41.261+05:30  INFO 26252 --- [commonReportsService] [nio-8081-exec-2] c.c.c.services.RW05ServiceImpl           : QED we Passing for RW-03 Report:31/03/2024
2024-09-09T11:44:41.322+05:30 DEBUG 26252 --- [commonReportsService] [nio-8081-exec-2] org.hibernate.SQL                        : 
    SELECT
        nvl(to_number(cont_liab_prov_lst_yr), 0) opening,
        nvl(to_number(cont_liab_prov_add), 0) additions,
        nvl(to_number(cont_liab_prov_used), 0) + nvl(to_number(cont_liab_prov_unused), 0) reversals 
    FROM
        crs_cont_liab_prov 
    WHERE
        cont_liab_prov_branch = ? 
        AND cont_liab_prov_date = to_date(?, 'dd/mm/yyyy') 
        AND cont_liab_prov_itemid = '18' 
Hibernate: 
    SELECT
        nvl(to_number(cont_liab_prov_lst_yr), 0) opening,
        nvl(to_number(cont_liab_prov_add), 0) additions,
        nvl(to_number(cont_liab_prov_used), 0) + nvl(to_number(cont_liab_prov_unused), 0) reversals 
    FROM
        crs_cont_liab_prov 
    WHERE
        cont_liab_prov_branch = ? 
        AND cont_liab_prov_date = to_date(?, 'dd/mm/yyyy') 
        AND cont_liab_prov_itemid = '18' 
2024-09-09T11:44:41.358+05:30  WARN 26252 --- [commonReportsService] [nio-8081-exec-2] o.h.engine.jdbc.spi.SqlExceptionHelper   : SQL Error: 1722, SQLState: 42000
2024-09-09T11:44:41.359+05:30 ERROR 26252 --- [commonReportsService] [nio-8081-exec-2] o.h.engine.jdbc.spi.SqlExceptionHelper   : ORA-01722: invalid number

2024-09-09T11:44:41.367+05:30 ERROR 26252 --- [commonReportsService] [nio-8081-exec-2] o.a.c.c.C.[.[.[/].[dispatcherServlet]    : Servlet.service() for servlet [dispatcherServlet] in context with path [] threw exception [Request processing failed: org.springframework.dao.InvalidDataAccessResourceUsageException: JDBC exception executing SQL [SELECT
nvl(to_number(cont_liab_prov_lst_yr), 0) opening,
nvl(to_number(cont_liab_prov_add), 0) additions,
nvl(to_number(cont_liab_prov_used), 0) +
nvl(to_number(cont_liab_prov_unused), 0) reversals
FROM
crs_cont_liab_prov
WHERE
cont_liab_prov_branch = ?
AND cont_liab_prov_date = to_date(?,'dd/mm/yyyy')
AND cont_liab_prov_itemid = '18' ] [ORA-01722: invalid number
] [n/a]; SQL [n/a]] with root cause

oracle.jdbc.OracleDatabaseException: ORA-01722: invalid number

	at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:636) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.T4CTTIoer11.processError(T4CTTIoer11.java:563) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.T4C8Oall.processError(T4C8Oall.java:1230) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.T4CTTIfun.receive(T4CTTIfun.java:771) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.T4CTTIfun.doRPC(T4CTTIfun.java:298) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.T4C8Oall.doOALL(T4C8Oall.java:511) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.T4CPreparedStatement.doOall8(T4CPreparedStatement.java:162) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.T4CPreparedStatement.executeForDescribe(T4CPreparedStatement.java:1009) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.OracleStatement.prepareDefineBufferAndExecute(OracleStatement.java:1270) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.OracleStatement.executeMaybeDescribe(OracleStatement.java:1148) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.OracleStatement.executeSQLSelect(OracleStatement.java:1660) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.OracleStatement.doExecuteWithTimeout(OracleStatement.java:1469) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.OraclePreparedStatement.executeInternal(OraclePreparedStatement.java:3760) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.OraclePreparedStatement.executeQuery(OraclePreparedStatement.java:3935) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.OraclePreparedStatementWrapper.executeQuery(OraclePreparedStatementWrapper.java:1101) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at com.zaxxer.hikari.pool.ProxyPreparedStatement.executeQuery(ProxyPreparedStatement.java:52) ~[HikariCP-5.1.0.jar:na]
	at com.zaxxer.hikari.pool.HikariProxyPreparedStatement.executeQuery(HikariProxyPreparedStatement.java) ~[HikariCP-5.1.0.jar:na]
	at org.hibernate.sql.results.jdbc.internal.DeferredResultSetAccess.executeQuery(DeferredResultSetAccess.java:246) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.jdbc.internal.DeferredResultSetAccess.getResultSet(DeferredResultSetAccess.java:167) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.jdbc.internal.AbstractResultSetAccess.getMetaData(AbstractResultSetAccess.java:36) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.jdbc.internal.AbstractResultSetAccess.getColumnCount(AbstractResultSetAccess.java:52) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.query.results.ResultSetMappingImpl.resolve(ResultSetMappingImpl.java:193) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.exec.internal.JdbcSelectExecutorStandardImpl.resolveJdbcValuesSource(JdbcSelectExecutorStandardImpl.java:327) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.exec.internal.JdbcSelectExecutorStandardImpl.doExecuteQuery(JdbcSelectExecutorStandardImpl.java:115) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.exec.internal.JdbcSelectExecutorStandardImpl.executeQuery(JdbcSelectExecutorStandardImpl.java:83) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.exec.spi.JdbcSelectExecutor.list(JdbcSelectExecutor.java:76) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.exec.spi.JdbcSelectExecutor.list(JdbcSelectExecutor.java:65) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.query.sql.internal.NativeSelectQueryPlanImpl.performList(NativeSelectQueryPlanImpl.java:138) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.query.sql.internal.NativeQueryImpl.doList(NativeQueryImpl.java:628) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.query.spi.AbstractSelectionQuery.list(AbstractSelectionQuery.java:423) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.query.Query.getResultList(Query.java:120) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.springframework.data.jpa.repository.query.JpaQueryExecution$CollectionExecution.doExecute(JpaQueryExecution.java:129) ~[spring-data-jpa-3.3.0.jar:3.3.0]
	at org.springframework.data.jpa.repository.query.JpaQueryExecution.execute(JpaQueryExecution.java:92) ~[spring-data-jpa-3.3.0.jar:3.3.0]
	at org.springframework.data.jpa.repository.query.AbstractJpaQuery.doExecute(AbstractJpaQuery.java:152) ~[spring-data-jpa-3.3.0.jar:3.3.0]
	at org.springframework.data.jpa.repository.query.AbstractJpaQuery.execute(AbstractJpaQuery.java:140) ~[spring-data-jpa-3.3.0.jar:3.3.0]
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker.doInvoke(RepositoryMethodInvoker.java:170) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker.invoke(RepositoryMethodInvoker.java:158) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.data.repository.core.support.QueryExecutorMethodInterceptor.doInvoke(QueryExecutorMethodInterceptor.java:164) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.data.repository.core.support.QueryExecutorMethodInterceptor.invoke(QueryExecutorMethodInterceptor.java:143) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.data.projection.DefaultMethodInvokingMethodInterceptor.invoke(DefaultMethodInvokingMethodInterceptor.java:70) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.transaction.interceptor.TransactionInterceptor$1.proceedWithInvocation(TransactionInterceptor.java:123) ~[spring-tx-6.1.8.jar:6.1.8]
	at org.springframework.transaction.interceptor.TransactionAspectSupport.invokeWithinTransaction(TransactionAspectSupport.java:392) ~[spring-tx-6.1.8.jar:6.1.8]
	at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:119) ~[spring-tx-6.1.8.jar:6.1.8]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.dao.support.PersistenceExceptionTranslationInterceptor.invoke(PersistenceExceptionTranslationInterceptor.java:137) ~[spring-tx-6.1.8.jar:6.1.8]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.data.jpa.repository.support.CrudMethodMetadataPostProcessor$CrudMethodMetadataPopulatingMethodInterceptor.invoke(CrudMethodMetadataPostProcessor.java:136) ~[spring-data-jpa-3.3.0.jar:3.3.0]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:97) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:223) ~[spring-aop-6.1.8.jar:6.1.8]
	at jdk.proxy4/jdk.proxy4.$Proxy157.getRW03Data(Unknown Source) ~[na:na]
	at com.crs.commonReportsService.services.RW05ServiceImpl.getRW03Data(RW05ServiceImpl.java:176) ~[classes/:na]
	at com.crs.commonReportsService.services.RW05ServiceImpl.tabData(RW05ServiceImpl.java:56) ~[classes/:na]
	at com.crs.commonReportsService.controllers.RW05Controller.tabData(RW05Controller.java:50) ~[classes/:na]
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

I am getting this error while hiting the api to fetch the data from table 
Method or query part of jpa 

@Repository
public interface CrsContLiabProvRepository extends JpaRepository<CrsContLiabProv,String> {

    @Query(value="SELECT\n" +
            "nvl(to_number(cont_liab_prov_lst_yr), 0) opening,\n" +
            "nvl(to_number(cont_liab_prov_add), 0) additions,\n" +
            "nvl(to_number(cont_liab_prov_used), 0) +\n" +
            "nvl(to_number(cont_liab_prov_unused), 0) reversals\n" +
            "FROM\n" +
            "crs_cont_liab_prov\n" +
            "WHERE\n" +
            "cont_liab_prov_branch = ?\n" +
            "AND cont_liab_prov_date = to_date(?,'dd/mm/yyyy')\n" +
            "AND cont_liab_prov_itemid = '18' ",nativeQuery = true)
    List<List<String>> getRW03Data(@Param("branch_code") String branch,
                     @Param("quarterEndDate") String quarterEndDate);

                     This is the table SQL as below

                     
  CREATE TABLE "FNSONLI"."CRS_CONT_LIAB_PROV" 
   (	"CONT_LIAB_PROV_BRANCH" VARCHAR2(5 BYTE) NOT NULL ENABLE, 
	"CONT_LIAB_PROV_DATE" DATE NOT NULL ENABLE, 
	"CONT_LIAB_PROV_ITEMID" VARCHAR2(20 BYTE), 
	"CONT_LIAB_PROV_LST_YR" VARCHAR2(20 BYTE), 
	"CONT_LIAB_PROV_ADD" VARCHAR2(20 BYTE), 
	"CONT_LIAB_PROV_USED" VARCHAR2(20 BYTE), 
	"CONT_LIAB_PROV_UNUSED" VARCHAR2(20 BYTE), 
	"CONT_LIAB_PROV_CUR_YR" VARCHAR2(20 BYTE), 
	"CONT_LIAB_PROV_REMARKS" VARCHAR2(500 BYTE), 
	"REPORT_MASTER_LIST_ID_FK" VARCHAR2(10 BYTE) NOT NULL ENABLE, 
	 CONSTRAINT "CRS_CONT_IDX1" UNIQUE ("CONT_LIAB_PROV_BRANCH", "CONT_LIAB_PROV_DATE", "CONT_LIAB_PROV_ITEMID")
  USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
  BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "TSDATA"  ENABLE
   ) SEGMENT CREATION IMMEDIATE 
  PCTFREE 10 PCTUSED 40 INITRANS 1 MAXTRANS 255 
 NOCOMPRESS LOGGING
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
  BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "TSDATA" ;

  CREATE INDEX "FNSONLI"."CRS_LIAB1" ON "FNSONLI"."CRS_CONT_LIAB_PROV" ("CONT_LIAB_PROV_BRANCH", "CONT_LIAB_PROV_DATE") 
  PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
  BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "TSDATA" ;

  CREATE INDEX "FNSONLI"."CRS_LIAB2" ON "FNSONLI"."CRS_CONT_LIAB_PROV" ("CONT_LIAB_PROV_BRANCH", "REPORT_MASTER_LIST_ID_FK", "CONT_LIAB_PROV_ITEMID") 
  PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS 
  STORAGE(INITIAL 65536 NEXT 1048576 MINEXTENTS 1 MAXEXTENTS 2147483645
  PCTINCREASE 0 FREELISTS 1 FREELIST GROUPS 1
  BUFFER_POOL DEFAULT FLASH_CACHE DEFAULT CELL_FLASH_CACHE DEFAULT)
  TABLESPACE "TSDATA" ;

