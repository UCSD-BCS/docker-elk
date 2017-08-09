# https://github.com/elastic/logstash-docker
FROM docker.elastic.co/logstash/logstash:5.5.1
COPY ./config/logstash.yml /usr/share/logstash/config/logstash.yml
COPY ./pipeline/ /usr/share/logstash/pipeline
EXPOSE 5000

# Add your logstash plugins setup here
# Example: RUN logstash-plugin install logstash-filter-json
