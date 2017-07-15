# fluentd/Dockerfile
FROM fluent/fluentd:${fluentd.version}

LABEL "com.jeecookbook.elkf4dev-fluentd.description"="${project.description}"
LABEL "com.jeecookbook.elkf4dev-fluentd.version"="${fluentd.version}"

RUN ["gem", "install", "fluent-plugin-elasticsearch", "--no-rdoc", "--no-ri", "--version", "1.9.3"]