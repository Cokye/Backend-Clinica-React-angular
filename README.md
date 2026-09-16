# ⚙️ Backend - API REST de Autenticación y Usuarios

[![Java](https://img.shields.io/badge/Java-17+-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?style=for-the-badge&logo=spring-boot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Oracle](https://img.shields.io/badge/Oracle_Database-F80000?style=for-the-badge&logo=oracle&logoColor=white)](https://www.oracle.com/database/)
[![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apache-maven&logoColor=white)](https://maven.apache.org/)

Servicio backend desarrollado con **Java y Spring Boot** que centraliza la lógica de autenticación y gestión de usuarios para dos clientes frontend independientes (Angular y React), con persistencia relacional en **Oracle Database**.

---

## 📌 Arquitectura General

El servicio opera como una API RESTful desacoplada:

```text
+--------------------------+
|  Frontend Angular (:4200)| ──┐
+--------------------------+   │
                               ├──> [ Backend Spring Boot (:8080) ] <──> [ Oracle Database ]
+--------------------------+   │
|   Frontend React (:5173) | ──┘
+--------------------------+
```

---

## 🛠️ Stack Tecnológico y Dependencias

* **Lenguaje:** Java 17+
* **Framework:** Spring Boot 3.x
* **Herramienta de compilación:** Maven
* **Base de Datos:** Oracle Database (Free / XE)
* **Dependencias principales (`pom.xml`):**
  * `spring-boot-starter-web`: Creación de controladores RESTful y manejo de peticiones HTTP.
  * `spring-boot-starter-data-jpa`: Capa de persistencia con Hibernate ORM.
  * `com.oracle.database.jdbc:ojdbc11`: Driver JDBC oficial para conexión a Oracle Database.
  * `spring-boot-starter-validation`: Validación de payloads de entrada (`@NotBlank`, `@Email`).
  * `spring-boot-starter-security`: Manejo de autenticación y autorización.
  * `lombok`: Reducción de código repetitivo (getters, setters, constructores).

---

## 📋 Requisitos Previos

* **Java JDK:** 17 o superior.
* **Oracle Database:** Instancia local o contenedor en ejecución en el puerto `1521`.
* **Maven:** Incluido a través de `./mvnw`.

---

## ⚙️ Configuración

Configura la conexión a tu base de datos Oracle en `src/main/resources/application.properties`:

```properties
server.port=8080

# Conexión a Oracle Database
spring.datasource.url=jdbc:oracle:thin:@localhost:1521/FREEPDB1
spring.datasource.username=tu_usuario
spring.datasource.password=tu_password
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver

# Configuración JPA / Hibernate
spring.jpa.database-platform=org.hibernate.dialect.OracleDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

> **Habilitación de CORS:** Asegúrate de habilitar el acceso cruzado para los orígenes de desarrollo:
> * `http://localhost:4200` (Angular)
> * `http://localhost:5173` (React)

---

## 🚀 Instalación y Puesta en Marcha

### 1. Clonar el repositorio

```bash
git clone https://github.com/Cokye/Backend-Clinica-React-angula
cd TU_REPOSITORIO_BACKEND
```

### 2. Ejecutar la aplicación

```bash
./mvnw clean spring-boot:run
```

API disponible en: `http://localhost:8080`

---

## 📡 Endpoints de la API

| Método | Endpoint | Descripción | Consumido por |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/auth/login` | Valida credenciales e inicia sesión | Angular / React |
| `GET` | `/api/usuarios` | Devuelve el listado de usuarios registrados | Angular / React |
| `POST` | `/api/usuarios` | Registra un nuevo usuario en la base de datos | Angular / React |

---

## 👤 Autor

Desarrollado por **Felipe** ([@Cokye](https://github.com/Cokye))
