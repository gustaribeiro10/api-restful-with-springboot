Products API – Spring Boot + PostgreSQL

A simple REST API for creating, retrieving, updating, and deleting products, built with Spring Boot 3, Spring Data JPA, Hibernate, Bean Validation, HATEOAS, and PostgreSQL.

✨ Features

Verb

Endpoint

Description

POST

/products

Registers a new product.

GET

/products

Lists all products with HATEOAS links.

GET

/products/{id}

Retrieves a product by UUID.

PUT

/products/{id}

Updates the name and price of an existing product.

DELETE

/products/{id}

Removes a product.

Each response includes HATEOAS links that make resource navigation easier.

🚀 Running locally

Prerequisites

Java 17+ (JDK)

Maven 3.9+ or Gradle (Maven is used by default)

PostgreSQL 14+ running on localhost:5432, database products-api

Steps

Clone the repository:

git clone https://github.com/YOUR_USER/products-api.git
cd products-api

Set up the database (if needed):

CREATE DATABASE "products-api";
-- default user "postgres"/"1234" can be changed in application.properties

Build & run:

./mvnw spring-boot:run
# or
mvn clean package && java -jar target/springboot-*.jar

The application starts at http://localhost:8080.

⚙️ Main dependencies

spring‑boot‑starter‑web – REST layer

spring‑boot‑starter‑data‑jpa – JPA/Hibernate integration

spring‑boot‑starter‑validation – Jakarta Bean Validation

spring‑boot‑starter‑hateoas – HATEOAS links

postgresql – JDBC driver

Versions are managed by the Spring Boot BOM and can be found in pom.xml.

🔍 Implementation details

UUID as primary key ensures distributed uniqueness.

BeanUtils.copyProperties copies data from DTO to entity.

@Valid on endpoints triggers validation declared in ProductRecordDto.

HATEOAS: each loaded product receives a self link, and the item endpoint adds a link back to the list.

DDL‑auto update: Hibernate automatically creates/updates the TB_PRODUCTS table.
