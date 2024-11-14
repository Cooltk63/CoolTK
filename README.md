This is my WSFederationFilter class 
package com.crs.SsoLoginService.auth10.federation;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Component;

import javax.servlet.*;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.regex.Pattern;

@Component
public class WSFederationFilter implements Filter {

	private static final String PRINCIPAL_SESSION_VARIABLE = "FederatedPrincipal";

	private String loginPage;
	private String excludedUrlsRegex;
	private String excludedUrlsRegex_JS;
	private String excludedUrlsRegex_CSS;
	
	final Logger logger = LoggerFactory.getLogger(WSFederationFilter.class.getName());
	static org.apache.log4j.Logger log = org.apache.log4j.Logger.getLogger(WSFederationFilter.class.getName());

	public WSFederationFilter() {
		logger.debug("constructing");
	}

	@Override
	public void init(FilterConfig config) throws ServletException {
		//logger.debug("initializing");
		this.loginPage = config.getInitParameter("login-page-url");
		this.excludedUrlsRegex = config.getInitParameter("exclude-urls-regex");
		this.excludedUrlsRegex_JS = config.getInitParameter("exclude-urls-regex-js");
		this.excludedUrlsRegex_CSS = config.getInitParameter("exclude-urls-regex-css");
		//logger.info("excludedUrlsRegex <><><> " + excludedUrlsRegex);
		
	}

	@Override
	public void doFilter(ServletRequest request, ServletResponse response,
			FilterChain chain) throws IOException, ServletException {

		log.info("filtering");

		FederatedPrincipal principal = null;
		HttpServletRequest httpRequest = (HttpServletRequest) request;
		HttpServletResponse httpResponse = (HttpServletResponse) response;
		String path =  httpRequest.getRequestURL().toString();

		boolean checkSession = sessionTokenExists(httpRequest);
		log.info("checkSession <><><> " + checkSession);
		
			// is the request is a token?
			if(checkSession == false){ // Condition Added By Deepak
				log.info("WSFederationFilter doFilter httpRequest >>>>>>> " + httpRequest.getRequestURI());
				if (this.isSignInResponse(httpRequest)) {
					log.info("authenticating with token");
					log.info("WSFederationFilter doFilter principal >>>>>>> " + principal);
					log.info("WSFederationFilter doFilter httpResponse >>>>>>> " + httpResponse);
					principal = this.authenticateWithToken(httpRequest, httpResponse);
					log.info("WSFederationFilter doFilter principal >>>>>>> " + principal);
					this.writeSessionToken(httpRequest, principal);
					this.redirectToOriginalUrl(httpRequest, httpResponse);
				}
			}
		log.info("authenticating with token");
			// is principal in session?
			if (principal == null && this.sessionTokenExists(httpRequest)) {
				log.info("authenticating with session token");
				principal = this.authenticateWithSessionToken(httpRequest,
						httpResponse);
			}
		log.info("authenticating with token " + principal);
			// if not authenticated at this point, redirect to login page
			//logger.info("httpRequest.getRequestURL().toString() <><> " + httpRequest.getRequestURL().toString());
			//logger.info("Matcher <><><> " + Pattern.compile(this.excludedUrlsRegex).matcher(httpRequest.getRequestURL().toString()).find());
			
			boolean excludedUrl = httpRequest.getRequestURL().toString().contains(this.loginPage) 
								  || (this.excludedUrlsRegex != null
							      && !this.excludedUrlsRegex.isEmpty() 
							      && Pattern.compile(this.excludedUrlsRegex).matcher(httpRequest.getRequestURL().toString()).find()); 
//							      || (this.excludedUrlsRegex != null
//									  && !this.excludedUrlsRegex.isEmpty() 
//									  && Pattern.compile(this.excludedUrlsRegex).matcher(httpRequest.getRequestURL().toString()).find());

			//logger.info("excludedUrl <><><> " + excludedUrl);
			if(excludedUrl){
				logger.info("excludedUrl <><> " + excludedUrl);
			}
			
			if (!excludedUrl && principal == null) {
				log.info("INSIDE  Condition 1");
				if (!FederatedConfiguration.getInstance().getEnableManualRedirect()) {
					log.info("INSIDE  Condition 2");
					log.info("redirecting to identity provider");
					this.redirectToIdentityProvider(httpRequest, httpResponse);
				} else {
					log.info("INSIDE  Condition 3");
					log.info("redirecting to login page");
					this.redirectToLoginPage(httpRequest, httpResponse);
				}

				return;
			}
		log.info("principal=" + principal);
		log.info("excludedUrlsRegex <><> " + excludedUrlsRegex);
		log.info("path.toLowerCase() <><> " + path.toLowerCase());
			boolean pathVal =  path.toLowerCase().contains(excludedUrlsRegex);
		log.info("pathVal <><> " + pathVal);
				chain.doFilter(new FederatedHttpServletRequest(httpRequest, principal),response);
//			}
			
			
		
	}

