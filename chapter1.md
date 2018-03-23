# Pre

1. create - mysql mot settings table
2. create - mysql mot job table
3. create - mongo cron table
4. user pre-define MOT day, topic, message

# Cron

1. backend-api-mibo-store load cron job when server start \(like: 0 0 12 \* \* \*\)
2. read MOT setting \(like: Day1 show 'Welcome'\)
3. check Mibo create date, get matched Mibo
4. insert MOT job - status = init
5. call GRPC - MQTT \(mqtt topic: mibo/v1/{miboId}/server/events/mot\)
   1. mqtt received: {"header":{"mId":"JasondeMacBook-Pro-2.local:192.168.102.52:3c50f83c","timestamp":"1521686480691"},"body":{"topic":"welcome","message":"welcome message"}}
6. update MOT job - status = finish



