# docker-maven-postgres

Simple docker image to execute integration test or BDD in your favorite CI

## Bitbucket pipeline

To test the image in local run : 

``docker run -it --volume=/Users/adrien/workspaces/kconnect/app-service:/localDebugRepo --workdir="/localDebugRepo" --memory=4g --entrypoint=/bin/bash adrienpessu/docker-maven-postgres ``

### bitbucket-pipelines.yml example

```
image: adrienpessu/docker-maven-postgres`
  pipelines:
    default:
      - step:
          script:
            - pg_ctlcluster $PG_MAJOR main start
            - gosu postgres psql -c "CREATE USER ${POSTGRES_USER} WITH PASSWORD '${POSTGRES_PASSWORD}';"
            - gosu postgres psql -c "CREATE DATABASE ${POSTGRES_DB} OWNER ${POSTGRES_USER};"
            - mvn clean -V -B -s settings.xml -Prepo sonar:sonar deploy
```