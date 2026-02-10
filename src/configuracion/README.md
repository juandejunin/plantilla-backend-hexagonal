# Carpeta: configuracion

## Descripción
Esta carpeta contiene la **configuración e inicialización global** de la aplicación.  
Incluye archivos que preparan la infraestructura y el arranque de la app, aplicable a todos los módulos.

No debe contener lógica de negocio ni casos de uso.

---

## Qué incluir aquí

1. **Bootstrap global**
   - Archivo principal de arranque de la aplicación.
   - Inicializa dependencias, servicios compartidos y adaptadores globales.
   - Ejemplo: `bootstrap.ts`

2. **Servidor / listeners**
   - Configura y levanta el servidor HTTP, listeners de eventos o colas globales.
   - Ejemplo: `server.ts`

3. **Base de datos**
   - Inicialización de la conexión a la base de datos principal.
   - Pools, migraciones, clientes, etc.
   - Ejemplo: `bbdd.ts`

4. **Configuraciones transversales**
   - Logging global
   - Variables de entorno
   - Integraciones que afectan a todos los módulos

---

## Ejemplo de estructura

```
configuracion/
 ├─ bootstrap.ts      # Inicializa servicios y dependencias globales
 ├─ server.ts         # Inicializa servidor HTTP y listeners globales
 └─ bbdd.ts           # Inicializa conexión con la base de datos
```

---

## Ejemplo de bootstrap.ts (TypeScript)

```typescript
import { initDatabase } from './bbdd';
import { startServer } from './server';

export async function bootstrap() {
  const db = await initDatabase();
  const server = await startServer();

  return { db, server };
}
```

> Este archivo prepara la aplicación para ejecutar todos los módulos, levantando la infraestructura global sin incluir lógica de negocio.

