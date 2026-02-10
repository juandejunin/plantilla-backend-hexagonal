# Template Backend – Arquitectura Hexagonal por Módulos

## 📌 Descripción
Este repositorio provee un **template base para desarrollar backends modulares** utilizando **arquitectura hexagonal** aplicada **de forma independiente en cada módulo de dominio**.

El objetivo del template es:
- escalar sin perder control
- proteger la lógica de negocio
- facilitar el mantenimiento y la evolución del sistema
- servir como guía estructural para equipos

---

## 🧠 Principios de diseño

> **La estructura se organiza por módulos de dominio.  
> Cada módulo implementa arquitectura hexagonal de forma independiente.**

A partir de este principio:

- los **módulos organizan el dominio**
- la **arquitectura hexagonal organiza las dependencias**
- el dominio queda aislado de detalles técnicos
- no existe una “hexagonal global” para todo el sistema

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

### 📁 `modulos`
Contiene todos los **módulos de dominio** del sistema.  
Cada módulo representa un subdominio o bounded context.

### 📁 `modulo-ejemplo`
Es un **módulo de referencia** incluido únicamente con fines didácticos.

👉 Para crear un nuevo módulo:
1. Copie la carpeta `modulo-ejemplo`
2. Renómbrela según el dominio (por ejemplo: `usuarios`, `pedidos`)
3. Adapte el contenido al nuevo contexto

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
Este template **no modela un negocio específico**.  
Modela una **forma de estructurar y pensar sistemas backend**:

- modular
- explícita
- orientada al dominio
- preparada para crecer

---

## 🚀 Próximos pasos
A partir de este template, cada equipo puede:
- agregar nuevos módulos
- definir reglas de dependencia más estrictas
- adaptar la infraestructura según el stack tecnológico
