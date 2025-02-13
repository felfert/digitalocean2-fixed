[![CI](https://github.com/felfert/digitalocean2-fixed/actions/workflows/ci.yaml/badge.svg)](https://github.com/felfert/digitalocean2-fixed/actions/workflows/ci.yaml)

## What is this?
A backported fix for version 2.5.0 of the digitalocean2 provider of apache jclouds.
The original PR is here https://github.com/apache/jclouds/pull/216

If you still use apache-jclouds 2.5.0, to use this fixed version in your maven projects,
modify your project's pom.xml like this:

#### Before
```xml
    <dependency>
      <groupId>org.apache.jclouds</groupId>
      <artifactId>jclouds-allcompute</artifactId>
      <version>2.5.0</version>
    </dependency>
```
#### After
```xml
    <dependency>
      <groupId>org.apache.jclouds</groupId>
      <artifactId>jclouds-allcompute</artifactId>
      <version>2.5.0</version>
      <exclusions>
        <!-- exclude broken digitalocean2 ... -->
        <exclusion>
          <groupId>org.apache.jclouds.provider</groupId>
          <artifactId>digitalocean2</artifactId>
        </exclusion>
      </exclusions>
    </dependency>
    <!-- ... and use the backported fix instead -->
    <dependency>
      <groupId>com.github.felfert</groupId>
      <artifactId>digitalocean2-fixed</artifactId>
      <version>2.5.1</version>
    </dependency>
```
