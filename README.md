package com.crs.SsoLoginService.Security;

import com.crs.SsoLoginService.auth10.federation.WSFederationFilter;
import jakarta.servlet.Filter;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter;

@Configuration
public class SecurityConfig {

    @Autowired
    private WSFederationFilter wsFederationFilter;

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
                // Disable CSRF protection if not needed
                .authorizeHttpRequests(authorize -> authorize
                        .requestMatchers("/", "/public/**").permitAll() // Allow public access to root path and public endpoints
                        .anyRequest().authenticated() // Protect all other endpoints
                )
                // Add your custom WS-Federation filter before the default security filters
                .addFilterBefore((Filter) wsFederationFilter, UsernamePasswordAuthenticationFilter.class);

        return http.build();
    }
}

This is the error i am getting 
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'securityFilterChain' defined in class path resource [com/crs/SsoLoginService/Security/SecurityConfig.class]: Failed to instantiate [org.springframework.security.web.SecurityFilterChain]: Factory method 'securityFilterChain' threw exception with message: class com.crs.SsoLoginService.auth10.federation.WSFederationFilter cannot be cast to class jakarta.servlet.Filter (com.crs.SsoLoginService.auth10.federation.WSFederationFilter is in unnamed module of loader org.springframework.boot.devtools.restart.classloader.RestartClassLoader @6282ea00; jakarta.servlet.Filter is in unnamed module of loader 'app')
	at org.springframework.beans.factory.support.ConstructorResolver.instantiate(ConstructorResolver.java:648) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.ConstructorResolver.instantiateUsingFactoryMethod(ConstructorResolver.java:636) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.instantiateUsingFactoryMethod(AbstractAutowireCapableBeanFactory.java:1337) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1167) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:562) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:522) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:337) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:335) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:200) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:975) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:962) ~[spring-context-6.1.8.jar:6.1.8]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624) ~[spring-context-6.1.8.jar:6.1.8]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146) ~[spring-boot-3.3.0.jar:3.3.0]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754) ~[spring-boot-3.3.0.jar:3.3.0]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456) ~[spring-boot-3.3.0.jar:3.3.0]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:335) ~[spring-boot-3.3.0.jar:3.3.0]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1363) ~[spring-boot-3.3.0.jar:3.3.0]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1352) ~[spring-boot-3.3.0.jar:3.3.0]
	at com.crs.SsoLoginService.SsoService.main(SsoService.java:10) ~[SSOLoginService/:na]
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
	at org.springframework.boot.devtools.restart.RestartLauncher.run(RestartLauncher.java:50) ~[spring-boot-devtools-3.3.0.jar:3.3.0]
Caused by: org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.security.web.SecurityFilterChain]: Factory method 'securityFilterChain' threw exception with message: class com.crs.SsoLoginService.auth10.federation.WSFederationFilter cannot be cast to class jakarta.servlet.Filter (com.crs.SsoLoginService.auth10.federation.WSFederationFilter is in unnamed module of loader org.springframework.boot.devtools.restart.classloader.RestartClassLoader @6282ea00; jakarta.servlet.Filter is in unnamed module of loader 'app')
	at org.springframework.beans.factory.support.SimpleInstantiationStrategy.instantiate(SimpleInstantiationStrategy.java:177) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.ConstructorResolver.instantiate(ConstructorResolver.java:644) ~[spring-beans-6.1.8.jar:6.1.8]
	... 22 common frames omitted
Caused by: java.lang.ClassCastException: class com.crs.SsoLoginService.auth10.federation.WSFederationFilter cannot be cast to class jakarta.servlet.Filter (com.crs.SsoLoginService.auth10.federation.WSFederationFilter is in unnamed module of loader org.springframework.boot.devtools.restart.classloader.RestartClassLoader @6282ea00; jakarta.servlet.Filter is in unnamed module of loader 'app')
	at com.crs.SsoLoginService.Security.SecurityConfig.securityFilterChain(SecurityConfig.java:22) ~[SSOLoginService/:na]
	at com.crs.SsoLoginService.Security.SecurityConfig$$SpringCGLIB$$0.CGLIB$securityFilterChain$0(<generated>) ~[SSOLoginService/:na]
	at com.crs.SsoLoginService.Security.SecurityConfig$$SpringCGLIB$$FastClass$$1.invoke(<generated>) ~[SSOLoginService/:na]
	at org.springframework.cglib.proxy.MethodProxy.invokeSuper(MethodProxy.java:258) ~[spring-core-6.1.8.jar:6.1.8]
	at org.springframework.context.annotation.ConfigurationClassEnhancer$BeanMethodInterceptor.intercept(ConfigurationClassEnhancer.java:339) ~[spring-context-6.1.8.jar:6.1.8]
	at com.crs.SsoLoginService.Security.SecurityConfig$$SpringCGLIB$$0.securityFilterChain(<generated>) ~[SSOLoginService/:na]
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
	at org.springframework.beans.factory.support.SimpleInstantiationStrategy.instantiate(SimpleInstantiationStrategy.java:140) ~[spring-beans-6.1.8.jar:6.1.8]
	... 23 common frames omitted


Process finished with exit code 0
