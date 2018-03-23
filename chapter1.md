# Pre

1. create - mysql mot settings table
2. create - mysql mot job table
3. create - mongo cron table
4. 使用者預先設定 cron time
5. 使用者在 portal 預先設定 MOT day, topic, message
6. backend-api-mibo-store 在 server start 的時候載入 cron time \(like: 0 0 12 \* \* \*\)

# Cron

1. 讀取 MOT setting \(like: Day1 show 'Welcome'\)
2. 確認 Mibo create date, 得到符合的 Mibo
3. 寫入 MOT job history table - status = init
4. call GRPC - MQTT \(mqtt topic: mibo/v1/{miboId}/server/events/mot\)
   ```
   mqtt received: {"header":{"mId":"JasondeMacBook-Pro-2.local:192.168.102.52:3c50f83c","timestamp":"1521686480691"},"body":{"topic":"welcome","message":"welcome message"}}
   ```
5. 更新 MOT job history table - status = finish



