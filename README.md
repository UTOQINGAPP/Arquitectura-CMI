# Arquitectura CMI – Versión 0.2.3 Alpha

## 📚 ¿Qué es la Arquitectura CMI?

La Arquitectura **CMI** (*Capas, Módulos, Contenedores Integrados*) es una propuesta de organización de proyectos enfocada en:

- Modularidad extrema.
- Escalabilidad limpia.
- Mantenibilidad a largo plazo.
- Separación estricta de responsabilidades.

Inspirada en principios sólidos de ingeniería de software (SRP, OCP, IoC, Cohesión/Acoplamiento), CMI propone una estructura clara que facilita el crecimiento ordenado de aplicaciones, especialmente en entornos como Flutter y desarrollo multiplataforma.

---

## 🏛️ Principios Fundamentales de CMI

- **División por Capas**: `configs/`, `core/`, `ui/`.
- **Módulos Estándar**: Dentro de cada capa, los módulos siguen convenciones estrictas (por ejemplo, `rules/`, `uses/`, `layouts/`, `pages/`, `shared/`).
- **Contenedores y Enrutadores**:
  - Cada contenedor no genérico posee un **enrutador** obligatorio.
  - La comunicación entre capas, módulos y contenedores pasa a través de enrutadores, evitando acoplamientos directos.
- **Nomenclatura Estandarizada**:
  - Cada archivo refleja claramente su propósito (`data_rules.dart`, `services_uses.dart`, etc.).

---

## 🛠️ Estructura Base Estándar

```plaintext
lib/
├── main.dart
│   # Punto de entrada de la aplicación.
│   # Inicializa dependencias y lanza el widget raíz (App).
│
├── configs/
│   └── configs.dart
│       # Enrutador principal de la capa Configs.
│       # Expondrá las configuraciones generales como rutas, temas y ajustes globales.
│
├── core/
│   ├── core.dart
│   │   # Enrutador de la capa Core.
│   │   # Expondrá los módulos Rules y Uses hacia el exterior.
│   │
│   ├── rules/
│   │   ├── data/
│   │   │   └── data_rules.dart
│   │   │       # Enrutador del contenedor Data en Rules.
│   │   │       # Define las entidades, contratos de datos del dominio.
│   │   │
│   │   ├── services/
│   │   │   └── services_rules.dart
│   │   │       # Enrutador del contenedor Services en Rules.
│   │   │       # Define los contratos de servicios de dominio.
│   │   │
│   │   ├── consumers/
│   │   │   └── consumers_rules.dart
│   │   │       # Enrutador del contenedor Consumers en Rules.
│   │   │       # Define los contratos de consumidores de dominio.
│   │   │
│   │   └── rules.dart
│   │       # Enrutador principal del módulo Rules.
│   │
│   └── uses/
│       ├── adapters/
│       │   └── adapters_uses.dart
│       │       # Enrutador del contenedor Adapters en Uses.
│       │       # Define transformaciones entre entidades y estructuras de almacenamiento o infraestructura.
│       │
│       ├── services/
│       │   └── services_uses.dart
│       │       # Enrutador del contenedor Services en Uses.
│       │       # Implementa lógica de servicios de aplicación (uso de reglas, operaciones sobre datos, etc.).
│       │
│       ├── consumers/
│       │   └── consumers_uses.dart
│       │       # Enrutador del contenedor Consumers en Uses.
│       │       # Implementa lógica de consumo que conecta UI y servicios.
│       │
│       ├── origins/
│       │   └── origins_uses.dart
│       │       # Enrutador del contenedor Origins en Uses.
│       │       # Define acceso o adaptación de datos de fuentes externas (API, almacenamiento local, etc.).
│       │
│       └── uses.dart
│           # Enrutador principal del módulo Uses.
│
├── ui/
│   ├── ui.dart
│   │   # Enrutador principal de la capa UI.
│   │   # Expondrá módulos como Layouts, Pages, Shared hacia la presentación.
│   │
│   ├── app/
│   │   └── app.dart
│   │       # Widget raíz de la aplicación (MaterialApp, configuración de rutas, temas, etc.).
│   │
│   ├── layouts/
│   │   └── layouts.dart
│   │       # Enrutador principal de Layouts.
│   │       # Encargado de gestionar los layouts generales de la app (estructura visual fija).
│   │
│   ├── pages/
│   │   └── pages.dart
│   │       # Enrutador principal de Pages.
│   │       # Gestión de páginas independientes de layouts (como login, registro, error 404, etc.).
│   │
│   └── shared/
│       ├── components/
│       │   └── components_shared.dart
│       │       # Enrutador del contenedor Components en Shared.
│       │       # Elementos visuales reutilizables (botones, inputs, etc.).
│       │
│       ├── logic/
│       │   └── logic_shared.dart
│       │       # Enrutador del contenedor Logic en Shared.
│       │       # Lógica reutilizable a nivel general (providers, helpers, etc.).
│       │
│       ├── dialogs/
│       │   └── dialogs_shared.dart
│       │       # Enrutador del contenedor Dialogs en Shared.
│       │       # Ventanas emergentes, modales y componentes de interacción secundaria.
│       │
│       └── shared.dart
│           # Enrutador principal de Shared.
```