	protected void redirectToLoginPage(HttpServletRequest httpRequest,
			HttpServletResponse httpResponse) {
		String encodedReturnUrl = URLUTF8Encoder
				.encode(getRequestPathAndQuery(httpRequest));
		String redirect = this.loginPage + "?returnUrl=" + encodedReturnUrl;
		httpResponse.setHeader("Location", redirect);
		httpResponse.setStatus(302);
	}

	protected void redirectToIdentityProvider(HttpServletRequest httpRequest,
			HttpServletResponse httpResponse) {
		String wctx = getRequestPathAndQuery(httpRequest);
		String redirect = FederatedLoginManager.getFederatedLoginUrl(wctx);
		httpResponse.setHeader("Location", redirect);
		httpResponse.setStatus(302);
	}

	protected void redirectToOriginalUrl(HttpServletRequest httpRequest,
			HttpServletResponse httpResponse) {
		String wctx = httpRequest.getParameter("wctx");
		log.info("wctx >>>> ");
		if (wctx != null) {
			httpResponse.setHeader("Location", wctx);
			httpResponse.setStatus(302);
		}
	}

	protected Boolean isSignInResponse(HttpServletRequest request) {
	//logger.info("request.getMethod().equals(POST) <><><> " + request.getMethod().equals("POST"));
	//logger.info("request.getParameter(wa) <><><> " + request.getParameter("wa"));
	//logger.info("request.getParameter(wresult) <><><> " + request.getParameter("wresult"));
	
//		if(!request.getParameter("wa").equalsIgnoreCase("null")){
//			logger.info("HIISJHGFHJGFHJGFHJFSGJHGF");
//		}
		if (request.getMethod().equals("POST")
				&& request.getParameter("wa").equals("wsignin1.0")
				&& request.getParameter("wresult") != null) {
			return true;
		}

		return false;
	}

	protected Boolean sessionTokenExists(HttpServletRequest request) {
		// this could use signed cookies instead of sessions
		return request.getSession().getAttribute(PRINCIPAL_SESSION_VARIABLE) != null;
	}

	protected FederatedPrincipal authenticateWithSessionToken(
			HttpServletRequest request, HttpServletResponse response)
			throws IOException {
		return (FederatedPrincipal) request.getSession().getAttribute(
				PRINCIPAL_SESSION_VARIABLE);
	}

	protected void writeSessionToken(HttpServletRequest request,
			FederatedPrincipal principal) throws IOException {
		request.getSession()
				.setAttribute(PRINCIPAL_SESSION_VARIABLE, principal);
	}

	protected FederatedPrincipal authenticateWithToken(
			HttpServletRequest request, HttpServletResponse response)
			throws IOException {
		String token = request.getParameter("wresult").toString();

		if (token == null) {
			log.info("token Value is null <><><><> " + token);
			sendError(request, response, 400,
					"You were supposed to send a wresult parameter with a token");
		}

		FederatedLoginManager loginManager = FederatedLoginManager.fromRequest(
				request, null);

		try {

			log.info("token Value <><><><> " + token);
			log.info("response Value <><><><> " + response);
			FederatedPrincipal principal = loginManager.authenticate(token,response);  //
			log.info("principal <<><><> " + principal);
			log.info("principal <<><><> " + principal);
			return principal;
		} catch (FederationException e) {
			e.printStackTrace();
			//logger.error(e.getMessage(), e);
			log.info("FederationException :" + e.getMessage());
			sendError(request, response, 500,
					"Oops an error occurred validating the token.");
		}

		return null;
	}

