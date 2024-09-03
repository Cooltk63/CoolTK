2024-09-03T17:55:57.750+05:30  WARN 2784 --- [commonReportsService] [nio-8081-exec-1] o.h.engine.jdbc.spi.SqlExceptionHelper   : SQL Error: 17026, SQLState: 99999
2024-09-03T17:55:57.750+05:30 ERROR 2784 --- [commonReportsService] [nio-8081-exec-1] o.h.engine.jdbc.spi.SqlExceptionHelper   : Numeric Overflow
2024-09-03T17:55:57.750+05:30  INFO 2784 --- [commonReportsService] [nio-8081-exec-1] o.h.e.internal.DefaultLoadEventListener  : HHH000327: Error performing load command

org.hibernate.exception.GenericJDBCException: Could not extract column [5] from JDBC ResultSet [Numeric Overflow] [n/a]
	at org.hibernate.exception.internal.StandardSQLExceptionConverter.convert(StandardSQLExceptionConverter.java:63) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:108) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.engine.jdbc.spi.SqlExceptionHelper.convert(SqlExceptionHelper.java:94) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.jdbc.internal.JdbcValuesResultSetImpl.getCurrentRowValue(JdbcValuesResultSetImpl.java:387) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.internal.RowProcessingStateStandardImpl.getJdbcValue(RowProcessingStateStandardImpl.java:120) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.graph.basic.BasicResultAssembler.extractRawValue(BasicResultAssembler.java:52) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.graph.basic.BasicResultAssembler.assemble(BasicResultAssembler.java:59) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.graph.DomainResultAssembler.assemble(DomainResultAssembler.java:35) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.graph.entity.AbstractEntityInitializer.extractConcreteTypeStateValues(AbstractEntityInitializer.java:1037) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.graph.entity.AbstractEntityInitializer.initializeEntityInstance(AbstractEntityInitializer.java:794) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.graph.entity.AbstractEntityInitializer.initializeEntity(AbstractEntityInitializer.java:769) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.graph.entity.AbstractEntityInitializer.initializeInstance(AbstractEntityInitializer.java:761) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.internal.InitializersList.initializeInstance(InitializersList.java:73) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.internal.StandardRowReader.coordinateInitializers(StandardRowReader.java:113) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.internal.StandardRowReader.readRow(StandardRowReader.java:87) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.spi.ListResultsConsumer.consume(ListResultsConsumer.java:190) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.spi.ListResultsConsumer.consume(ListResultsConsumer.java:33) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.exec.internal.JdbcSelectExecutorStandardImpl.doExecuteQuery(JdbcSelectExecutorStandardImpl.java:211) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.exec.internal.JdbcSelectExecutorStandardImpl.executeQuery(JdbcSelectExecutorStandardImpl.java:83) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.exec.spi.JdbcSelectExecutor.list(JdbcSelectExecutor.java:76) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.exec.spi.JdbcSelectExecutor.list(JdbcSelectExecutor.java:65) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.loader.ast.internal.SingleIdLoadPlan.load(SingleIdLoadPlan.java:145) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.loader.ast.internal.SingleIdLoadPlan.load(SingleIdLoadPlan.java:117) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.loader.ast.internal.SingleIdEntityLoaderStandardImpl.load(SingleIdEntityLoaderStandardImpl.java:75) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.persister.entity.AbstractEntityPersister.doLoad(AbstractEntityPersister.java:3726) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.persister.entity.AbstractEntityPersister.load(AbstractEntityPersister.java:3715) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultLoadEventListener.loadFromDatasource(DefaultLoadEventListener.java:604) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultLoadEventListener.loadFromCacheOrDatasource(DefaultLoadEventListener.java:590) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultLoadEventListener.load(DefaultLoadEventListener.java:560) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultLoadEventListener.doLoad(DefaultLoadEventListener.java:544) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultLoadEventListener.load(DefaultLoadEventListener.java:207) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultLoadEventListener.loadWithRegularProxy(DefaultLoadEventListener.java:290) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultLoadEventListener.proxyOrLoad(DefaultLoadEventListener.java:242) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultLoadEventListener.doOnLoad(DefaultLoadEventListener.java:111) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultLoadEventListener.onLoad(DefaultLoadEventListener.java:68) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.service.internal.EventListenerGroupImpl.fireEventOnEachListener(EventListenerGroupImpl.java:138) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.internal.SessionImpl.fireLoadNoChecks(SessionImpl.java:1225) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.internal.SessionImpl.fireLoad(SessionImpl.java:1213) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.load(IdentifierLoadAccessImpl.java:209) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.doLoad(IdentifierLoadAccessImpl.java:160) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.lambda$load$1(IdentifierLoadAccessImpl.java:149) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.perform(IdentifierLoadAccessImpl.java:112) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.load(IdentifierLoadAccessImpl.java:149) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.internal.SessionImpl.get(SessionImpl.java:1026) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultMergeEventListener.lambda$entityIsDetached$0(DefaultMergeEventListener.java:408) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.engine.spi.LoadQueryInfluencers.fromInternalFetchProfile(LoadQueryInfluencers.java:106) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultMergeEventListener.entityIsDetached(DefaultMergeEventListener.java:406) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultMergeEventListener.merge(DefaultMergeEventListener.java:210) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultMergeEventListener.doMerge(DefaultMergeEventListener.java:148) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultMergeEventListener.onMerge(DefaultMergeEventListener.java:132) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.internal.DefaultMergeEventListener.onMerge(DefaultMergeEventListener.java:86) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.event.service.internal.EventListenerGroupImpl.fireEventOnEachListener(EventListenerGroupImpl.java:127) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.internal.SessionImpl.fireMerge(SessionImpl.java:850) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.internal.SessionImpl.merge(SessionImpl.java:836) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
	at org.springframework.orm.jpa.ExtendedEntityManagerCreator$ExtendedEntityManagerInvocationHandler.invoke(ExtendedEntityManagerCreator.java:364) ~[spring-orm-6.1.8.jar:6.1.8]
	at jdk.proxy4/jdk.proxy4.$Proxy139.merge(Unknown Source) ~[na:na]
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
	at org.springframework.orm.jpa.SharedEntityManagerCreator$SharedEntityManagerInvocationHandler.invoke(SharedEntityManagerCreator.java:319) ~[spring-orm-6.1.8.jar:6.1.8]
	at jdk.proxy4/jdk.proxy4.$Proxy139.merge(Unknown Source) ~[na:na]
	at org.springframework.data.jpa.repository.support.SimpleJpaRepository.save(SimpleJpaRepository.java:631) ~[spring-data-jpa-3.3.0.jar:3.3.0]
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
	at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:354) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker$RepositoryFragmentMethodInvoker.lambda$new$0(RepositoryMethodInvoker.java:277) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker.doInvoke(RepositoryMethodInvoker.java:170) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker.invoke(RepositoryMethodInvoker.java:158) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.data.repository.core.support.RepositoryComposition$RepositoryFragments.invoke(RepositoryComposition.java:516) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.data.repository.core.support.RepositoryComposition.invoke(RepositoryComposition.java:285) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.data.repository.core.support.RepositoryFactorySupport$ImplementationMethodExecutionInterceptor.invoke(RepositoryFactorySupport.java:628) ~[spring-data-commons-3.3.0.jar:3.3.0]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.data.repository.core.support.QueryExecutorMethodInterceptor.doInvoke(QueryExecutorMethodInterceptor.java:168) ~[spring-data-commons-3.3.0.jar:3.3.0]
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
	at org.springframework.data.jpa.repository.support.CrudMethodMetadataPostProcessor$CrudMethodMetadataPopulatingMethodInterceptor.invoke(CrudMethodMetadataPostProcessor.java:165) ~[spring-data-jpa-3.3.0.jar:3.3.0]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:97) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184) ~[spring-aop-6.1.8.jar:6.1.8]
	at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:223) ~[spring-aop-6.1.8.jar:6.1.8]
	at jdk.proxy4/jdk.proxy4.$Proxy157.save(Unknown Source) ~[na:na]
	at com.crs.commonReportsService.services.RW46ServiceImpl.update(RW46ServiceImpl.java:279) ~[classes/:na]
	at com.crs.commonReportsService.controllers.RW46Controller.update(RW46Controller.java:45) ~[classes/:na]
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
Caused by: java.sql.SQLException: Numeric Overflow
	at oracle.jdbc.driver.NumberCommonAccessor.throwOverflow(NumberCommonAccessor.java:4161) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.NumberCommonAccessor.getInt(NumberCommonAccessor.java:111) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.GeneratedStatement.getInt(GeneratedStatement.java:171) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at oracle.jdbc.driver.GeneratedScrollableResultSet.getInt(GeneratedScrollableResultSet.java:269) ~[ojdbc11-21.9.0.0.jar:21.9.0.0.0]
	at com.zaxxer.hikari.pool.HikariProxyResultSet.getInt(HikariProxyResultSet.java) ~[HikariCP-5.1.0.jar:na]
	at org.hibernate.type.descriptor.jdbc.IntegerJdbcType$2.doExtract(IntegerJdbcType.java:87) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.type.descriptor.jdbc.BasicExtractor.extract(BasicExtractor.java:44) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	at org.hibernate.sql.results.jdbc.internal.JdbcValuesResultSetImpl.getCurrentRowValue(JdbcValuesResultSetImpl.java:379) ~[hibernate-core-6.5.2.Final.jar:6.5.2.Final]
	... 140 common frames omitted

