import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter;

@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    private final WSFederationFilter wsFederationFilter;

    public SecurityConfig(WSFederationFilter wsFederationFilter) {
        this.wsFederationFilter = wsFederationFilter;
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/public/**").permitAll() // Allow public access to specific paths
                .antMatchers("/").authenticated() // Protect the root URL (landing page)
                .anyRequest().authenticated()
            .and()
            .oauth2Login()
                .defaultSuccessUrl("/home", true);

        // Apply the filter only for requests to the root URL "/"
        http.addFilterBefore(wsFederationFilter, UsernamePasswordAuthenticationFilter.class)
            .requestMatcher(request -> request.getRequestURI().equals("/"));
    }
}