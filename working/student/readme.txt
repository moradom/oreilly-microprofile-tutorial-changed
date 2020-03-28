

setjdk.bat

cd student

-- dev mode

mvnw quarkus:dev

-- package the jar

mvnw quarkus:package

-- run from jar

java -jar target\student-1.0-SNAPSHOT-runner.jar

-- build on docker (it was required to add 4 GB of RAM to Docker) (fails but creates the binary for Linux)

mvnw package -Pnative -Dquarkus.native.container-build=true

mvnw package -Pnative -Dquarkus.native.container-runtime=docker

-- make docker image

-- bigger image 164 MB

docker build -f src/main/docker/Dockerfile.native -t quarkus-quickstart/getting-started .

-- smaller 44 MB

docker build -f src/main/docker/Dockerfile.native2 -t quarkus-quickstart/getting-started .

-- run docker

docker run -i --rm -p 8080:8080 quarkus-quickstart/getting-started
