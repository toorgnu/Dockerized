# Build the docker image 

docker build -t torproxy:00 .


# Run the docker images

docker run -ti -p 127.0.0.1:9050:9050  --name torproxy00 -v "$(pwd)/torrc-config/torrc:/etc/tor/torrc" torproxy:00
