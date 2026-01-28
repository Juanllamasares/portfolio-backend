## ✨ Características principales

- Arquitectura **Hexagonal** (Ports & Adapters) → dominio 100% puro y desacoplado
- Cumplimiento estricto de **principios SOLID** (especialmente Dependency Inversion y Single Responsibility)
- **Domain-Driven Design** ligero: entidades ricas, value objects, excepciones de dominio
- **Tests**:
  - Unitarios (JUnit 5 + Mockito) → >90% coverage en domain + application
  - Integración (Testcontainers + @SpringBootTest slice tests)
  - Arquitectónicos (ArchUnit) → enforcement de reglas hexagonales
- Validación declarativa + self-validating entities
- Manejo de errores centralizado y respuestas consistentes (RFC 7807 Problem Details)
- Configuración con **YAML** + perfiles (dev, test, prod)
- Documentación automática con **OpenAPI 3 / Swagger**
- Preparado para CI/CD (GitHub Actions incluido)

## 🏛️ Arquitectura

```text
src/main/java/com.tuempresa.proyecto
├── Application.java                 ← Spring Boot entry point
├── domain                           ← Núcleo puro (sin dependencias externas)
│   ├── model                        ← Entidades, Value Objects, IDs
│   ├── service                      ← Puertos primarios (interfaces de casos de uso)
│   └── exception                    ← Excepciones de negocio
├── application                      ← Casos de uso / orquestación
│   └── service
│       └── [UseCase]Service.java    ← Implementación de puertos primarios
└── infrastructure                   ← Adaptadores + Spring wiring
    ├── adapter
    │   ├── in.web                       ← Controladores REST, DTOs de entrada/salida
    │   └── out.persistence              ← Implementaciones de puertos secundarios (JPA, etc.)
    ├── config                           ← Beans, Security, OpenAPI, etc.
    └── repository                       ← Interfaces Spring Data JPA
