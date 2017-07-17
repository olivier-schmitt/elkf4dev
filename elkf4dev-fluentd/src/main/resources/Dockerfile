# fluentd/Dockerfile
FROM fluent/fluentd:${fluentd.version}

LABEL "com.jeecookbook.elkf4dev-fluentd.description"="${project.description}"
LABEL "com.jeecookbook.elkf4dev-fluentd.version"="${fluentd.version}"
LABEL "com.jeecookbook.elkf4dev-fluentd.flavor"="Alpine Linux"

RUN apk add --update --virtual .build-deps \
        sudo build-base ruby-dev \
 && sudo gem install \
        fluent-plugin-elasticsearch \
 && sudo gem sources --clear-all \
 && apk del .build-deps \
 && rm -rf /var/cache/apk/* \
           /home/fluent/.gem/ruby/2.3.0/cache/*.gem
