# Mis Recordatorios — Flutter Android
Aplicación móvil Flutter para gestionar recordatorios mediante la API NestJS.

## Requisitos Windows
Instalar Flutter estable, Android Studio, Android SDK y aceptar licencias con `flutter doctor --android-licenses`. Clonar este repositorio y ejecutar `flutter create --overwrite --platforms=android --project-name mis_recordatorios .` para generar el scaffolding nativo Android completo y el Gradle Wrapper, conservando el código Dart; luego `flutter pub get` y abrir la carpeta en Android Studio.

## Ejecutar
```powershell
flutter pub get
flutter run
```
Seleccionar emulador o dispositivo USB con depuración habilitada. Emulador: `http://10.0.2.2:3000`; celular físico: `http://IP-DE-LA-LAPTOP:3000`. Para USB: `adb reverse tcp:3000 tcp:3000` y configurar `http://127.0.0.1:3000`.

## Configuración de API
En la app abrir Configuración del servidor, guardar la URL y probar `GET /health`. La URL queda guardada localmente. Iniciar NestJS en el puerto 3000 y permitir conexiones locales en el firewall de Windows cuando se use Wi-Fi.

## Datos y APK
Los recordatorios se guardan en PostgreSQL a través de NestJS; Flutter nunca se conecta directamente a PostgreSQL. El workflow manual **Flutter Android CI** genera scaffolding Android, analiza, prueba, compila APK debug y publica un artefacto con retención de un día. Descargar desde Actions > ejecución > Artifacts.
