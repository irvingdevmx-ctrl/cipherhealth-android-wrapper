# CipherHealth Android (wrapper nativo)

Empaqueta la PWA CipherHealth como APK **sin permisos** (sin INTERNET) usando `WebViewAssetLoader`.
Todo el HTML/JS/CSS y las librerías van dentro de `app/src/main/assets/`.

## Publicar una versión
1. Crea los 4 secretos en GitHub → Settings → Secrets and variables → Actions:
   `KEYSTORE_BASE64`, `KEYSTORE_PASSWORD`, `KEY_ALIAS`, `KEY_PASSWORD`.
2. Sube el código y crea una etiqueta: `git tag v0.6.2 && git push origin v0.6.2`.
3. GitHub Actions compila, firma y publica el APK en **Releases** (con SHA256).

Sin secretos, cada push compila un APK de prueba (debug) descargable en Actions → Artifacts.

## Actualizar la app web
Edita `app/src/main/assets/{index.html,app.js,db.js,styles.css}`, sube `versionCode`/`versionName`
en `app/build.gradle`, añade `fastlane/metadata/android/es-MX/changelogs/<versionCode>.txt` y etiqueta.
Si agregas clases de Tailwind nuevas hay que regenerar `vendor/tailwind.css`
(`npx tailwindcss@3.4.17 -i in.css -o vendor/tailwind.css --minify` con el mismo `tailwind.config.js` de la PWA).

## Tiendas
- IzzyOnDroid: https://gitlab.com/IzzyOnDroid/repo (solicitud con el enlace al Release firmado).
- F-Droid: copia `fdroid/mx.aistudiomx.cipherhealth.yml` a un merge request en fdroiddata.
