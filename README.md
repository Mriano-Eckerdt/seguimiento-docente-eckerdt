# 📘 Seguimiento Docente - Prof. Eckerdt Mariano

Aplicación web progresiva (PWA) para el seguimiento de asistencia, evaluaciones y promedios de estudiantes. Diseñada para docentes de matemática, funciona 100% offline y sincroniza con Firebase + Google Drive.

## ✨ Características

- 📋 **Gestión de cursos** por año y división
- ✅ **Asistencia** con estados: Presente (P), Ausente (A), Tarde (T), Retirado (R)
- 📝 **Evaluaciones** con tipos configurables y promedios automáticos
- 📊 **Resumen anual** con condición de aprobación
- 📄 **Exportación PDF** compacta (sin bloques negros)
- 💾 **Exportación CSV** para Excel
- ☁️ **Sincronización Firebase** en tiempo real
- 🗂️ **Backup Google Drive** manual y automático
- 📱 **Modo offline** con Service Worker
- 🔒 **Datos locales** (LocalStorage) + nube

## 🚀 Cómo usar

### Opción 1: GitHub Pages (Recomendado)

1. Creá un repositorio nuevo en GitHub
2. Subí estos 4 archivos a la raíz del repo
3. Andá a **Settings → Pages → Source** y seleccioná la rama `main`
4. Tu app estará en `https://tuusuario.github.io/nombre-repo/`

### Opción 2: Firebase Hosting

```bash
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy
```

### Opción 3: Local

Simplemente abrí `index.html` en tu navegador. Los datos se guardan en LocalStorage.

## ⚙️ Configuración

### Firebase (Sincronización en la nube)

1. Andá a [Firebase Console](https://console.firebase.google.com/)
2. Creá un proyecto → Agregá una app Web
3. Copiá el objeto de configuración JSON
4. En la app, tocá el botón **🔄 Sincronizado** (barra superior)
5. Pegá el JSON y guardá

**Reglas de Realtime Database:**
```json
{
  "rules": {
    "prof_eckerdt": {
      "$uid": {
        ".read": "auth.uid == $uid",
        ".write": "auth.uid == $uid"
      }
    }
  }
}
```

### Google Drive (Backup)

1. Andá a [Google Cloud Console](https://console.cloud.google.com/)
2. Activá la **Google Drive API**
3. Creá credenciales:
   - **OAuth 2.0 Client ID** (aplicación Web)
   - **API Key**
4. En la app, pegalos en el modal de sincronización
5. Usá **Guardar Backup** / **Restaurar Backup**

## 📁 Estructura del proyecto

```
📁 seguimiento-docente/
├── 📄 index.html       ← Aplicación principal (Firebase + Drive + PWA)
├── 📄 manifest.json    ← Configuración PWA (instalable)
├── 📄 sw.js           ← Service Worker (funciona sin internet)
└── 📄 README.md       ← Este archivo
```

## 📱 Instalar en el celular

### Android (Chrome)
1. Abrí la app en Chrome
2. Tocá los **3 puntos → Agregar a pantalla de inicio**
3. Se instala como app nativa

### iPhone (Safari)
1. Abrí la app en Safari
2. Tocá **Compartir → Agregar a pantalla de inicio**

## 🔄 Flujo de trabajo recomendado

1. **Configurá el año lectivo** y las fechas de trimestres
2. **Creá los cursos** y los estudiantes
3. **Marcá asistencia** día a día (funciona sin internet)
4. **Cargá evaluaciones** con calificaciones
5. **Sincronizá con Firebase** cuando tengas WiFi
6. **Hacé backup a Drive** periódicamente

## 🛡️ Seguridad

- Los datos se guardan **primero en tu dispositivo** (offline first)
- Firebase usa **autenticación anónima** (sin contraseñas)
- Cada usuario tiene su propio nodo en la base de datos
- Google Drive backup es **privado** (solo vos lo ves)

## 📝 Licencia

© 2026 Prof. Eckerdt Mariano. Todos los derechos reservados.

---

**Versión:** 2.0.2 | **Tecnologías:** Vanilla JS, Firebase, Google Drive API, jsPDF
