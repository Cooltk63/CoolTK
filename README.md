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
                )
                // Add your custom WS-Federation filter before the default security filters
                .addFilterBefore((Filter) wsFederationFilter, UsernamePasswordAuthenticationFilter.class);

        return http.build();
    }
}
