# Retroreel-App
# ✅ Checklist Retroreel con Buildah + Podman

## 🛠️ 1. Preparar el entorno
- [ ] Asegúrate de tener `Dockerfile`, `nginx.conf` y la carpeta `html/` en el mismo directorio.
- [ ] Asegúrate de que `nginx.conf` esté correctamente estructurado, sin errores de directivas (`server` va dentro de `http`).

## 🔧 2. Construir la imagen
```bash
buildah bud -t retroreel-streaming:latest -f Dockerfile .
```

## 🗑️ 3. Eliminar contenedor anterior (si existe)
```bash
podman rm -f retroreel-web
```

## 🚀 4. Lanzar el nuevo contenedor
```bash
podman run -d -p 8080:80 --name retroreel-web retroreel-streaming:latest
```

## 👀 5. Verificar que el contenedor está activo
```bash
podman ps
```

## 🌍 6. Comprobar en el navegador
- Abre tu navegador en: [http://localhost:8080](http://localhost:8080) (o la IP del nodo master:8080).
- Si no ves los nuevos cambios, sigue el siguiente paso.

## 🔄 7. Vaciar caché del navegador
- [ ] Pulsa `Ctrl+F5` o usa el modo incógnito para evitar ver versiones cacheadas.

## 🧪 8. Si no se ven los cambios:
- [ ] Asegúrate de que los archivos modificados están realmente en el `html/`.
- [ ] Reconstruye la imagen y repite desde el paso 2.
