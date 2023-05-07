### Maven project
- https://openjfx.io/openjfx-docs/#maven
- Add dependecy (libs): Refer pom.xml
- Config to build exe

  - javafx-maven-plugin, jpackage-maven-plugin -> to build exe
  - Guide link: https://dev.to/cherrychain/javafx-jlink-and-jpackage-h9

- Command
```cmd
mvn clean compile javafx:jlink jpackage:jpackage
```
- Output folder: /target/dist (refer to img below)

- Config to build jar 

```xml
 <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-shade-plugin</artifactId>
    <executions>
        <execution>
            <goals>
                <goal>shade</goal>
            </goals>
            <configuration>
                <shadedArtifactAttached>true</shadedArtifactAttached>
                <transformers>
                    <transformer implementation=
                                         "org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                        <mainClass>com.example.demo.HelloApplication</mainClass>
                    </transformer>
                </transformers>
            </configuration>
        </execution>
    </executions>
</plugin>
```

Run jar (-shade file) file  with vm option

```command
--module-path "path\javafx-sdk-11.0.2\lib" --add-modules javafx.controls,javafx.fxml,javafx.base --add-exports javafx.graphics/com.sun.javafx.sg.prism=ALL-UNNAMED
```
### Note

Install WIX Toolset to use jpackage
https://stackoverflow.com/questions/59655362/java-jpackage-native-packaging-wix-tools-not-found-error

Using jdk 14 or 15, 16

![img.png](img.png)

