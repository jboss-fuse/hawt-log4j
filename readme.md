Hawt Log4j
==========

This module contains a log4j PatternLayout that can sanitize the message of a log event before formating it so that you avoid attackers from [forging malicious log entries](https://cwe.mitre.org/data/definitions/117.html).

Example usage (in a log4j.properties file):

    log4j.appender.out.layout=org.jboss.hawt.log4j.SanitizingPatternLayout
    log4j.appender.out.layout.ConversionPattern=%p | %m%n
    log4j.appender.out.layout.replaceRegex=\\n
    log4j.appender.out.layout.replacement=--NL--
    log4j.appender.out.layout.trim=true

The `org.jboss.hawt.log4j.SanitizingPatternLayout` layout supports all the properties the standard log4j `PatternLayout` supports plus the following:

| Property Name | Description |
|---------------|-------------|
| trim | Should the message be trimmed first. Handy for remvoing leading/trailling whitespace |
| replaceRegex | A regular expression that will be replaced |
| replacement | The replacement that will be used |

