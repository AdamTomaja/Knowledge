# Quickly generate new Java Maven Project
```bash
mvn archetype:generate -DgroupId=your.package -DartifactId=projectArtifactId -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

```

# How do I configure maven to compile in Java 8 version
```xml
<project>
    <build>
        <plugins>
            <plugin>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.3</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

# Deploy to remote Tomcat server
## Configure plugin
```xml
<project>
    <build>
		<plugins>
			<plugin>
				<groupId>org.apache.tomcat.maven</groupId>
				<artifactId>tomcat7-maven-plugin</artifactId>
				<version>2.2</version>
				<configuration>
					<url>http://yourserver:8083/manager/text</url>
					<server>serverName</server>
					<path>/appname</path>
				</configuration>
			</plugin>
		</plugins>
	</build>
</project>
```
## Configure manager username and password in external file
```bash
vi C:\Users\Adam\.m2\settings.xml
```

```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                          http://maven.apache.org/xsd/settings-1.0.0.xsd">
<servers>
      <server>
        <id>serverName</id>
        <username>admin</username>
        <password>yourpassword</password>
      </server>
	</servers>
</settings>
```
* Now You can execute 
```bash
mvn tomcat7:deploy
``` 
