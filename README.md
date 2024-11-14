import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter;
import org.springframework.security.web.util.matcher.AntPathRequestMatcher;

@Configuration
public class SecurityConfig {

    private final ApiCallFilter apiCallFilter;

    public SecurityConfig(ApiCallFilter apiCallFilter) {
        this.apiCallFilter = apiCallFilter;
    }

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        // Define a matcher for the "/Test" endpoint
        AntPathRequestMatcher testEndpointMatcher = new AntPathRequestMatcher("/Test");

        // Configure security for "/Test" only
        http
            .securityMatcher(testEndpointMatcher)  // Apply security only on /Test
            .authorizeHttpRequests(authorize -> authorize
                .anyRequest().permitAll()  // Allow all requests without security constraints
            )
            .addFilterBefore(apiCallFilter, UsernamePasswordAuthenticationFilter.class);

        // Configure global security for other endpoints if needed
        http
            .authorizeHttpRequests(authorize -> authorize
                .anyRequest().permitAll()
            );

        return http.build();
    }
}