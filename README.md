# FIAP Coworking — Reservas de Salas & Recursos

Stack: Java 21, Spring Boot 3.3.x, Thymeleaf, Spring Data JPA, Flyway, PostgreSQL, OAuth2 (Google), Docker Compose, Bootstrap 5.

## Rodar em DEV
1. `docker compose up -d db`
2. Exportar OAuth:
   - `OAUTH_GOOGLE_ID=...`
   - `OAUTH_GOOGLE_SECRET=...`
3. `mvn clean package -DskipTests`
4. `java -jar target/coworking-reservas-0.0.1.jar --spring.profiles.active=dev`

## Docker (app + db)
```bash
mvn clean package -DskipTests
docker compose up --build
```

Rotas: `/`, `/reservas`, `/salas`, `/recursos` • Login: `/oauth2/authorization/google`

### Regras
- Sem sobreposição de reservas na mesma sala
- Duração máxima 8h
- Recursos só quando ativos
