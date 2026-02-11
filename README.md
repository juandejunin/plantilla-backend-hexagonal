# Template Backend – Ports & Adapters con Vertical Slicing

## 📌 Descripción

Este repositorio provee un template base para desarrollar backends modulares utilizando arquitectura hexagonal (Ports & Adapters) aplicada de forma independiente en cada módulo, siguiendo el enfoque de Vertical Slicing.

Cada módulo funciona como una rebanada vertical, conteniendo todo lo necesario para implementar una funcionalidad completa: dominio, aplicación y adaptadores.

El objetivo del template es:

Escalar el proyecto sin perder control ni modularidad.

Proteger la lógica de negocio manteniéndola independiente de frameworks o infraestructura.

Facilitar el mantenimiento y la evolución del sistema.

Servir como guía estructural para equipos, usando nomenclatura y convenciones reconocidas internacionalmente (Ports & Adapters, Vertical Slicing).ervir como guía estructural para equipos

---

## 🧠 Principios de diseño

El sistema se organiza en módulos de dominio independientes.
Cada módulo implementa su propia arquitectura hexagonal (Ports & Adapters), siguiendo el enfoque de Vertical Slicing.

A partir de este principio:

Cada módulo encapsula su propio dominio, casos de uso y adaptadores, formando una slice vertical independiente.

La arquitectura hexagonal asegura que las dependencias fluyan de afuera hacia adentro, protegiendo el dominio de detalles técnicos y frameworks.

No existe una “hexagonal global” para todo el sistema; cada módulo mantiene autonomía y cohesión.

Facilita modularidad, escalabilidad y pruebas aisladas para cada funcionalidad.
---

## 🧩 Estructura del proyecto

```text
src
 ├─ configuracion
 │   └─ (bootstrap, configuración transversal)
 └─ modulos
     └─ modulo-ejemplo
         ├─ dominio
         ├─ aplicacion
         ├─ adaptadores
         └─ configuracion
```

### 📁 modulos

Contiene todos los módulos de dominio del sistema.
Cada módulo representa un subdominio o bounded context y funciona como una slice vertical (Vertical Slice):

Cada módulo incluye dominio, aplicación y adaptadores, de manera autocontenida.

Permite aislar la lógica de negocio de detalles técnicos y frameworks.

Facilita modularidad, pruebas independientes y escalabilidad, ya que no existe una arquitectura global que acople todos los módulos.

💡 Esto significa que cada módulo puede evolucionar, probarse y desplegarse de manera independiente, siguiendo los principios de Ports & Adapters.

### 📁 modulo-ejemplo

Es un módulo de referencia, incluido únicamente con fines didácticos.
Sirve como ejemplo de slice vertical, implementando dominio, aplicación y adaptadores siguiendo los principios de Ports & Adapters.

👉 Para crear un nuevo módulo:

1. Copie la carpeta `modulo-ejemplo`.
2. Renómbrela según el subdominio o bounded context (por ejemplo: `usuarios`, `pedidos`).
3. Adapte el contenido al nuevo contexto, manteniendo la separación de `dominio`, `aplicacion` y `adaptadores`.

---

## 🏗️ Arquitectura de un módulo

Cada módulo implementa arquitectura hexagonal internamente:

### `dominio`
- lógica de negocio
- reglas e invariantes
- entidades y value objects
- interfaces (puertos) que el dominio necesita

📌 No depende de frameworks ni infraestructura.

---

### `aplicacion`
- casos de uso
- orquestación de acciones
- coordinación entre dominio y puertos

📌 Depende del dominio, pero no de adaptadores concretos.

---

### `adaptadores`
- implementaciones técnicas
- controladores (HTTP, eventos, etc.)
- persistencia, mensajería, integraciones externas

📌 Dependen de `aplicacion` y `dominio`.

---

### `configuracion`
- configuración específica del módulo
- wiring / inyección de dependencias
- inicialización técnica local al módulo

---

## 🔒 Reglas generales

- El **dominio no depende de infraestructura**
- Los módulos **no acceden directamente** al dominio de otros módulos
- La comunicación entre módulos debe hacerse mediante:
  - casos de uso expuestos
  - eventos
  - contratos explícitos

---

## 🎯 Objetivo del template
El objetivo del template es:

- Escalar el proyecto sin perder control ni modularidad.
- Proteger la lógica de negocio manteniéndola independiente de frameworks o infraestructura.
- Facilitar el mantenimiento y la evolución del sistema.
- Servir como guía estructural para equipos, usando nomenclatura y convenciones reconocidas internacionalmente (Ports & Adapters, Vertical Slicing).


---

## 🚀 Próximos pasos
A partir de este template, cada equipo puede:
- agregar nuevos módulos
- definir reglas de dependencia más estrictas
- adaptar la infraestructura según el stack tecnológico
