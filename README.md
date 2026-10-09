# task-link-DesarollodeAppsMoviles-
# TaskLink - Sistema de Gestión Académica Móvil 

**TaskLink** es una plataforma integral desarrollada bajo una arquitectura cliente-servidor desacoplada, orientada a centralizar y optimizar la gestión académica (tareas, horarios, asistencia, matrículas y calificaciones) con control de accesos por roles (Estudiante, Docente, Tutor/Apoderado y Administrador).

---

## Stack Tecnológico

### Cliente Móvil (Android)
* **Lenguaje:** Java
* **Interfaz:** XML Views con **View Binding** y componentes de **Google Material Design 3**.
* **Consumo de API:** Retrofit 2 + OkHttp + Gson.
* **Seguridad y Almacenamiento:** Android Security Crypto (`EncryptedSharedPreferences`) y tokens JWT.
* **Notificaciones:** Firebase Cloud Messaging (FCM).
* **Compatibilidad:** Desde Android 8.0 (API 26) en adelante.

### Servidor Backend (API REST)
* **Framework:** Spring Boot 3[cite: 1] (Java 17).
* **Seguridad:** Spring Security 6[cite: 1] (Stateless, autenticación por tokens JWT firmados con HMAC-SHA256[cite: 1] y cifrado de contraseñas **BCrypt**[cite: 1]).
* **Persistencia:** Spring Data JPA / Hibernate[cite: 1].
* **Contenedores:** Docker[cite: 1].

###  Base de Datos
* **Gestor:** MySQL 8.0[cite: 1] (Motor InnoDB, transaccionalidad ACID[cite: 1], codificación `utf8mb4` y normalización en Tercera Forma Normal - 3FN[cite: 1]).

---

## Estructura del Repositorio

El repositorio se organiza de forma modular para separar claramente las responsabilidades del cliente y el servidor:
```text
TaskLink/
│
├── mobile/          # Proyecto nativo de Android Studio (Java/XML)
│   ├── app/src/main/java/com/upn/tasklink/
│   │   ├── adapters/    # Adaptadores para RecyclerView (Tareas, Asistencia)
│   │   ├── models/      # Clases POJO de dominio
│   │   ├── network/     # Clientes Retrofit, Interceptors y DTOs
│   │   └── ui/          # Activities y Fragments por roles
│   └── ...
│
├── backend/         # Servidor API REST en Spring Boot 3
│   ├── src/main/java/com/upn/tasklink/
│   │   ├── controllers/ # Endpoints REST semánticos
│   │   ├── services/    # Lógica de negocio y validaciones pedagógicas
│   │   ├── repository/  # Interfaces JpaRepository
│   │   └── security/    # Configuración JWT y filtros de seguridad
│   └── ...
│
└── README.md
