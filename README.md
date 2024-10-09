### 1) How to Build Images

To build the client and server images, run the following commands:

```bash
# Build client image
docker build -t netcat-client -f Dockerfile-client .

# Build server image
docker build -t netcat-server -f Dockerfile-server .


To create a non-default bridge network, use the following command:
docker network create my-bridge-network

# Run the server container
docker run --rm --name netcat-server --network my-bridge-network netcat-server

# In a separate terminal, run the client container
docker run --rm --name netcat-client --network my-bridge-network -e SERVER_IP=netcat-server netcat-client
