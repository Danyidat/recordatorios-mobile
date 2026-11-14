# Mis Recordatorios — Flutter Android
Aplicación móvil Flutter para gestionar recordatorios mediante la API NestJS.

## Requisitos Windows
Instalar Flutter estable, Android Studio, Android SDK y aceptar licencias con `flutter doctor --android-licenses`. Clonar este repositorio y ejecutar `flutter create --platforms=android --project-name mis_recordatorios .` una sola vez para generar la carpeta nativa Android si aún no existe; luego `flutter pub get` y abrir la carpeta del proyecto en Android Studio.

## Ejecutar
```powershell
flutter pub get
flutter run
```
En Android Studio, seleccionar un emulador o dispositivo USB con depuración habilitada. La configuración inicial del emulador es `http://10.0.2.2:3000`; en celular físico usar `http://IP-DE-LA-LAPTOP:3000`. Para USB: `adb reverse tcp:3000 tcp:3000` y configurar `http://127.0.0.1:3000`.

## Configuración de API
En la app abrir Configuración del servidor, guardar la URL y probar `GET /health`. La URL queda guardada localmente. Iniciar NestJS en el puerto 3000 y permitir conexiones locales en el firewall de Windows cuando se use Wi-Fi.

## Datos y APK
Los recordatorios se guardan en PostgreSQL a través de NestJS; Flutter nunca se conecta directamente a PostgreSQL. El workflow manual **Flutter Android CI** analiza, prueba, compila APK debug y publica un artefacto con retención de un día. Descargarlo desde Actions > ejecución > Artifacts.
