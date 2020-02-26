# maven-test

## How this project was created

```
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```

## Building the project

```
mvn package
```

## Running the project

```
java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App
```

## Publishing the project

Added following element to end of `pom.xml` file:

```xml
  <distributionManagement>
    <repository>
      <id>github</id>
      <name>GitHub OWNER Apache Maven Packages</name>
      <url>https://maven.pkg.github.com/jcansdale-test/maven-test</url>
    </repository>
  </distributionManagement>
```

Create or update the file at `~/.m2/settings.xml`:

```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">

  <activeProfiles>
    <activeProfile>github</activeProfile>
  </activeProfiles>

  <profiles>
    <profile>
      <id>github</id>
      <repositories>
        <repository>
          <id>github</id>
          <name>GitHub OWNER Apache Maven Packages</name>
          <url>https://maven.pkg.github.com/jcansdale-test/maven-test</url>
        </repository>
      </repositories>
    </profile>
  </profiles>

  <servers>
    <server>
      <id>github</id>
      <username>jcansdale-test</username>
      <password>GITHUB_TOKEN</password>
    </server>
  </servers>
</settings>
```

Publish the package:

```
mvn deploy
```

## References

- Maven in 5 Minutes
https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html

- Configuring Apache Maven for use with GitHub Packages
https://help.github.com/en/packages/using-github-packages-with-your-projects-ecosystem/configuring-apache-maven-for-use-with-github-packages