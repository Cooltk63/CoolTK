name=LoggingConfig
appender.console.type=Console
appender.console.name=ConsoleAppender
appender.console.layout.type=PatternLayout
appender.console.layout.pattern=%d{HH:mm:ss.SSS} [%t] %-5level %logger{36} - %msg%n

logger.security.name=com.crs.SsoLoginService.Security
logger.security.level=DEBUG
logger.security.additivity=false
logger.security.appenderRef.console.ref=ConsoleAppender

rootLogger.level=INFO
rootLogger.appenderRefs=console
rootLogger.appenderRef.console.ref=ConsoleAppender