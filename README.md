Maven Packaging for [Windows Service Wrapper](https://github.com/winsw/winsw)
===========================================

[![Join the chat at https://gitter.im/winsw/winsw](https://badges.gitter.im/winsw/winsw.svg)](https://gitter.im/winsw/winsw?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Changelog](https://img.shields.io/github/release/jenkinsci/winsw-maven-packaging.svg?label=changelog)](https://github.com/jenkinsci/winsw-maven-packaging/releases/latest)

This repository represents the legacy packaging of [Windows Service Wrapper](https://github.com/winsw/winsw) as a Maven artifact
which is hosted in the [Jenkins Artifactory](https://repo.jenkins-ci.org/webapp/#/artifacts/browse/tree/General/releases/com/sun/winsw/winsw).
New versions of the project use GitHub Releases and NuGet, but some Pipelines including Jenkins still use Maven as a download source.

New releases of the Maven packaging will be performed upon request.

## Usage

Maven Dependency Plugin can be used to access the executable in the Maven projects.
Exampe for adding the executable as resource to another JAR file.

```xml
  <build>
    <plugins>
      <plugin>
        <artifactId>maven-dependency-plugin</artifactId>
        <executions>
          <execution>
            <id>winsw</id>
            <phase>generate-resources</phase>
            <goals>
              <goal>copy</goal>
            </goals>
            <configuration>
              <artifactItems>
                <artifactItem>
                  <groupId>com.sun.winsw</groupId>
                  <artifactId>winsw</artifactId>
                  <version>${winsw.version}</version>
                  <classifier>bin</classifier>
                  <type>exe</type>
                  <outputDirectory>${project.build.outputDirectory}/org/jenkinsci/modules/windows_agent_installer</outputDirectory>
                  <destFileName>jenkins-agent.exe</destFileName>
                </artifactItem>
              </artifactItems>
            </configuration>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
```

## Release notes

See [GitHub Releases](https://github.com/jenkinsci/winsw-maven-packaging/releases).
