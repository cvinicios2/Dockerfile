FROM store/oracle/serverjre:8

ENV ES_PKG_NAME elasticsearch-1.5.0

RUN yum install wget build-essential gcc make apt-get -y
run apt-get update


# Install Elasticsearch.
run wget https://download.elastic.co/elasticsearch/release/org/elasticsearch/distribution/deb/elasticsearch/2.3.1/elasticsearch-2.3.1.deb
run dpkg -i elasticsearch-2.3.1.deb
RUN systemctl enable elasticsearch.service


ADD config.yml /etc/elasticsearch/elasticsearch.yml

RUN /bin/systemctl enable elasticsearch.service


# Mount elasticsearch.yml config
ADD elasticsearch.yml /elasticsearch/config/elasticsearch.yml

# Define working directory.
WORKDIR /data


CMD ["elasticsearch"]

# Expose ports.
#   - 9200: HTTP
#   - 9300: transport
EXPOSE 9200
EXPOSE 9300
