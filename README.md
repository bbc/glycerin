glycerin
========

A Java HTTP client for Nitro

Usage
-----

1. Add a maven dependency:
```xml
       <dependency>
          <groupId>com.metabroadcast.atlas.glycerin</groupId>
          <artifactId>glycerin</artifactId>
          <version>0.1.11</version>
      </dependency>
      ```
You'll need the MetaBroadcast repository: `http://mvn.metabroadcast.com/all`

1. Create a Glycerin instance: 
```java
Glycerin glycerin = XmlGlycerin.builder(apiKey);
```

1. Execute a query: 
```java
GlycerinResponse<Broadcast> broadcasts = glycerin.execute(BroadcastQuery.builder() .withDescendantsOf("b039gr8y").build());
```

Compiling
---------

Glycerin is built with [gradle](http://gradle.org "Gradle"). In the glycerin directory:

* `gradle compileJava` will generate and compile glycerin.
* `gradle install` will install maven artifacts into a local mvn repo.

Code is generated from:

* the XML schema via XJC. The bindings are regenerated using the `generateXmlSource` task from the `nitro-schema.xsd`.  
* From the API description using the query generator in the _src/queries/java_ package. The query sources are generated using the `generateQueries` task using `api.xml`. The description can be updated via the `fetchApiDescription` task with an API key.

Schema Updates
--------------

When you need to update to newer versions

 * The XSD schema can be found under `/nitro/api/schema`; fetch the new one into `nitro-schema.xsd`
 * The api query schema can be under `/nitro/api`; fetch the new one into `api.xml`

You can to this automatically by running:
```
gradle fetchApiDescription -Dnitro.apikey=<YOUR_API_KEY>
```