	private void sendError(HttpServletRequest request,
			HttpServletResponse response, int errorNum, String message)
			throws IOException {
		// create the session to avoid IllegalStateException: Cannot create
		// a session after the response has been committed.
		request.getSession();
		//logger.warn("response " + errorNum + ": " + message);
		response.sendError(errorNum, message);
	}

	@Override
	public void destroy() {
	}

	private static String getRequestPathAndQuery(HttpServletRequest req) {
		String reqUri = req.getRequestURI().toString();
		String queryString = req.getQueryString();
		if (queryString != null) {
			reqUri += "?" + queryString;
		}

		return reqUri;
	}
}

This is my Security Config Class
package com.crs.SsoLoginService.Security;

import com.crs.SsoLoginService.auth10.federation.WSFederationFilter;
import jakarta.servlet.Filter;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
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
                ).addFilter((Filter) wsFederationFilter);
                // Add your custom WS-Federation filter before the default security filters
                //.addFilterBefore((Filter) wsFederationFilter, UsernamePasswordAuthenticationFilter.class);

        return http.build();
    }
}

This is the error i am getting 


Error starting ApplicationContext. To display the condition evaluation report re-run your application with 'debug' enabled.
2024-11-14T14:59:10.848+05:30 ERROR 19936 --- [SsoLoginService] [           main] o.s.boot.SpringApplication               : Application run failed

org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'securityFilterChain' defined in class path resource [com/crs/SsoLoginService/Security/SecurityConfig.class]: Failed to instantiate [org.springframework.security.web.SecurityFilterChain]: Factory method 'securityFilterChain' threw exception with message: class com.crs.SsoLoginService.auth10.federation.WSFederationFilter cannot be cast to class jakarta.servlet.Filter (com.crs.SsoLoginService.auth10.federation.WSFederationFilter and jakarta.servlet.Filter are in unnamed module of loader 'app')
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
Caused by: org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.security.web.SecurityFilterChain]: Factory method 'securityFilterChain' threw exception with message: class com.crs.SsoLoginService.auth10.federation.WSFederationFilter cannot be cast to class jakarta.servlet.Filter (com.crs.SsoLoginService.auth10.federation.WSFederationFilter and jakarta.servlet.Filter are in unnamed module of loader 'app')
	at org.springframework.beans.factory.support.SimpleInstantiationStrategy.instantiate(SimpleInstantiationStrategy.java:177) ~[spring-beans-6.1.8.jar:6.1.8]
	at org.springframework.beans.factory.support.ConstructorResolver.instantiate(ConstructorResolver.java:644) ~[spring-beans-6.1.8.jar:6.1.8]
	... 19 common frames omitted
Caused by: java.lang.ClassCastException: class com.crs.SsoLoginService.auth10.federation.WSFederationFilter cannot be cast to class jakarta.servlet.Filter (com.crs.SsoLoginService.auth10.federation.WSFederationFilter and jakarta.servlet.Filter are in unnamed module of loader 'app')
	at com.crs.SsoLoginService.Security.SecurityConfig.securityFilterChain(SecurityConfig.java:23) ~[SSOLoginService/:na]
	at com.crs.SsoLoginService.Security.SecurityConfig$$SpringCGLIB$$0.CGLIB$securityFilterChain$0(<generated>) ~[SSOLoginService/:na]
	at com.crs.SsoLoginService.Security.SecurityConfig$$SpringCGLIB$$FastClass$$1.invoke(<generated>) ~[SSOLoginService/:na]
	at org.springframework.cglib.proxy.MethodProxy.invokeSuper(MethodProxy.java:258) ~[spring-core-6.1.8.jar:6.1.8]
	at org.springframework.context.annotation.ConfigurationClassEnhancer$BeanMethodInterceptor.intercept(ConfigurationClassEnhancer.java:339) ~[spring-context-6.1.8.jar:6.1.8]
	at com.crs.SsoLoginService.Security.SecurityConfig$$SpringCGLIB$$0.securityFilterChain(<generated>) ~[SSOLoginService/:na]
	at java.base/jdk.internal.reflect.DirectMethodHandleAccessor.invoke(DirectMethodHandleAccessor.java:103) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Method.java:580) ~[na:na]
	at org.springframework.beans.factory.support.SimpleInstantiationStrategy.instantiate(SimpleInstantiationStrategy.java:140) ~[spring-beans-6.1.8.jar:6.1.8]
	... 20 common frames omitted
