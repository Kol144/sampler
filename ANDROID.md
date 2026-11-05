# Sampler para Android

La app se empaqueta con Capacitor usando los archivos web incluidos en este repositorio. Los proyectos, letras y samples se guardan localmente en IndexedDB dentro de los datos privados de la app; la apariencia elegida se guarda como preferencia global del dispositivo y se aplica a todos los proyectos. Los datos permanecen al cerrar y volver a abrir la app y al instalar una actualización. Android los elimina si desinstalas la app o borras sus datos. La app solicita al sistema conservar el almacenamiento local cuando la plataforma lo permite. El APK de depuración no está firmado para distribución en Google Play.

## Generar un APK local

Instala Node.js 22 o posterior y Android Studio con Android SDK (incluidas las herramientas de plataforma y una versión compatible de Android SDK). En PowerShell, desde la carpeta raíz del repositorio:

```powershell
npm install
if (-not (Test-Path android)) { npx cap add android }
npm run build
npx cap sync android
Set-Location android
.\gradlew.bat assembleDebug
```

El APK queda en:

```text
android\app\build\outputs\apk\debug\app-debug.apk
```

En macOS/Linux, usa `./gradlew assembleDebug` desde `android`.

## Compilar desde GitHub Actions

1. Sube los cambios a GitHub.
2. Abre el repositorio y entra en **Actions**.
3. Selecciona **Build Android APK** y pulsa **Run workflow**.
4. Cuando termine correctamente, abre la ejecución y descarga el artefacto **sampler-android-debug-apk**.

El artefacto contiene `app-debug.apk` y se conserva durante 30 días. El workflow instala Node y Java en GitHub; no requiere secretos ni credenciales de firma.

## Actualizar la app después de cambiar la web

1. Modifica y sube los archivos web.
2. Para compilar localmente, ejecuta `npm run build` y `npx cap sync android` antes de Gradle.
3. Vuelve a ejecutar **Build Android APK** en GitHub Actions para obtener un APK actualizado.

La primera compilación local requiere Android Studio/SDK. La compilación de GitHub Actions configura Node y Java automáticamente; el SDK de Android lo instala Gradle en el runner.
