# Guía de Instalación del MCP Server de Airtable

Ahora que hemos clonado el repositorio, aquí te muestro los pasos para completar la instalación y configuración:

## 1. Requisitos Previos

- Node.js (versión 18 o superior)
- npm (incluido con Node.js)
- Una cuenta de Airtable y una API key

## 2. Pasos de Instalación

### Opción 1: Instalación con npx (Recomendado)

1. Abre Claude Desktop
2. Ve a Configuración > Desarrollador > Editar Configuración
3. Modifica el archivo `claude_desktop_config.json` para incluir:

```json
{
  "mcpServers": {
    "airtable": {
      "command": "npx",
      "args": ["@felores/airtable-mcp-server"],
      "env": {
        "AIRTABLE_API_KEY": "tu_api_key_aqui"
      }
    }
  }
}
```

### Opción 2: Instalación Local (Desarrollo)

1. Instala las dependencias:
```bash
cd /Users/josealejandrotiendaramirez/Documents/01- PROYECTOS/05- AI PROJECTS/MCP/airtable-mcp-server
npm install
```

2. Construye el proyecto:
```bash
npm run build
```

3. Ejecuta el servidor:
```bash
node build/index.js
```

4. Configura Claude para usar tu instalación local:
   - Abre Claude Desktop
   - Ve a Configuración > Desarrollador > Editar Configuración
   - Modifica el archivo `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "airtable": {
      "command": "node",
      "args": ["/Users/josealejandrotiendaramirez/Documents/01- PROYECTOS/05- AI PROJECTS/MCP/airtable-mcp-server/build/index.js"],
      "env": {
        "AIRTABLE_API_KEY": "tu_api_key_aqui"
      }
    }
  }
}
```

## 3. Obtener una API Key de Airtable

1. Inicia sesión en [airtable.com](https://airtable.com)
2. Ve a [Airtable's Builder Hub](https://airtable.com/create/tokens) para crear un token de acceso personal
3. En la sección de token de acceso personal, selecciona estos permisos:
   - data.records:read
   - data.records:write
   - schema.bases:read
   - schema.bases:write
4. Selecciona el workspace o bases a las que quieres dar acceso
5. Copia el token generado y úsalo como tu AIRTABLE_API_KEY

## 4. Verificar la Instalación

1. Inicia Claude Desktop
2. El servidor MCP de Airtable debería aparecer en la sección "Connected MCP Servers"
3. Prueba con un comando simple:
```
Lista todas las bases de Airtable
```

## Consideraciones de Seguridad

- Nunca compartas tu API key de Airtable
- Mantén actualizado el servidor MCP
- Usa permisos mínimos necesarios en Airtable

## Solución de Problemas

Si encuentras problemas:

1. Verifica que Node.js esté instalado correctamente
2. Asegúrate de que la API key es válida
3. Revisa los logs de Claude Desktop para errores específicos
4. Confirma que la ruta al archivo JS es correcta en la configuración
