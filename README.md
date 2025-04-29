# Arquitectura CMI – Versión 0.2.0 Alpha

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
├── configs/
│   └── configs.dart
├── core/
│   ├── core.dart
│   ├── rules/
│   │   ├── data/
│   │   │   └── data_rules.dart
│   │   ├── services/
│   │   │   └── services_rules.dart
│   │   ├── consumers/
│   │   │   └── consumers_rules.dart
│   │   └── rules.dart
│   └── uses/
│       ├── adapters/
│       │   └── adapters_uses.dart
│       ├── services/
│       │   └── services_uses.dart
│       ├── consumers/
│       │   └── consumers_uses.dart
│       ├── origins/
│       │   └── origins_uses.dart
│       └── uses.dart
├── ui/
│   ├── ui.dart
│   ├── app/
│   │   └── app.dart
│   ├── layouts/
│   │   └── layouts.dart
│   ├── pages/
│   │   └── pages.dart
│   └── shared/
│       ├── components/
│       │   └── components_shared.dart
│       ├── logic/
│       │   └── logic_shared.dart
│       ├── dialogs/
│       │   └── dialogs_shared.dart
│       └── shared.dart
