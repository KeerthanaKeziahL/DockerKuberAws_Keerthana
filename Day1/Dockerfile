FROM eclipse-temurin:23-jdk AS builder

WORKDIR /app

COPY .mvn/ .mvn
COPY mvnw pom.xml ./

RUN ./mvnw dependency:go-offline

COPY src ./src

RUN ./mvnw clean package -DskipTests

FROM eclipse-temurin:23-jdk

WORKDIR /app

COPY --from=builder /app/target/customer-service-0.0.1-SNAPSHOT.war app.war


EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.war"]

