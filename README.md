# Flutter Camera Demo

Aplicación mínima para probar la cámara, capturar una fotografía, previsualizarla y guardarla/descargarla como JPG.

## Requisitos
- Flutter instalado y configurado (`flutter doctor`).
- Cámara disponible y permisos autorizados.
- Para web: navegador compatible y ejecutar en `localhost` o desplegar con HTTPS.

## Ejecutar
Desde esta carpeta:

```bash
flutter pub get
flutter run
```

Para elegir un dispositivo:

```bash
flutter devices
flutter run -d <id-del-dispositivo>
```

Para probar en navegador:

```bash
flutter run -d chrome
```

## Comportamiento del guardado
- **Web:** el botón Guardar captura solicita la descarga del JPG al navegador. El usuario elige dónde conservarlo según la configuración del navegador.
- **Android/iOS:** se utiliza `file_saver` para entregar el JPG al mecanismo de guardado disponible en el dispositivo. El destino exacto depende de la plataforma y de su versión; no es una galería persistente administrada por esta app.
- La previsualización de la foto se mantiene en memoria mientras la pantalla siga abierta. No se crea una galería interna ni una base de datos de capturas.

## Permisos y configuración
El plugin `camera` solicita el acceso cuando corresponde. Si la plataforma exige una declaración explícita, verifica:

- **Android:** permiso `android.permission.CAMERA` en `android/app/src/main/AndroidManifest.xml`.
- **iOS:** clave `NSCameraUsageDescription` en `ios/Runner/Info.plist`, con una explicación como `La aplicación necesita la cámara para tomar fotografías de prueba.`
- **Web:** autoriza el permiso de cámara en el navegador. La cámara normalmente requiere contexto seguro: `localhost` o HTTPS.

Si el proyecto no tiene todavía las carpetas de plataforma, créalas primero con Flutter:

```bash
flutter create .
flutter pub get
flutter run
```

## Dependencias
- `camera`: vista previa y captura.
- `file_saver`: guardar/descargar los bytes de la imagen en plataformas compatibles.

## Alcance de esta demo
Es una base para probar la cámara en una app de clase o prototipo. No sube imágenes a un servidor ni las sincroniza entre dispositivos.
