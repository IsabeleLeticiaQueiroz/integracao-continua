# usa imagem maven para compartilhar projeto
FROM maven:3.9.9-eclipse-temurin-21 AS build 

# define a pasta de trabalho dentro do container
WORKDIR /app

# como estamos na raiz do projeto, fazemos um ponto daqui para o ponto definido que é /app do container
# copia todo o codigo pra dentro do container
COPY . .

# compila e gera o JAR (PULA TESTES)
RUN mvn clean package -DskipTests

# Apenas o java runtime
FROM eclipse-temurin:21-jre

# define pasta de trabaalho dentro do container
WORKDIR /app

# copia o jar na etapa anterior
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT [ "java", "-jar", "app.jar"]
