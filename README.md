Build Images 
-------------
docker build -t client -f Dockerfile-client .
docker build -t grpc_server -f Dockerfile-server .

Run server
-----------
docker run -d --name grpc_server --network grpc_network -p 50051:50051 grpc_server:latest

Run client
----------
docker run -it --name client --network grpc_network --env "GREETER_ENDPOINT=grpc_server:50051" client ./client -name Alice