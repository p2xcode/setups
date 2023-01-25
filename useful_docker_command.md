Remove dangling images
docker rmi -f $(docker images -f "dangling=true" -q)

Remove exitted containers
docker rm $(docker ps -a -f status=exited -f status=created -q)

Build an image from a Dockerfile in current dir and give it a name
docker build -t image_name .


Run a container with a name
docker container run -it --rm --name ubuntu ubuntu /bin/bash

Attach to running container and run bash
docker exec -i -t my_httpd /bin/bash

Test