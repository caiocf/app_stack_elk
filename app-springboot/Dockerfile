# Etapa 1: Construção da aplicação (imagem Maven)
FROM maven:3.8.4-openjdk-17-slim AS builder
WORKDIR /app

# primeiro copia pom.xml e baixa as dependências
COPY pom.xml .
RUN --mount=type=cache,target=/root/.m2 mvn dependency:go-offline

# depois copia o restante dos arquivos
COPY src ./src
RUN mvn clean package -DskipTests

# Etapa 2: Imagem final para rodar a aplicação (imagem JDK leve)
FROM azul/zulu-openjdk-alpine:17

WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080

# Comando para executar a aplicação
ENTRYPOINT ["java", "-jar", "/app/app.jar"]