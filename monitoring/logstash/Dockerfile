# 기반 이미지를 amd64 아키텍처를 위한 Logstash 이미지로 변경합니다.
FROM --platform=linux/amd64 docker.elastic.co/logstash/logstash:7.17.0

# 필요한 파일을 이미지에 추가합니다.
ADD mysql-connector-java-8.3.0.jar /usr/share/logstash/logstash-core/lib/jars/
