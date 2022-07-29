# Simple Spring Boot Application
This is a simple sprint boot application for the backend interview project. The project uses [Spring Initializer](https://start.spring.io/#!type=maven-project&language=java&platformVersion=2.7.2&packaging=jar&jvmVersion=11&groupId=com.example&artifactId=demo&name=demo&description=Demo%20project%20for%20Spring%20Boot&packageName=com.example.demo&dependencies=data-rest,data-jpa,h2) with

- Java 11
- Spring Data JPA
- Spring Data REST
- H2 Database

The project provides an HATEAOS implementation for a People lookup service.
The project is the same as the guide at https://spring.io/guides/gs/accessing-data-rest/
## Build and Run
Steps to build the project
1. Import the project into IntelliJ selecting the defaults (Maven project)
2. Build the project in IntelliJ

Steps to run the project
1. Click on the Run button in IntelliJ and wait ...

Eventually you will see the Spring boot logo in the console

## Test
- To verify the REST API is available use
`curl http://localhost:8080`. You will see an response similar to the one below
```
{
  "_links" : {
    "people" : {
      "href" : "http://localhost:8080/people{?page,size,sort}",
      "templated" : true
    },
    "profile" : {
      "href" : "http://localhost:8080/profile"
    }
  }
}
```
- To add a person use 
  ```
  curl -i -H "Content-Type:application/json" -d '{"firstName": "Frodo", "lastName": "Baggins"}' http://localhost:8080/people
  ```
- To list people use
```
curl http://localhost:8080/people
```
- To find a person by last name use
```
curl http://localhost:8080/people/search/findByLastName?name=Baggins
```

## Database SQL
To connect to the database to run SQL, use the embedded SQL UI at http://localhost:8080/h2-console

The JDBC URL can be retrieved from the logs. Review the app startup logs for a line similar to the one below
```
2022-07-29 08:19:39.369  INFO 32659 --- [           main] o.s.b.a.h2.H2ConsoleAutoConfiguration    : H2 console available at '/h2-console'. Database available at 'jdbc:h2:mem:7020c287-ff87-47c6-ac88-0b497938691b'
```
In the log example above, the JDBC URL is `jdbc:h2:mem:7020c287-ff87-47c6-ac88-0b497938691b`