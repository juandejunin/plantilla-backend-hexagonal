# Carpeta: aplicacion

## Descripción
Contiene los **casos de uso** del módulo y la **orquestación de la lógica de negocio**.  
Coordina el dominio con los adaptadores, pero **no implementa reglas de negocio directamente**.

---

## Qué incluir aquí

- Casos de uso (services, handlers)
- Orquestación entre entidades y value objects del dominio
- Invocación de puertos (interfaces del dominio) y adaptadores concretos
- Validaciones de flujo (no reglas de negocio)

---

## Ejemplo de estructura

```
aplicacion/
 ├─ casosDeUso/
 │    └─ crearUsuario.ts
 └─ servicios/
      └─ usuarioService.ts
```

---

## Principios clave

- Depende del `dominio` y de interfaces de los adaptadores.
- No contiene lógica de infraestructura (HTTP, DB, etc.).
- Cada caso de uso debe ser **unitariamente testeable** sin necesidad de frameworks.
