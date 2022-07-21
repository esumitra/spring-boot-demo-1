# Simple Spring Boot Application
This is a simple sprint boot application for the backend interview project. The project uses

- Java 11
- JPA
- Spring Data REST
- H2 Database

The project provides a complete HATEAOS implementation for a People lookup service.
The project is the same as the guide at https://spring.io/guides/gs/accessing-data-rest/
## Build and Run
Steps to build the project
1. Import the project into IntelliJ selecting the defaults (Maven project)
2. Build the project in IntelliJ

Steps to run the project
1. Click on the Run button and wait ...

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
