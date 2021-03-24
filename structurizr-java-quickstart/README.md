# Integration with a local Structurizr server

Download the war file from <https://structurizr.com/help/on-premises>.

DO NOT SHARE `structurizr-onpremises-XXXX.war` file as it is licensed. 

Start the server:

```bash
# tmp directory to store Structurizr server data
STRUCTURIZR_SERVER_DATA_PATH=/tmp/structurizr

# Structurizr WAR file
STRUCTURIZR_WAR_PATH=/path/to/structurizr-onpremises-XXXX.war

mkdir -p STRUCTURIZR_SERVER_DATA_PATH 

docker run -it --rm -p 8080:8080 \ 
    -v ${STRUCTURIZR_WAR_PATH}:/usr/local/tomcat/webapps/ROOT.war \
    -v /tmp/structurizr:/usr/local/structurizr \
     tomcat:9.0.38-jdk11-openjdk
```

Create a workspace and get the API key and secret:

- Open <http://localhost:8080>, username: structurizr, password: password
- Go to <http://localhost:8080/dashboard>
- Click "Create a new workspace"
- Go to workspace settings: <http://localhost:8080/workspace/1/settings>
- Copy API key and secret


Configure this Java application by pasting the API key and secret into `structurizr.properties`.

Finally, run the program, using your IDE or Gradle; for example:

```
./gradlew run
```

Go to <http://localhost:8080/workspace/1> and enjoy nice diagrams! 

# Integration with Structurizr.com

Procedure is pretty much the same with "Integration with a local Structurizr server" above, except you need to get the api key, secret and the workspace id from
Structurizr.com.

Put the API key and secret into `structurizr.properties`.

Replace the `structurizr.api.url` in `structurizr.properties` with `https://api.structurizr.com`.

Replace the workspace id in `Structurizr.java`.


Finally, run the program, using your IDE or Gradle; for example:

```
./gradlew run
```

Go to <https://structurizr.com/dashboard> and enjoy nice diagrams!
