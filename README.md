# POC de Librería Común (Prueba de Concepto)

## Descripción General
Este repositorio contiene la Prueba de Concepto (POC) para la arquitectura estandarizada de APIs RESTful. Demuestra la implementación de una estructura de directorios orientada al dominio, utilizando librerías centralizadas de RAML 1.0 y tipos de datos consumidos directamente desde Anypoint Exchange.

## Estructura del Repositorio
Para garantizar una alta escalabilidad y mantenibilidad en todo el ecosistema de APIs, este proyecto se adhiere estrictamente a un enfoque de diseño orientado al dominio (DDD). Los recursos se agrupan por entidad de negocio en lugar de por clasificación técnica:

```
├── api.raml
├── examples
│   └── customers
│       ├── customer-paginated-list-response.json
│       ├── customer-patch-request.json
│       ├── customer-post-request.json
│       ├── customer-put-request.json
│       └── customer-response.json
├── exchange.json
├── LICENSE
├── README.md
└── types
    └── customers
        ├── CustomerPatch.raml
        ├── CustomerRequest.raml
        └── CustomerResponse.raml
```

## Convenciones de Nomenclatura y Estándares
Las siguientes convenciones de nomenclatura deben aplicarse estrictamente para cualquier nueva contribución a este repositorio:

1. **Tipos de Datos (RAML):** 
   * Modelados como entidades de negocio, nunca como verbos HTTP.
   * Deben usar `PascalCase` (ej., `CustomerRequest.raml`, `CustomerResponse.raml`).
2. **Ejemplos (JSON):** 
   * Deben usar `kebab-case`.
   * Estructurados como `{entidad}-{acción/método}-{tipo}.json` (ej., `customer-post-request.json`, `customer-paginated-list-response.json`).
3. **Agrupación de Directorios:** 
   * Los archivos están aislados por dominio de negocio (ej., `/customers/`). El uso de carpetas genéricas cruzadas como `/requests` o `/responses` está estrictamente prohibido para simplificar la gestión de recursos y el desacoplamiento.

## Capacidades Principales
* **Paginación Estandarizada:** Implementa un wrapper estándar `PaginatedResponse` para recursos de colección, asegurando una estructura de metadatos consistente (`totalRecords`, `offset`, `limit`) en todos los endpoints GET.
* **Traits y Resource Types Modulares:** Hereda comportamientos arquitectónicos comunes (manejo de errores, correlation IDs, parámetros de consulta) directamente de la Librería Común centralizada en Exchange.

## Despliegue y Uso
Esta POC está diseñada para ser importada en Anypoint Studio o Anypoint Design Center. 
Asegúrate de que tu entorno local esté correctamente autenticado con la plataforma Anypoint de la organización para resolver las dependencias externas de Exchange definidas en el `api.raml` raíz.
