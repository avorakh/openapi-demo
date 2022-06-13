1. ReadyAPI run server
2. Run NGROK to have external DNS:
ngrok http 8088
3. Edit "UsersMock+ngrok.postman_environment.json file" to use NGROK DNS
4. Run newman: 
# only CLI report 
docker run -v "$(pwd)":/etc/newman  -t postman/newman:alpine run  Users_Service_with_FT.postman_collection.json  --environment="UsersMock+ngrok.postman_environment.json"

#  CLI + htmlextra report
docker run -t -v $(pwd):/etc/newman dannydainton/htmlextra run Users_Service_with_FT.postman_collection.json  --environment="UsersMock+ngrok.postman_environment.json" -r htmlextra,cli
