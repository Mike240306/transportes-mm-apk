# Formato de Respaldo en Google Drive - Transportes M&M

## 📁 Cómo se ve en Google Drive

### Nombres de archivos:
```
backup-transportes-mm-2025-07-21T03-34-56.json
backup-transportes-mm-2025-07-20T15-22-10.json  
backup-transportes-mm-2025-07-19T09-45-33.json
```

### Ubicación:
- **Carpeta**: En la carpeta que especifiques o en la raíz de Google Drive
- **Tipo**: Archivos JSON (texto plano, legible)
- **Tamaño**: Normalmente 0.01 - 0.10 MB (muy pequeños)

## 📋 Contenido del archivo JSON

### Estructura completa:
```json
{
  "backup_info": {
    "created_at": "2025-07-21T03:34:56.803Z",
    "timestamp": "2025-07-21T03-34-56",
    "version": "1.0",
    "app_name": "Transportes M&M"
  },
  "data": {
    "users": [
      {
        "id": 1,
        "username": "Leonidas", 
        "role": "admin",
        "firstName": "Miguel",
        "lastName": "Admin",
        "email": "admin@transportesmm.com",
        "isActive": true,
        "createdAt": "2025-07-20T..."
      }
    ],
    "drivers": [
      {
        "id": 10,
        "userId": 9,
        "driverCode": "Kwid Plata",
        "profileImageUrl": "/uploads/1753056020410-514458646.jpg",
        "carInfo": {...}
      }
    ],
    "tickets": [
      {
        "id": 8,
        "driverId": 10,
        "weekStart": "2025-07-07",
        "weekEnd": "2025-07-13", 
        "platformIncome": 2500.00,
        "cashPayments": 800.00,
        "netTotal": 1200.50
      }
    ],
    "messages": [...],
    "communications": [...],
    "driver_locations": [...]
  },
  "counts": {
    "users": 10,
    "drivers": 8,
    "tickets": 0,
    "messages": 0,
    "communications": 2,
    "driver_locations": 5
  }
}
```

## 🔍 Qué información específica se respalda:

### 👥 Usuarios (users):
- Administradores y choferes
- Credenciales de acceso (contraseñas encriptadas)
- Información personal: nombres, teléfonos, emails
- Estados activos/inactivos

### 🚗 Choferes (drivers):
- Códigos de choferes (ej: "Kwid Plata", "Potra", "Oso")
- URLs de fotos de perfil
- Información del auto
- Fechas de registro

### 🧾 Tickets (tickets):
- Historial completo semanal
- Ingresos de plataforma
- Pagos en efectivo  
- Deducciones (renta, IVA, ISR)
- Totales netos calculados
- Quién creó/modificó cada ticket

### 💬 Mensajes (messages):
- Chat completo entre admin y choferes
- Archivos adjuntos
- Estados de leído/no leído
- Timestamps exactos

### 📢 Comunicados (communications):
- Mensajes broadcast del administrador
- Estados de lectura por chofer
- Fechas de envío

### 📍 Ubicaciones GPS (driver_locations):
- Coordenadas exactas de choferes
- Estados online/offline
- Últimas actualizaciones de ubicación

## 📱 Cómo ver/abrir los respaldos:

### En Google Drive:
1. **Navegador web**: Haz doble clic → se abre como texto
2. **Aplicación Drive**: Descargar → abrir con editor de texto
3. **Compartir**: Enviar enlace a otros administradores

### En tu teléfono/computadora:
1. **Descargar archivo**: `.json` se puede abrir con cualquier editor
2. **Aplicaciones recomendadas**:
   - **Android**: "Text Editor", "JSON Viewer"
   - **iPhone**: "Files", "Documents"  
   - **PC**: Notepad, Visual Studio Code, cualquier editor
   - **Mac**: TextEdit, Visual Studio Code

### Para restaurar datos:
- El formato JSON es estándar
- Se puede importar a cualquier base de datos
- Fácil de leer por programadores
- Compatible con herramientas de migración

## ⚡ Ventajas del formato JSON:

✅ **Universal**: Se abre en cualquier dispositivo
✅ **Legible**: Puedes ver exactamente qué datos tienes
✅ **Pequeño**: Archivos muy ligeros  
✅ **Seguro**: No se puede corromper fácilmente
✅ **Estándar**: Compatible con todas las herramientas modernas

## 🔄 Gestión automática en Google Drive:

- **Subida automática**: Cada respaldo se sube inmediatamente
- **Limpieza automática**: Solo mantiene los 12 más recientes (cobertura anual completa)
- **Sin duplicados**: Sistema inteligente de nombres únicos  
- **Acceso desde cualquier lugar**: Disponible en todos tus dispositivos
- **Historial anual**: 12 respaldos cubren todos los meses del año

¡Es el formato más seguro y compatible para proteger toda tu información! 🛡️