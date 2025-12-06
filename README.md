# EventTickets - Plateforme Microservices

Plateforme de billetterie événementielle basée sur une architecture microservices.

## 🏗️ Architecture

| Service                         | Technologie          | Port | Description                  | Testing/Quality Tools                                          |
| ------------------------------- | -------------------- | ---- | ---------------------------- | -------------------------------------------------------------- |
| `api-gateway`                   | Node.js, Express     | 3000 | Point d'entrée, JWT, routage | Nodemon, Morgan                                                |
| `EventCatalogService`           | Java 17, Spring Boot | 8080 | Catalogue d'événements       | JUnit, Mockito, JaCoCo, Checkstyle, Snyk, Swagger              |
| `TicketInventoryService`        | Java 17, Spring Boot | 8082 | Stocks et réservations       | JUnit, Mockito, JaCoCo, Checkstyle, SonarQube, JMeter, Swagger |
| `paymentAndNotificationService` | PHP 8.2, Laravel     | 8083 | Paiements et notifications   | PHPUnit, Mockery, PHPStan, Larastan, Laravel Pint              |
| `user-service`                  | Node.js, Prisma      | 3001 | Authentification, profils    | Jest, ESLint, Snyk, SonarScanner, Swagger                      |
| `web`                           | React.js, Vite       | 5173 | Frontend                     | ESLint, Vite                                                   |

## 🚀 Démarrage rapide

```bash
# API Gateway (démarrer en premier)
cd api-gateway && npm install && npm run dev

# Event Catalog Service
cd EventCatalogService && mvnw.cmd spring-boot:run

# Ticket Inventory Service
cd TicketInventoryService && mvnw.cmd spring-boot:run

# Payment & Notification Service
cd paymentAndNotificationService && composer install && php artisan serve

# User Service
cd user-service && npm install && npm run dev

# Frontend
cd web && npm install && npm run dev
```

## 🧪 Tests

| Service                       | Commande           |
| ----------------------------- | ------------------ |
| EventCatalogService           | `mvnw.cmd test`    |
| TicketInventoryService        | `mvnw.cmd test`    |
| paymentAndNotificationService | `php artisan test` |

### Couverture de code (JaCoCo)

```bash
cd TicketInventoryService
mvn verify
# Rapport: target/site/jacoco/index.html
```

### Analyse SonarQube

```bash
cd TicketInventoryService
mvn verify sonar:sonar -Psonar -Dsonar.token=YOUR_TOKEN
```

### Tests de charge (JMeter)

```bash
cd TicketInventoryService/jmeter
jmeter -n -t TicketReservationLoadTest.jmx -l results.jtl
```

## 🐳 Docker

```bash
docker-compose up -d
```

## 📁 Structure

```
EventTickets/
├── api-gateway/                 # API Gateway (Node.js)
├── EventCatalogService/         # Catalogue (Spring Boot)
├── TicketInventoryService/      # Inventaire (Spring Boot)
├── paymentAndNotificationService/  # Paiement (Laravel)
├── user-service/                # Utilisateurs (Node.js)
├── web/                         # Frontend (Vue.js)
└── docker-compose.yml
```

## ⚙️ Configuration

Chaque service nécessite un fichier `.env` (voir `.env.example` dans chaque dossier).

| Service      | Variables clés                  |
| ------------ | ------------------------------- |
| api-gateway  | `JWT_SECRET`, URLs des services |
| Spring Boot  | `spring.datasource.*`           |
| Laravel      | `DB_*`, `MAIL_*`, clés paiement |
| user-service | `DATABASE_URL`, `JWT_SECRET`    |
| web          | `VITE_API_BASE_URL`             |

## 📚 Documentation API

- **Swagger UI**: http://localhost:8080/swagger-ui.html (EventCatalog)
- **Swagger UI**: http://localhost:8082/swagger-ui.html (TicketInventory)
- **Swagger UI**: http://localhost:3001/api-docs (User Service)

## 📸 Screenshots

![Homepage](web/public/screenshots/1.jpeg)
Sign up Page

![Event Catalog](web/public/screenshots/2.jpeg)
Login Page

### Organizer Side

![Event Details](web/public/screenshots/3.jpeg)
Dashboard organizer

![Ticket Selection](web/public/screenshots/4.png)
Add New Event Page 

![Booking Process](web/public/screenshots/5.jpeg)
My Events Page

![Cart](web/public/screenshots/6.jpeg)
tickets Management

### Client Side

![Payment](web/public/screenshots/7.png)
Home Page

![Confirmation](web/public/screenshots/8.png)
Events page

![User Profile](web/public/screenshots/9.jpeg)
Event Detail Page

![My Tickets](web/public/screenshots/10.jpeg)
Event Reservation Page

![Order History](web/public/screenshots/11.jpeg)
Ticket Detail

### Admin Panel

![Admin Dashboard](web/public/screenshots/12.jpeg)
Admin Dashboard for Users Management

![Analytics](web/public/screenshots/13.png)
Admin Dashboard for Roles Management
