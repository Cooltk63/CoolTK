import org.springframework.context.annotation.Bean;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.security.web.util.matcher.AntPathRequestMatcher;

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
            .addFilterBefore(apiCallFilter, UsernamePasswordAuthenticationFilter.class)
            .requestMatcher(new AntPathRequestMatcher("/Test"));  // Apply filter only on /Test

        return http.build();
    }
}