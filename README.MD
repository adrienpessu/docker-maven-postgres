# docker-maven-postgres

Simple docker image to execute integration test or BDD in your favorite CI

## Bitbucket pipeline

To test the image in local run : 

``docker run -it --volume=/Users/adrien/workspaces/kconnect/app-service:/localDebugRepo --workdir="/localDebugRepo" --memory=4g --entrypoint=/bin/bash adrienpessu/docker-maven-postgres ``