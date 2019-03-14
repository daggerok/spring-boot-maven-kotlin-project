# spring-boot-maven-kotlin-project
spring-boot maven kotlin starter project

1) create kotlin project via IDEA or start.spring.io

2) update in generated pom.xml `maven-compiler-plugin` and `maven-kotlin-plugin` like so:

```xml
<project>
  <!-- ... -->
  <properties>
    <java.version>1.8</java.version>
  </properties>
  <!-- ... -->
  <build>
    <plugins>
      <plugin>
        <groupId>org.jetbrains.kotlin</groupId>
        <artifactId>kotlin-maven-plugin</artifactId>
        <configuration>
          <jvmTarget>${java.version}</jvmTarget>
          <args>
            <arg>-Xjsr305=strict</arg>
          </args>
          <compilerPlugins>
            <plugin>spring</plugin>
          </compilerPlugins>
        </configuration>
        <executions>
          <execution>
            <id>compile</id>
            <goals>
              <goal>compile</goal>
            </goals>
            <configuration>
              <sourceDirs>
                <sourceDir>${project.basedir}/src/main/kotlin</sourceDir>
                <sourceDir>${project.basedir}/src/main/java</sourceDir>
              </sourceDirs>
            </configuration>
          </execution>
          <execution>
            <id>test-compile</id>
            <goals>
              <goal>test-compile</goal>
            </goals>
            <configuration>
              <sourceDirs>
                <sourceDir>${project.basedir}/src/test/kotlin</sourceDir>
                <sourceDir>${project.basedir}/src/test/java</sourceDir>
              </sourceDirs>
            </configuration>
          </execution>
        </executions>
        <dependencies>
          <dependency>
            <groupId>org.jetbrains.kotlin</groupId>
            <artifactId>kotlin-maven-allopen</artifactId>
            <version>${kotlin.version}</version>
          </dependency>
        </dependencies>
      </plugin>

      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.8.0</version>
        <executions>
          <execution>
            <id>default-compile</id>
            <phase>none</phase>
          </execution>
          <execution>
            <id>default-testCompile</id>
            <phase>none</phase>
          </execution>
          <execution>
            <id>java-compile</id>
            <phase>compile</phase>
            <goals>
              <goal>compile</goal>
            </goals>
          </execution>
          <execution>
            <id>java-test-compile</id>
            <phase>test-compile</phase>
            <goals>
              <goal>testCompile</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <!-- ... -->
    </plugins>
  </build>
</project>
```
