# Carpeta: adaptadores

## Descripción
Esta carpeta contiene las **implementaciones técnicas** que interactúan con el mundo exterior o con infraestructuras externas.  
Su función es **adaptar la aplicación y el dominio a tecnologías concretas**, sin incluir lógica de negocio.

---

## Qué incluir aquí

- Controladores (HTTP, CLI, GraphQL, eventos)
- Repositorios que implementen los puertos del dominio
- Integraciones con APIs externas
- Mensajería, colas o listeners
- Mappers o transformadores de datos (DTOs → entidades)

---

## Ejemplo de estructura

```
adaptadores/
 ├─ controladores/
 │    └─ httpController.ts
 ├─ repositorios/
 │    └─ usuarioRepository.ts
 └─ serviciosExternos/
      └─ emailService.ts
```

---

## Principios clave

- Dependen de `aplicacion` y `dominio`, pero **no deben contener reglas de negocio**.
- Los adaptadores son reemplazables sin afectar el dominio.
- Todos los accesos externos deben ir por aquí (bases de datos, APIs, colas, etc.).
