import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.web.authentication.UsernamePasswordAuthenticationFilter;

@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    private final AdfsFilter adfsFilter;

    public SecurityConfig(AdfsFilter adfsFilter) {
        this.adfsFilter = adfsFilter;
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/public/**").permitAll() // Public paths
                .antMatchers("/index.html").authenticated() // Protect index.html
                .anyRequest().authenticated() // All other paths require authentication
            .and()
            .oauth2Login()
                .defaultSuccessUrl("/home", true);

        // Add the ADFS filter only for requests to "index.html"
        http.addFilterBefore(adfsFilter, UsernamePasswordAuthenticationFilter.class)
            .requestMatcher(request -> request.getRequestURI().endsWith("index.html"));
    }
}