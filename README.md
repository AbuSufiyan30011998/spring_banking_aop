# Banking Payment AOP — Spring Boot Real-Time Practice Project

## Technologies
- Java 17
- Spring Boot 3.3.x
- Spring Web
- Spring Data JPA / Hibernate
- MySQL
- Spring AOP
- Bean Validation
- Maven

## What this project demonstrates
1. REST API
2. Service and repository layers
3. JPA entities
4. MySQL persistence
5. @Transactional
6. @Before / @After / @AfterThrowing
7. @Around
8. ProceedingJoinPoint
9. Custom @Audit annotation
10. Global exception handling
11. Performance monitoring
12. Banking money-transfer use case

## Database
Create MySQL database if desired:
CREATE DATABASE banking_db;

Update username/password in application.properties.

## Run
mvn spring-boot:run

The application starts on:
http://localhost:8080

## APIs

GET accounts:
GET http://localhost:8080/api/accounts

GET one account:
GET http://localhost:8080/api/accounts/100001

Transfer:
POST http://localhost:8080/api/payments/transfer

Body:
{
  "fromAccount": "100001",
  "toAccount": "100002",
  "amount": 5000
}

Expected response:
{
  "transactionId": 1,
  "status": "SUCCESS",
  "message": "Money transferred successfully"
}

## AOP flow

HTTP request
 -> Controller
 -> Spring AOP proxy
 -> Logging/Performance/Audit advice
 -> @Transactional service
 -> Repository
 -> MySQL

## Interview explanation

"I worked on a banking payment service where customers could transfer money between accounts. I used Spring Boot, REST, JPA and MySQL. Spring AOP was used to keep cross-cutting concerns separate from business logic. I implemented logging with @Before/@After, performance monitoring with @Around and a custom @Audit annotation for transaction auditing. The transfer operation used @Transactional so the debit, credit and transaction record were handled as one database transaction."

## Important interview points
- Spring AOP is proxy-based.
- @Around uses ProceedingJoinPoint.
- proceed() invokes the target method.
- Self-invocation can bypass the Spring proxy.
- @Transactional is commonly implemented using Spring's proxy/interception infrastructure.
- Avoid putting business logic inside aspects.
- In production, use a proper logging framework such as SLF4J/Logback instead of System.out.println.
