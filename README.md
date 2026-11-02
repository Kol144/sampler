# Sampler

Sampler personal en español, diseñado como app web local, adaptable y preparada para empaquetarse en Android/iOS con Capacitor.

## Ejecutar en desarrollo

Necesitas Node.js 22+ y npm:

```sh
npm install
npm run dev
```

## Preparar app móvil

```sh
npm install
npx cap add android
npx cap add ios
npm run cap:sync
```

Android se compila con Android Studio/SDK. iOS requiere macOS y Xcode. La app guarda proyectos y samples en IndexedDB dentro del dispositivo; exporta proyectos `.pulso` para copias o transferencias.

Los formatos reproducibles y el tamaño máximo dependen de los decodificadores, memoria y almacenamiento del dispositivo. La herramienta estima BPM de un archivo que el navegador pueda decodificar; la tonalidad se introduce manualmente.
