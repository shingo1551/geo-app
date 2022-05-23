# ArangoDB

## docker

    docker pull --platform linux/x86_64 arangodb:3.8.6
    docker run -e ARANGO_ROOT_PASSWORD=pa55w0rd --platform linux/x86_64 -p 8529:8529 -d --name arangodb arangodb:3.8.6
