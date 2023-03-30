# Micorservices

## HW-16
### Запуск контейнеров с другим алиасом
docker run -d --network=reddit --network-alias=post_db-1 --network-alias=comment_db-1 mongo:4.2-rc
docker run -d --env="POST_DATABASE_HOST=post_db-1" --network=reddit --network-alias=post-1 nosko/post:1.0 
docker run -d --env="COMMENT_DATABASE_HOST=comment_db-1" --network=reddit --network-alias=comment-1 nosko/comment:1.0 
docker run -d --env="POST_SERVICE_HOST=post-1" --env="COMMENT_SERVICE_HOST=comment-1" --network=reddit -p 9292:9292 nosko/ui:1.0
