Download the war file from https://structurizr.com/help/on-premises.

DO NOT SHARE structurizr-onpremises-2306.war file as it is licensed. 

Start the server:

```
mkdir /tmp/structurizr
su -c "setenforce 0"
docker run -it --rm -p 8080:8080 -v /home/aliok/Downloads/structurizr-onpremises-2306.war:/usr/local/tomcat/webapps/ROOT.war -v /tmp/structurizr:/usr/local/structurizr tomcat:9.0.38-jdk11-openjdk
```

Create a workspace and get the API key and secret:

- Open http://localhost:8080, username: structurizr, password: password
- Go to http://localhost:8080/dashboard
- Click "Create a new workspace"
- Go to workspace settings: http://localhost:8080/workspace/1/settings
- Copy API key and secret

Configure this Java application by pasting the API key and secret into structurizr.properties.

Finally, run the program, using your IDE or Gradle; for example:

```
./gradlew run
```

Then go to http://localhost:8080/workspace/1 and check the diagram (only 1 at the moment).

For more information, please see [Structurizr for Java - Getting Started](https://github.com/structurizr/java/blob/master/docs/getting-started.md).
