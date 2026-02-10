# Carpeta: dominio

## Descripción
Contiene la **lógica de negocio pura** del módulo.  
Define entidades, value objects, agregados y reglas de negocio.  
**No depende de frameworks ni infraestructura**.

---

## Qué incluir aquí

- Entidades (`User`, `Order`, etc.)
- Value Objects (`Email`, `Money`, `DateRange`, etc.)
- Agregados y reglas de consistencia
- Interfaces (puertos) que describen lo que el dominio necesita del exterior

---

## Ejemplo de estructura

```
dominio/
 ├─ entidades/
 │    └─ usuario.ts
 ├─ valueObjects/
 │    └─ email.ts
 ├─ agregados/
 │    └─ ordenAggregate.ts
 └─ puertos/
      └─ usuarioRepository.ts
```

---

## Principios clave

- Debe estar completamente aislado de la infraestructura.
- Protege invariantes y reglas de negocio.
- Fomenta un dominio rico (con métodos y comportamientos dentro de las entidades, no solo datos).
- Es el núcleo que **los casos de uso de `aplicacion` utilizan**.