2024-09-03T17:55:57.762+05:30  INFO 2784 --- [commonReportsService] [nio-8081-exec-1] c.c.c.services.RW46ServiceImpl           : Exception Occurred :org.hibernate.exception.GenericJDBCException: Could not extract column [5] from JDBC ResultSet [Numeric Overflow] [n/a]
2024-09-03T17:55:57.762+05:30  INFO 2784 --- [commonReportsService] [nio-8081-exec-1] c.c.c.services.RW46ServiceImpl           : Exception Occurred :Could not extract column [5] from JDBC ResultSet [Numeric Overflow] [n/a]
org.springframework.orm.jpa.JpaSystemException: Could not extract column [5] from JDBC ResultSet [Numeric Overflow] [n/a]
	at org.springframework.orm.jpa.vendor.HibernateJpaDialect.convertHibernateAccessException(HibernateJpaDialect.java:341)
	at org.springframework.orm.jpa.vendor.HibernateJpaDialect.translateExceptionIfPossible(HibernateJpaDialect.java:241)
	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.translateExceptionIfPossible(AbstractEntityManagerFactoryBean.java:550)
	at org.springframework.dao.support.ChainedPersistenceExceptionTranslator.translateExceptionIfPossible(ChainedPersistenceExceptionTranslator.java:61)
	at org.springframework.dao.support.DataAccessUtils.translateIfNecessary(DataAccessUtils.java:335)
	at org.springframework.dao.support.PersistenceExceptionTranslationInterceptor.invoke(PersistenceExceptionTranslationInterceptor.java:152)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.data.jpa.repository.support.CrudMethodMetadataPostProcessor$CrudMethodMetadataPopulatingMethodInterceptor.invoke(CrudMethodMetadataPostProcessor.java:165)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.aop.interceptor.ExposeInvocationInterceptor.invoke(ExposeInvocationInterceptor.java:97)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:223)
	at jdk.proxy4/jdk.proxy4.$Proxy157.save(Unknown Source)
	at com.crs.commonReportsService.services.RW46ServiceImpl.update(RW46ServiceImpl.java:279)
	at com.crs.commonReportsService.controllers.RW46Controller.update(RW46Controller.java:45)
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
Caused by: org.hibernate.exception.GenericJDBCException: Could not extract column [5] from JDBC ResultSet [Numeric Overflow] [n/a]
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
	at org.hibernate.sql.results.spi.ListResultsConsumer.consume(ListResultsConsumer.java:190)
	at org.hibernate.sql.results.spi.ListResultsConsumer.consume(ListResultsConsumer.java:33)
	at org.hibernate.sql.exec.internal.JdbcSelectExecutorStandardImpl.doExecuteQuery(JdbcSelectExecutorStandardImpl.java:211)
	at org.hibernate.sql.exec.internal.JdbcSelectExecutorStandardImpl.executeQuery(JdbcSelectExecutorStandardImpl.java:83)
	at org.hibernate.sql.exec.spi.JdbcSelectExecutor.list(JdbcSelectExecutor.java:76)
	at org.hibernate.sql.exec.spi.JdbcSelectExecutor.list(JdbcSelectExecutor.java:65)
	at org.hibernate.loader.ast.internal.SingleIdLoadPlan.load(SingleIdLoadPlan.java:145)
	at org.hibernate.loader.ast.internal.SingleIdLoadPlan.load(SingleIdLoadPlan.java:117)
	at org.hibernate.loader.ast.internal.SingleIdEntityLoaderStandardImpl.load(SingleIdEntityLoaderStandardImpl.java:75)
	at org.hibernate.persister.entity.AbstractEntityPersister.doLoad(AbstractEntityPersister.java:3726)
	at org.hibernate.persister.entity.AbstractEntityPersister.load(AbstractEntityPersister.java:3715)
	at org.hibernate.event.internal.DefaultLoadEventListener.loadFromDatasource(DefaultLoadEventListener.java:604)
	at org.hibernate.event.internal.DefaultLoadEventListener.loadFromCacheOrDatasource(DefaultLoadEventListener.java:590)
	at org.hibernate.event.internal.DefaultLoadEventListener.load(DefaultLoadEventListener.java:560)
	at org.hibernate.event.internal.DefaultLoadEventListener.doLoad(DefaultLoadEventListener.java:544)
	at org.hibernate.event.internal.DefaultLoadEventListener.load(DefaultLoadEventListener.java:207)
	at org.hibernate.event.internal.DefaultLoadEventListener.loadWithRegularProxy(DefaultLoadEventListener.java:290)
	at org.hibernate.event.internal.DefaultLoadEventListener.proxyOrLoad(DefaultLoadEventListener.java:242)
	at org.hibernate.event.internal.DefaultLoadEventListener.doOnLoad(DefaultLoadEventListener.java:111)
	at org.hibernate.event.internal.DefaultLoadEventListener.onLoad(DefaultLoadEventListener.java:68)
	at org.hibernate.event.service.internal.EventListenerGroupImpl.fireEventOnEachListener(EventListenerGroupImpl.java:138)
	at org.hibernate.internal.SessionImpl.fireLoadNoChecks(SessionImpl.java:1225)
	at org.hibernate.internal.SessionImpl.fireLoad(SessionImpl.java:1213)
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.load(IdentifierLoadAccessImpl.java:209)
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.doLoad(IdentifierLoadAccessImpl.java:160)
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.lambda$load$1(IdentifierLoadAccessImpl.java:149)
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.perform(IdentifierLoadAccessImpl.java:112)
	at org.hibernate.loader.internal.IdentifierLoadAccessImpl.load(IdentifierLoadAccessImpl.java:149)
	at org.hibernate.internal.SessionImpl.get(SessionImpl.java:1026)
	at org.hibernate.event.internal.DefaultMergeEventListener.lambda$entityIsDetached$0(DefaultMergeEventListener.java:408)
	at org.hibernate.engine.spi.LoadQueryInfluencers.fromInternalFetchProfile(LoadQueryInfluencers.java:106)
	at org.hibernate.event.internal.DefaultMergeEventListener.entityIsDetached(DefaultMergeEventListener.java:406)
	at org.hibernate.event.internal.DefaultMergeEventListener.merge(DefaultMergeEventListener.java:210)
	at org.hibernate.event.internal.DefaultMergeEventListener.doMerge(DefaultMergeEventListener.java:148)
	at org.hibernate.event.internal.DefaultMergeEventListener.onMerge(DefaultMergeEventListener.java:132)
	at org.hibernate.event.internal.DefaultMergeEventListener.onMerge(DefaultMergeEventListener.java:86)
	at org.hibernate.event.service.internal.EventListenerGroupImpl.fireEventOnEachListener(EventListenerGroupImpl.java:127)
	at org.hibernate.internal.SessionImpl.fireMerge(SessionImpl.java:850)
	at org.hibernate.internal.SessionImpl.merge(SessionImpl.java:836)
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
	at org.springframework.orm.jpa.ExtendedEntityManagerCreator$ExtendedEntityManagerInvocationHandler.invoke(ExtendedEntityManagerCreator.java:364)
	at jdk.proxy4/jdk.proxy4.$Proxy139.merge(Unknown Source)
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
	at org.springframework.orm.jpa.SharedEntityManagerCreator$SharedEntityManagerInvocationHandler.invoke(SharedEntityManagerCreator.java:319)
	at jdk.proxy4/jdk.proxy4.$Proxy139.merge(Unknown Source)
	at org.springframework.data.jpa.repository.support.SimpleJpaRepository.save(SimpleJpaRepository.java:631)
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103)
	at java.base/java.lang.reflect.Method.invoke(Method.java:580)
	at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:354)
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker$RepositoryFragmentMethodInvoker.lambda$new$0(RepositoryMethodInvoker.java:277)
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker.doInvoke(RepositoryMethodInvoker.java:170)
	at org.springframework.data.repository.core.support.RepositoryMethodInvoker.invoke(RepositoryMethodInvoker.java:158)
	at org.springframework.data.repository.core.support.RepositoryComposition$RepositoryFragments.invoke(RepositoryComposition.java:516)
	at org.springframework.data.repository.core.support.RepositoryComposition.invoke(RepositoryComposition.java:285)
	at org.springframework.data.repository.core.support.RepositoryFactorySupport$ImplementationMethodExecutionInterceptor.invoke(RepositoryFactorySupport.java:628)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.data.repository.core.support.QueryExecutorMethodInterceptor.doInvoke(QueryExecutorMethodInterceptor.java:168)
	at org.springframework.data.repository.core.support.QueryExecutorMethodInterceptor.invoke(QueryExecutorMethodInterceptor.java:143)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.data.projection.DefaultMethodInvokingMethodInterceptor.invoke(DefaultMethodInvokingMethodInterceptor.java:70)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.transaction.interceptor.TransactionInterceptor$1.proceedWithInvocation(TransactionInterceptor.java:123)
	at org.springframework.transaction.interceptor.TransactionAspectSupport.invokeWithinTransaction(TransactionAspectSupport.java:392)
	at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:119)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:184)
	at org.springframework.dao.support.PersistenceExceptionTranslationInterceptor.invoke(PersistenceExceptionTranslationInterceptor.java:137)
	... 61 more
Caused by: java.sql.SQLException: Numeric Overflow
	at oracle.jdbc.driver.NumberCommonAccessor.throwOverflow(NumberCommonAccessor.java:4161)
	at oracle.jdbc.driver.NumberCommonAccessor.getInt(NumberCommonAccessor.java:111)
	at oracle.jdbc.driver.GeneratedStatement.getInt(GeneratedStatement.java:171)
	at oracle.jdbc.driver.GeneratedScrollableResultSet.getInt(GeneratedScrollableResultSet.java:269)
	at com.zaxxer.hikari.pool.HikariProxyResultSet.getInt(HikariProxyResultSet.java)
	at org.hibernate.type.descriptor.jdbc.IntegerJdbcType$2.doExtract(IntegerJdbcType.java:87)
	at org.hibernate.type.descriptor.jdbc.BasicExtractor.extract(BasicExtractor.java:44)
	at org.hibernate.sql.results.jdbc.internal.JdbcValuesResultSetImpl.getCurrentRowValue(JdbcValuesResultSetImpl.java:379)
	... 140 more
