# elkf4dev

[![Travis CI](https://travis-ci.org/olivier-schmitt/elkf4dev.svg?branch=master)](https://travis-ci.org/olivier-schmitt/elkf4dev)
[![Docker Repository on Quay](https://quay.io/repository/olivier_schmitt/elkf4dev-fluentd/status "Docker Repository on Quay")](https://quay.io/repository/olivier_schmitt/elkf4dev-fluentd)

This project offers a local ELK FluentD stack for developers.

Docker Compose is used to build a simple logging stack:

```yaml
version: '2'
services:
  fluentd:
    image: quay.io/olivier_schmitt/elkf4dev-fluentd:latest
    volumes:
      - ${PWD}/conf/fluentd.conf:/fluentd/etc/fluent.conf
    links:
      - "elasticsearch"
    ports:
      - "24224:24224"
      - "24224:24224/udp"

    depends_on:
      - elasticsearch

  elasticsearch:
    image: elasticsearch
    expose:
      - 9200
    ports:
      - "9200:9200"

  kibana:
    image: kibana
    links:
      - "elasticsearch"
    ports:
      - "5601:5601"
    depends_on:
      - elasticsearch
```

Check the following folder to get the needed files: https://github.com/olivier-schmitt/elkf4dev/tree/master/elkf4dev-stack/src/main/resources

Download conf folder and docker-compose.yml, then run command "docker-compose up" to launch the stack.

Every container should run with the option --log-driver=fluentd in order to push logs to the stack.

Check Docker documentation about logging with Fluentd : https://docs.docker.com/engine/admin/logging/fluentd/
