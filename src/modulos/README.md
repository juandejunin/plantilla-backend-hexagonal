# Carpeta: modulos

## Descripción
Esta carpeta contiene todos los **módulos de dominio** de la aplicación.  
Cada módulo representa un subdominio o bounded context, y encapsula su lógica de negocio siguiendo arquitectura hexagonal.

El objetivo es organizar los dominios de manera modular, permitiendo escalabilidad y mantenibilidad.

---

## Cómo usar

1. Para crear un nuevo módulo:
   - Copie un módulo de ejemplo, como `modulo-ejemplo`.
   - Renómbrelo según su dominio, por ejemplo: `usuarios` o `pedidos`.
   - Adapte el contenido de `dominio`, `aplicacion`, `adaptadores` y `configuracion` según el contexto del módulo.

2. Cada módulo debe ser **independiente**:
   - No debe depender directamente de otros módulos para lógica de negocio.
   - La comunicación entre módulos debe realizarse mediante **casos de uso expuestos**, **eventos** o **interfaces explícitas**.

---

## Estructura de un módulo

```
modulos/
 └─ modulo-ejemplo/
     ├─ dominio           # Entidades, value objects, reglas de negocio
     ├─ aplicacion        # Casos de uso y orquestación de lógica
     ├─ adaptadores       # Controladores, repositorios, servicios externos
     └─ configuracion     # Configuración específica del módulo (opcional)
```

### Breve descripción de cada carpeta dentro de un módulo:

- **dominio**: Aquí vive la lógica de negocio pura, independiente de frameworks o infraestructura.
- **aplicacion**: Coordina los casos de uso y conecta el dominio con los adaptadores.
- **adaptadores**: Implementaciones técnicas de entrada/salida, persistencia, mensajería, API, etc.
- **configuracion**: Archivos de inicialización específicos del módulo, si los necesita.

---


