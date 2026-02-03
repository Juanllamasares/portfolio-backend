## ✨ Características principales

- Arquitectura **Hexagonal** (Ports & Adapters) → dominio 100% puro y desacoplado
- Cumplimiento estricto de **principios SOLID** (especialmente Dependency Inversion y Single Responsibility)
- **Domain-Driven Design** ligero: entidades ricas, value objects, excepciones de dominio
- **Tests**:
  - Unitarios (JUnit 5 + Mockito) 
  - Integración (Testcontainers + @SpringBootTest slice tests)
  - Arquitectónicos (ArchUnit) → enforcement de reglas hexagonales
- Validación declarativa + self-validating entities
- Manejo de errores centralizado y respuestas consistentes 
- Configuración con **YAML** + perfiles (dev, test, prod)
- Documentación automática con **OpenAPI 3 / Swagger**
- Preparado para CI/CD (GitHub Actions incluido)

## 🏛️ Arquitectura

```text
src/main/java/com/juan_llamasares/portfolio_backend/
├── domain/
│   └── model/
│       
├── application/
│   ├── port/
│   │   ├── in/     
│   │   └── out/    
│   ├── usecase/   
│   └── dto/       
└── infrastructure/
    ├── adapter/
    │   ├── in/
    │   │   └── web/
    │   └── out/
    │       └── persistence/
    │           ├── entity/
    │           ├── repository/
    │           └── impl/
    ├── config/     
    └── mapper/     
       
