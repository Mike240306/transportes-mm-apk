# 🔧 Cómo Activar Google Drive para Respaldos Automáticos

## Paso 1: Crear Proyecto en Google Cloud Console

1. **Ve a Google Cloud Console**: https://console.cloud.google.com
2. **Crear nuevo proyecto**:
   - Haz clic en "Seleccionar proyecto" → "Nuevo proyecto"
   - Nombre: "Transportes MM Backups" (o el que prefieras)
   - Haz clic en "Crear"

## Paso 2: Habilitar Google Drive API

1. **En tu proyecto**, ve a "APIs y servicios" → "Biblioteca"
2. **Busca "Google Drive API"**
3. **Haz clic en "Google Drive API"** → "Habilitar"

## Paso 3: Crear Cuenta de Servicio

1. **Ve a "APIs y servicios"** → "Credenciales"
2. **Haz clic en "Crear credenciales"** → "Cuenta de servicio"
3. **Completa los datos**:
   - Nombre: "transportes-mm-backup"
   - ID: se genera automáticamente
   - Descripción: "Cuenta para respaldos automáticos"
4. **Haz clic en "Crear y continuar"**
5. **Rol**: Selecciona "Editor" o "Propietario"
6. **Haz clic en "Listo"**

## Paso 4: Generar Clave JSON

1. **En la lista de cuentas de servicio**, haz clic en la que creaste
2. **Ve a la pestaña "Claves"**
3. **Haz clic en "Agregar clave"** → "Crear nueva clave"
4. **Selecciona "JSON"** → "Crear"
5. **Se descargará un archivo JSON** - guárdalo seguro

## Paso 5: Configurar en Replit

### GOOGLE_SERVICE_ACCOUNT:
1. **Abre el archivo JSON descargado** con cualquier editor de texto
2. **Copia TODO el contenido** (desde la primera { hasta la última })
3. **En Replit**, ve a Secrets y pega el JSON completo

Ejemplo del contenido que debes copiar:
```json
{
  "type": "service_account",
  "project_id": "tu-proyecto-123456",
  "private_key_id": "abcd1234...",
  "private_key": "-----BEGIN PRIVATE KEY-----\nMIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQC...\n-----END PRIVATE KEY-----\n",
  "client_email": "transportes-mm-backup@tu-proyecto-123456.iam.gserviceaccount.com",
  "client_id": "123456789012345678901",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://oauth2.googleapis.com/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/transportes-mm-backup%40tu-proyecto-123456.iam.gserviceaccount.com"
}
```

### GOOGLE_DRIVE_FOLDER_ID (Opcional):
1. **Ve a Google Drive** (drive.google.com)
2. **Crea una carpeta** llamada "Respaldos Transportes MM"
3. **Abre la carpeta** y copia el ID de la URL
   - URL: `https://drive.google.com/drive/folders/1AbCdEfGhIjKlMnOpQrStUvWxYz`
   - ID: `1AbCdEfGhIjKlMnOpQrStUvWxYz`
4. **En Replit**, pega solo el ID en GOOGLE_DRIVE_FOLDER_ID

## Paso 6: Dar Permisos a la Cuenta de Servicio

1. **En Google Drive**, ve a la carpeta que creaste
2. **Haz clic derecho** → "Compartir"
3. **Agrega el email de la cuenta de servicio**:
   - Email: `transportes-mm-backup@tu-proyecto-123456.iam.gserviceaccount.com`
   - Permisos: "Editor"
4. **Enviar**

## ✅ Verificación

Una vez configurado, verás en el dashboard:
- ✅ **Google Drive**: "Subida automática activa"
- El botón cambiará a: "Crear Respaldo + Drive"

Cada respaldo se guardará automáticamente en:
- 📂 Local: `/backups/` en el servidor
- ☁️ Google Drive: En tu carpeta especificada

## 🔒 Seguridad

- ✅ Las credenciales están encriptadas en Replit
- ✅ Solo admins autenticados pueden crear respaldos  
- ✅ La cuenta de servicio solo tiene acceso a Drive
- ✅ Se mantienen máximo 10 respaldos en Drive

## 🆘 Problemas Comunes

**Error "API not enabled"**:
- Verifica que habilitaste Google Drive API

**Error "Forbidden"**:
- Verifica que compartiste la carpeta con la cuenta de servicio

**Error "Invalid credentials"**:
- Verifica que copiaste el JSON completo correctamente

**No se sube a Drive**:
- Verifica que el GOOGLE_SERVICE_ACCOUNT esté configurado
- Revisa los logs del servidor para errores específicos