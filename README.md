l[14/11, 5:30 pm] Falguni Nakhwa - TCS: import jakarta.servlet.FilterChain;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework.stereotype.Component;
import org.springframework.web.filter.OncePerRequestFilter;

import java.io.IOException;

@Component
public class ApiCallFilter extends OncePerRequestFilter {

    @Override
    protected void doFilterInternal(HttpServletRequest request,
                                    HttpServletResponse response,
                                    FilterChain filterChain) throws ServletException, IOException {
        // You can add any logic here. For example, log request details.
        String requestUri = request.getRequestURI();
        System.out.println("API call to: " + requestUri);

        // Continue the filter chain
        filterChain.doFilter(request, response);
    }
}
[14/11, 5:30 pm] Falguni Nakhwa - TCS: import org.springframework.context.annotation.Bean;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter;

@Configuration
public class SecurityConfig {

    private final ApiCallFilter apiCallFilter;

    public SecurityConfig(ApiCallFilter apiCallFilter) {
        this.apiCallFilter = apiCallFilter;
    }

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .authorizeHttpRequests(authorize -> authorize
                .anyRequest().permitAll()  // Allow all requests without security constraints
            )
            .addFilterBefore(apiCallFilter, UsernamePasswordAuthenticationFilter.class);

        return http.build();
    }
}