import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.beans.factory.annotation.Autowired;

@Configuration
public class SecurityConfig {

    @Autowired
    private WsFederationFilter wsFederationFilter;

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .csrf().disable() // Disable CSRF protection if not needed
            .authorizeHttpRequests(authorize -> authorize
                .requestMatchers("/", "/public/**").permitAll() // Allow public access to root path and public endpoints
                .anyRequest().authenticated() // Protect all other endpoints
            )
            // Add your custom WS-Federation filter before the default security filters
            .addFilterBefore(wsFederationFilter, SecurityFilterChain.class);

        return http.build();
    }
}