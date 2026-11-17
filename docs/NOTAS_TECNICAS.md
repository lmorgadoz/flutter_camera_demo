# Notas técnicas

## Flujo
1. Se consulta la lista de cámaras disponibles.
2. Se selecciona preferentemente la cámara trasera (o la primera disponible).
3. `CameraPreview` muestra la imagen en tiempo real.
4. `takePicture()` genera un `XFile`.
5. Se muestra la captura.
6. `readAsBytes()` obtiene los bytes y `FileSaver` los entrega al mecanismo de guardado/descarga.

## Diferencia entre guardado local y web
En navegador, la aplicación no puede escribir arbitrariamente en una carpeta del equipo. El patrón adecuado para esta demo es iniciar una descarga y dejar que el navegador gestione el archivo. En móvil, el destino y el diálogo disponible dependen del sistema operativo y de la versión del plugin.

Para una aplicación productiva que requiera una galería privada de capturas, conviene implementar almacenamiento persistente por plataforma (por ejemplo, `path_provider` en móvil e IndexedDB en web) y una pantalla para listar, abrir y eliminar capturas.
