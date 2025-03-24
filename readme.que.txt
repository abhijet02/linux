--------------------------------------
--------------------------------------
--------------------------------------

log view :  

kill $(cat ./bin/shutdown-logview.pid)
nohup java -jar -Dspring.config.location=logview.properties log-view-deploy-1.0.4.jar >> logs/logview.logs 2>&1 &

--------------
--------------

consumer :
nohup java -jar -Dspring.config.location=consumer.properties consumer-deploy-1.0.1.jar >> logs/consumer.logs 2>&1 &


curl -X POST "http://10.140.0.237:8022/cloud-stream-consumer/shutdown" -H "accept: */*"




nohup java -jar -Dspring.config.location=consumer.properties -Dspring.application.name=app2 -Dserver.port=8022 -Dspring.cloud.stream.bindings.transmitConsumer-in-0.consumer.concurrency=2 consumer-deploy-1.0.1.jar >> logs/consumer2.logs 2>&1 &

---------------
--------------

producer :

kill $(cat ./bin/shutdown-producer.pid)

nohup java -jar -Dspring.config.location=producer.properties producer-deploy-1.0.4.jar >> logs/producer.logs 2>&1 &


--------------
--------------
rabitmq

systemctl restart rabbitmq-server


rabbitmq-plugins status rabbitmq_management
rabbitmq-plugins restart rabbitmq_management
rabbitmq-plugins enable rabbitmq_management
rabbitmqctl add_user admin Y8SbiTSNUaiMe0k
rabbitmqctl set_user_tags admin administrator
rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"

-----------------------------------
-----------------------------------

http://10.42.53.152:2032/cloud-stream-logview/status-summary
admin a
amin123

http://10.42.53.152:15672/#/queues

10.140.0.101 27017
10.140.0.101 2032
10.140.0.236 9099
10.140.0.134 15672


