org.apache.logging.log4j:log4j-core:pom:2.23.1 failed to transfer from http://0.0.0.0/ during a previous attempt. This failure was cached in the local repository and resolution is not reattempted until the update interval of maven-default-http-blocker has elapsed or updates are forced. Original error: Could not transfer artifact org.apache.logging.log4j:log4j-core:pom:2.23.1 from/to maven-default-http-blocker (http://0.0.0.0/): Blocked mirror for repositories: [my-repo (http://10.191.167.23:443/repository/, default, releases+snapshots)]

Since Maven 3.8.1 http repositories are blocked.

Possible solutions:
- Check that Maven settings.xml does not contain http repositories
- Check that Maven pom files do not contain http repository http://10.191.167.23:443/repository/
- Add a mirror(s) for http://10.191.167.23:443/repository/ that allows http url in the Maven settings.xml
- Downgrade Maven to version 3.8.1 or earlier in settings



this is the error i am getting while reloading or updating dependency via my local server

My settings.xml file as per below 
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <proxies>
        <proxy>
            <id>alias</id>
            <active>true</active>
            <protocol>https</protocol>
            <host>swg.sbi.co.in</host>
            <port>9090</port>
            <username>V1012297</username>
            <password>Tush##2485</password>
            <nonProxyHosts>http://10.191.167.23:443/repository/</nonProxyHosts>
<!--            <nonProxyHosts>https://repo.maven.apache.org/maven2</nonProxyHosts>-->
        </proxy>
    </proxies>
</settings>


also my pom.xml file as per below 
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://maven.apache.org/POM/4.0.0"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.3.0</version>
    </parent>
    <repositories>
        <repository>
            <id>my-repo</id>
            <name>My Repository</name>
            <url>http://10.191.167.23:443/repository/</url>
        </repository>
    </repositories>
    <groupId>com.crs</groupId>
    <artifactId>reportSubmission</artifactId>
    <version>0.0.2</version>
    <packaging>war</packaging>
    <name>reportSubmission</name>
    <description>reportSubmission</description>
    <properties>
        <java.version>17</java.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-actuator</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
            <scope>runtime</scope>
            <optional>true</optional>
        </dependency>
        <dependency>
            <groupId>com.oracle.database.jdbc</groupId>
            <artifactId>ojdbc11</artifactId>
            <scope>runtime</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
            <scope>provided</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency><!-- https://mvnrepository.com/artifact/io.jsonwebtoken/jjwt-api -->
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-api</artifactId>
            <version>0.12.6</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/io.jsonwebtoken/jjwt-impl -->
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-impl</artifactId>
            <version>0.12.6</version>
            <scope>runtime</scope>
        </dependency>
        <!-- https://mvnrepository.com/artifact/io.jsonwebtoken/jjwt-jackson -->
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-jackson</artifactId>
            <version>0.12.6</version>
            <scope>runtime</scope>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.glassfish.main.common/glassfish-api -->
        <dependency>
            <groupId>org.glassfish.main.common</groupId>
            <artifactId>glassfish-api</artifactId>
            <version>8.0.0-JDK17-M6</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.openjfx/javafx-swing -->
        <dependency>
            <groupId>org.openjfx</groupId>
            <artifactId>javafx-swing</artifactId>
            <version>23-ea+22</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.json/json -->
        <dependency>
            <groupId>org.json</groupId>
            <artifactId>json</artifactId>
            <version>20240303</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-core -->
        <dependency>
            <groupId>org.apache.logging.log4j</groupId>
            <artifactId>log4j-core</artifactId>
            <version>2.23.1</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.bouncycastle/bcprov-jdk18on -->
        <dependency>
            <groupId>org.bouncycastle</groupId>
            <artifactId>bcprov-jdk18on</artifactId>
            <version>1.78.1</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.apache.commons/commons-configuration2 -->
        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-configuration2</artifactId>
            <version>2.8.0</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.apache.commons/commons-collections4 -->
        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-collections4</artifactId>
            <version>4.4</version>
        </dependency>


        <!-- https://mvnrepository.com/artifact/commons-io/commons-io -->
        <dependency>
            <groupId>commons-io</groupId>
            <artifactId>commons-io</artifactId>
            <version>2.16.1</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.apache.commons/commons-digester3 -->
        <dependency>
            <groupId>org.apache.commons</groupId>
            <!--<artifactId>commons-digester3</artifactId>
            <version>3.2</version>-->
            <artifactId>commons-digester</artifactId>
            <version>2.1</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/commons-configuration/commons-configuration -->
        <dependency>
            <groupId>commons-configuration</groupId>
            <artifactId>commons-configuration</artifactId>
            <version>1.6</version>
        </dependency>




        <!-- https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports -->
        <dependency>
            <groupId>net.sf.jasperreports</groupId>
            <artifactId>jasperreports</artifactId>
            <version>6.21.3</version>
            <!--<version>7.0.0</version>-->
        </dependency>

        <!-- https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports-fonts -->
        <dependency>
            <groupId>net.sf.jasperreports</groupId>
            <artifactId>jasperreports-fonts</artifactId>
            <version>6.21.3</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports-functions -->
        <dependency>
            <groupId>net.sf.jasperreports</groupId>
            <artifactId>jasperreports-functions</artifactId>
            <version>6.21.3</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/net.sf.jasperreports/jasperreports-metadata -->
        <dependency>
            <groupId>net.sf.jasperreports</groupId>
            <artifactId>jasperreports-metadata</artifactId>
            <version>6.21.3</version>
        </dependency>


        <!-- https://mvnrepository.com/artifact/org.hibernate.orm/hibernate-core -->
        <dependency>
            <groupId>org.hibernate.orm</groupId>
            <artifactId>hibernate-core</artifactId>
            <version>6.5.2.Final</version>
        </dependency>


        <!-- https://mvnrepository.com/artifact/com.jcraft/jsch -->
        <dependency>
            <groupId>com.jcraft</groupId>
            <artifactId>jsch</artifactId>
            <version>0.1.55</version>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-security</artifactId>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.springframework.security/spring-security-core -->
        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-core</artifactId>
            <version>6.3.0</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.springframework.security/spring-security-web -->
        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-web</artifactId>
            <version>6.3.0</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.springframework.security/spring-security-config -->
        <dependency>
            <groupId>org.springframework.security</groupId>
            <artifactId>spring-security-config</artifactId>
            <version>6.3.0</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/org.apache.pdfbox/pdfbox -->
        <dependency>
            <groupId>org.apache.pdfbox</groupId>
            <artifactId>pdfbox</artifactId>
            <version>2.0.29</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/com.github.librepdf/openpdf -->
        <dependency>
            <groupId>com.github.librepdf</groupId>
            <artifactId>openpdf</artifactId>
            <version>2.0.3</version>
        </dependency>

        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <version>1.18.34</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/com.ibm.icu/com.ibm.icu -->
        <dependency>
            <groupId>com.ibm.icu</groupId>
            <artifactId>com.ibm.icu</artifactId>
            <version>3.8.1-20081006</version>
        </dependency>

        <!-- https://mvnrepository.com/artifact/com.ibm.icu/icu4j -->
        <dependency>
            <groupId>com.ibm.icu</groupId>
            <artifactId>icu4j</artifactId>
            <version>75.1</version>
        </dependency>


    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <version>3.3.1</version>
            </plugin>
        </plugins>
    </build>

</project>


I still dont understand what is issue of downloading or resolving dependency help me to get resolve this error.
