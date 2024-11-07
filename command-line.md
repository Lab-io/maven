# command line

- local repository:
    
  ```
  mvn clean compile "-Dmaven.repo.local=..\lib"
  
  or
  
  mvn clean compile quarkus:dev "-Dmaven.repo.local=..\repository"
  
  or
  
  mvn clean -o "-Dmaven.repo.local=..\repository"
  ```

- that copies the project dependencies from the repository to a defined location.
  ```

  mvn clean package "-Dmaven.repo.local=..\repository"

  and

  <build>
      <plugins>
          <plugin>
              <groupId>org.apache.maven.plugins</groupId>
              <artifactId>maven-dependency-plugin</artifactId>
              <executions>
                  <execution>
                      <id>copy-dependencies</id>
                      <phase>package</phase>
                      <goals>
                          <goal>copy-dependencies</goal>
                      </goals>
                      <configuration>
                          <outputDirectory>${project.build.directory}/lib</outputDirectory>
                          <overWriteReleases>false</overWriteReleases>
                          <overWriteSnapshots>false</overWriteSnapshots>
                          <overWriteIfNewer>true</overWriteIfNewer>
                      </configuration>
                  </execution>
              </executions>
          </plugin>
        </plugins>
  </build>
```



