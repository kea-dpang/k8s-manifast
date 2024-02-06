### logstash-config.yaml 생성
```
cd ./k8s-manifast/elasticsearch/logstash
touch logstash-config.yaml
```

### logstash-config.yaml 작성
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: logstash-config
data:
  logstash.yml: |
    http.host: "0.0.0.0"
    path.config: /usr/share/logstash/pipeline
  logstash.conf: |
    input {
      jdbc {
        jdbc_driver_library => "/usr/share/logstash/logstash-core/lib/jars/mysql-connector-java.jar"
        jdbc_driver_class => "com.mysql.cj.jdbc.Driver"
        jdbc_connection_string => "jdbc:mysql://[your-database-endpoint]/[your-database-name]"
        jdbc_user => "[your-database-user]"
        jdbc_password => "[your-database-password]"
        statement => "
          SELECT *
          FROM [your-table-name]
        "
        schedule => "* * * * *"
        type => "[your-type]"
        add_field => { "[@metadata][document_id]" => "%{[your-field-name]}" }
      }
    }

    output {
      elasticsearch {
        hosts => ["http://elasticsearch:9200"]
        index => "%{type}"
        document_id => "%{[@metadata][document_id]}"
      }
    }
```

### 참고
```
[your-database-endpoint], [your-database-name], [your-database-user], [your-database-password], [your-table-name], [your-type], [your-field-name] 는 실제 값으로 대체
```
