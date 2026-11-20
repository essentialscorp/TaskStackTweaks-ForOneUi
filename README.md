# TaskStackTweak · 0.5.1-beta3

[Bahasa Indonesia](#bahasa-indonesia) · [English](#english) · [Español](#español)

## Bahasa Indonesia

TaskStackTweak mengubah tampilan kartu **Aplikasi terkini** di Samsung One UI Home. Gaya **Berlapis** merapatkan kartu di belakang kartu utama saat digeser. **Klasik** memberi jarak lebih lebar. Keduanya terinspirasi dari iOS. Geser untuk menutup dan ketuk untuk membuka aplikasi tetap ditangani oleh launcher Samsung.

### Perangkat dan persyaratan

| Perangkat atau konfigurasi | Dukungan beta 3 |
|---|---|
| Samsung Galaxy A36 5G | Perangkat sasaran pengujian. Keberhasilan seluruh alur pada HP fisik belum dikonfirmasi. |
| Samsung Galaxy lain dengan One UI Home | Kandidat pengujian. Kompatibilitas bergantung pada versi launcher dan tata letak kartu. Belum ada daftar model atau versi One UI yang terverifikasi. |
| Launcher pihak ketiga, HP Xiaomi, atau HP merek lain | Di luar cakupan modul. Nama preset Xiaomi HyperOS merujuk pada gaya visual untuk launcher Samsung. |
| Android dan framework | APK memerlukan Android 9 (API 28) atau lebih baru. Untuk mengubah Recent Apps, perangkat juga memerlukan framework LSPosed yang menyediakan libxposed API 102 dan scope One UI Home. Batas Android ini hanya syarat instalasi. |
| Akses root aplikasi | Tombol restart memakai perintah superuser untuk membuka ulang One UI Home pada pengguna Android aktif. Di KernelSU, akses ini bisa diberikan khusus kepada TaskStackTweak. |

### Instalasi dan percobaan pertama

1. Pasang **APK beta yang sudah ditandatangani** dari rilis proyek. File dengan nama **unsigned** disediakan untuk penerbit. Pembaruan langsung memerlukan tanda tangan yang sama dengan APK yang terpasang.
2. Di pengelola LSPosed, aktifkan **TaskStackTweak**. Di bagian scope, pilih **One UI Home** (`com.sec.android.app.launcher`). Buka aplikasi TaskStackTweak. Untuk memakai tombol restart, izinkan **TaskStackTweak** (`dev.relz.taskstacktweak`) di **KernelSU → Superuser**.
3. Buka tiga aplikasi agar ada beberapa kartu untuk dibandingkan. Pegang HP tegak, gunakan tata letak Recent Apps horizontal, lalu pilih **Terinspirasi iOS · Berlapis** di TaskStackTweak.
4. Ketuk **Coba selama 2 menit**, lalu **Mulai ulang One UI Home**. Waktu percobaan dihitung sejak tombol **Coba** ditekan. Setelah layar utama terbuka, masuk ke Aplikasi terkini dan geser perlahan. Perhatikan jarak, ukuran, dan tumpang tindih kartu. Membuka pratinjau saja belum mengaktifkan gaya.
5. Jika hasilnya cocok, kembali ke modul, ketuk **Terapkan gaya**, lalu **Mulai ulang One UI Home**. Untuk mengganti bahasa aplikasi, gunakan **Bahasa** di bagian bawah.

### Pemecahan masalah

| Gejala | Yang perlu diperiksa |
|---|---|
| APK gagal dipasang atau diperbarui | Periksa versi Android dan gunakan APK bertanda tangan. Jika ada konflik tanda tangan, cari pembaruan dari penerbit dengan sertifikat yang sama. |
| Pratinjau bergerak, tetapi tombol Coba atau Terapkan redup | Pilih gaya selain One UI bawaan. Periksa modul dan scope di LSPosed, lalu buka kembali aplikasi. HyperOS dan Kustom juga memerlukan dua nilai skala dari tata letak Tilt Stack. Jika nilai itu tidak tersedia, coba Berlapis atau Klasik. |
| Profil tersimpan, tetapi Recent Apps terlihat sama | Pastikan waktu percobaan masih tersisa, restart launcher sekali, lalu uji dalam posisi tegak. Di log LSPosed, cari `TaskStackTweak`. Untuk kedua gaya iOS, `Deck armed` berarti modul menunggu kartu yang cocok. `Deck active` berarti modul sudah menerapkan transformasi pada kartu yang dikenali. |
| Tombol restart melaporkan akses ditolak atau waktu habis | Periksa izin Superuser untuk **TaskStackTweak** di KernelSU, kembali ke modul, lalu coba sekali. Alternatif manual: buka info aplikasi **One UI Home**, pilih **Paksa berhenti** jika tersedia, lalu tekan Home. |
| Efek hilang setelah dua menit atau beberapa restart cepat | Masa uji sudah berakhir, atau pengaman melewati konfigurasi setelah tiga peluncuran cepat berturut-turut. Jika launcher stabil, simpan ulang gaya dan restart sekali. Jika launcher macet, ikuti pemulihan di bawah. |

### Pemulihan dan laporan bug

Pilih **Pulihkan One UI**, lalu **Mulai ulang One UI Home**. Jika launcher terus tertutup, nonaktifkan TaskStackTweak di LSPosed sebelum membuka ulang launcher. Jika ADB sudah aktif dan komputer sudah diotorisasi, perintah `adb uninstall dev.relz.taskstacktweak` menghapus modul beserta data aplikasinya. Hindari menghapus data One UI Home karena susunan layar utama bisa hilang.

Untuk melaporkan bug, sertakan model HP, versi Android dan One UI, **versi aplikasi One UI Home**, versi framework, gaya dan tata letak yang dipilih, langkah sampai masalah muncul, serta baris log TaskStackTweak terkait. Untuk masalah restart, tambahkan pesan yang terlihat tepat di bawah tombol.

## English

TaskStackTweak changes how **Recent apps** cards appear in Samsung One UI Home. As you swipe, **Layered** brings the cards behind the main card closer together. **Classic** spaces them farther apart. Both styles are inspired by iOS. The Samsung launcher handles tapping a card to open an app and swiping it away.

### Devices and requirements

| Device or configuration | Beta 3 support |
|---|---|
| Samsung Galaxy A36 5G | Intended test device. A successful end-to-end run on physical hardware has yet to be confirmed. |
| Other Samsung Galaxy devices running One UI Home | Candidates for testing. Compatibility depends on the launcher version and card layout. A verified model or One UI version list is still pending. |
| Third-party launchers, Xiaomi phones, or other brands | Outside the module’s scope. The Xiaomi HyperOS preset is a visual style for the Samsung launcher. |
| Android and framework | The APK requires Android 9 (API 28) or later to install. Changing Recent apps also requires an LSPosed framework that provides libxposed API 102, with One UI Home in scope. |
| App root access | The restart button uses a superuser command to reopen One UI Home for the current Android user. KernelSU lets you grant this access specifically to TaskStackTweak. |

### Installation and first trial

1. Install the **signed beta APK** from the project release. An **unsigned** APK is provided for publishers. An in-place update requires the same signing certificate as the installed APK.
2. Enable **TaskStackTweak** in your LSPosed manager. Select **One UI Home** (`com.sec.android.app.launcher`) in the module scope. Open TaskStackTweak. To use its restart button, grant **TaskStackTweak** (`dev.relz.taskstacktweak`) access in **KernelSU → Superuser**.
3. Open three apps so you can compare adjacent cards. Hold the phone in portrait, use a horizontal Recent apps layout, then select **iOS-inspired · Layered** in TaskStackTweak.
4. Tap **Try for 2 minutes**, then **Restart One UI Home**. The timer starts when you tap **Try**. Once the home screen opens, enter Recent apps and swipe slowly. Look for changes in card spacing, size, and overlap. Playing the preview alone does not activate the style.
5. To keep the style, return to the module, tap **Apply style**, then **Restart One UI Home**. To switch the app language, use **Language** at the bottom.

### Troubleshooting

| Symptom | What to check |
|---|---|
| APK installation or update fails | Check the Android version and use a signed APK. If Android reports a signature conflict, obtain an update signed by the same publisher certificate. |
| The preview moves, but Try or Apply is dimmed | Select a style other than stock One UI. Check module activation and scope in LSPosed, then reopen the app. HyperOS and Custom also need two scale values from the Tilt Stack layout. Try Layered or Classic if those values are unavailable. |
| The profile is saved, but Recent apps looks the same | Check that the trial is still running, restart the launcher once, and test in portrait. Search the LSPosed log for `TaskStackTweak`. For either iOS-inspired style, `Deck armed` means the module is waiting for compatible cards. `Deck active` means it applied a transform to a recognized card. |
| Restart reports denied access or a timeout | Check the Superuser grant for **TaskStackTweak** in KernelSU, return to the app, and retry once. For a manual restart, open **One UI Home** app info, tap **Force stop** if available, then press Home. |
| The effect disappears after two minutes or several quick restarts | The trial may have expired, or the launch guard may have skipped the configuration after three rapid starts. If the launcher is stable, save the style again and restart once. If it keeps closing, follow recovery below. |

### Recovery and bug reports

Tap **Restore One UI**, then **Restart One UI Home**. If the launcher keeps closing, disable TaskStackTweak in LSPosed before reopening the launcher. If ADB is already enabled and the computer is authorized, `adb uninstall dev.relz.taskstacktweak` removes the module and its app data. Avoid clearing One UI Home data because this can erase your home screen layout.

For a bug report, include the phone model, Android and One UI versions, **One UI Home app version**, framework version, selected style and layout, steps to reproduce, and the relevant TaskStackTweak log lines. For restart issues, include the message directly below the button.

## Español

TaskStackTweak cambia la disposición de las tarjetas de **Aplicaciones recientes** en Samsung One UI Home. Al deslizar el dedo, el estilo **Capas** acerca entre sí las tarjetas que quedan detrás de la principal. **Clásico** deja más espacio entre ellas. Ambos estilos se inspiran en iOS. El lanzador de Samsung gestiona los gestos para abrir y cerrar aplicaciones.

### Dispositivos y requisitos

| Dispositivo o configuración | Compatibilidad de la beta 3 |
|---|---|
| Samsung Galaxy A36 5G | Modelo previsto para las pruebas. Sigue pendiente la confirmación de una prueba completa en un dispositivo físico. |
| Otros Samsung Galaxy con One UI Home | Candidatos para pruebas. La compatibilidad depende de la versión del lanzador y del diseño de las tarjetas. Aún no hay una lista de modelos o versiones de One UI verificados. |
| Lanzadores de terceros, teléfonos Xiaomi u otras marcas | Fuera del alcance del módulo. El preajuste Xiaomi HyperOS es un estilo visual para el lanzador de Samsung. |
| Android y entorno | El APK requiere Android 9 (API 28) o posterior para instalarse. Modificar las aplicaciones recientes también requiere un entorno LSPosed compatible con libxposed API 102 y que One UI Home esté seleccionado en el ámbito del módulo. |
| Acceso root de la aplicación | El botón de reinicio usa un comando de superusuario para volver a abrir One UI Home para el usuario actual de Android. KernelSU permite conceder este acceso específicamente a TaskStackTweak. |

### Instalación y primera prueba

1. Instala el **APK firmado de la beta** publicado por el proyecto. El APK **unsigned** está destinado a quien publica la aplicación. Para actualizar sobre una instalación existente se necesita el mismo certificado de firma.
2. Activa **TaskStackTweak** en el gestor de LSPosed. Selecciona **One UI Home** (`com.sec.android.app.launcher`) en el ámbito del módulo. Abre TaskStackTweak. Para usar el botón de reinicio, concede acceso a **TaskStackTweak** (`dev.relz.taskstacktweak`) en **KernelSU → Superusuario**.
3. Abre tres aplicaciones para comparar tarjetas contiguas. Sujeta el teléfono en vertical, usa una vista horizontal de aplicaciones recientes y selecciona **Inspirado en iOS · Capas** en TaskStackTweak.
4. Pulsa **Probar durante 2 minutos** y después **Reiniciar One UI Home**. El plazo comienza al pulsar **Probar**. Cuando aparezca la pantalla de inicio, abre las aplicaciones recientes y desliza el dedo despacio. Observa el tamaño, la separación y la superposición de las tarjetas. Reproducir la vista previa por sí solo no activa el estilo.
5. Para conservarlo, vuelve al módulo, pulsa **Aplicar estilo** y después **Reiniciar One UI Home**. Para cambiar de idioma, pulsa **Idioma** al pie de la pantalla.

### Solución de problemas

| Síntoma | Qué comprobar |
|---|---|
| Falla la instalación o la actualización | Comprueba la versión de Android y utiliza un APK firmado. Si Android indica un conflicto de firmas, busca una actualización firmada con el mismo certificado que la aplicación instalada. |
| La vista previa se mueve, pero Probar o Aplicar están desactivados | Selecciona un estilo distinto al original de One UI. Comprueba la activación y el ámbito en LSPosed y vuelve a abrir la aplicación. HyperOS y Personalizado también requieren dos valores de escala del diseño Tilt Stack. Si no aparecen, prueba Capas o Clásico. |
| El perfil se guarda, pero las tarjetas siguen iguales | Comprueba que la prueba siga activa, reinicia el lanzador una vez y prueba en vertical. Busca `TaskStackTweak` en el registro de LSPosed. Para ambos estilos inspirados en iOS, `Deck armed` indica que el módulo espera tarjetas compatibles. `Deck active` indica que aplicó una transformación a una tarjeta reconocida. |
| El reinicio indica acceso denegado o tiempo de espera agotado | Revisa el permiso de superusuario para **TaskStackTweak** en KernelSU y vuelve a intentarlo una vez. Para reiniciar manualmente, abre la información de **One UI Home**, pulsa **Forzar detención** si está disponible y después pulsa Inicio. |
| El efecto desaparece tras dos minutos o varios reinicios rápidos | Puede haber terminado la prueba, o la protección puede haber omitido la configuración tras tres inicios rápidos. Si el lanzador es estable, guarda de nuevo el estilo y reinícialo una vez. Si se cierra repetidamente, sigue los pasos de recuperación. |

### Recuperación e informes de errores

Pulsa **Restaurar One UI** y después **Reiniciar One UI Home**. Si el lanzador se cierra repetidamente, desactiva TaskStackTweak en LSPosed antes de volver a abrirlo. Si ADB ya está habilitado y el ordenador está autorizado, el comando `adb uninstall dev.relz.taskstacktweak` elimina el módulo y sus datos. Evita borrar los datos de One UI Home porque podrías perder la disposición de tu pantalla de inicio.

Al informar de un error, incluye el modelo del teléfono, las versiones de Android y One UI, la **versión de la aplicación One UI Home**, la versión del entorno, el estilo y el diseño seleccionados, los pasos para reproducirlo y las líneas pertinentes del registro de TaskStackTweak. Si falla el reinicio, añade el mensaje que aparece debajo del botón.

## Build

| | Bahasa Indonesia | English | Español |
|---|---|---|---|
| Toolchain | JDK 17, Android SDK 37, Gradle Wrapper 9.3.1 | JDK 17, Android SDK 37, Gradle Wrapper 9.3.1 | JDK 17, Android SDK 37, Gradle Wrapper 9.3.1 |
| Linux / macOS | `./gradlew assembleDebug assembleRelease` | `./gradlew assembleDebug assembleRelease` | `./gradlew assembleDebug assembleRelease` |
| Windows | `gradlew.bat assembleDebug assembleRelease` | `gradlew.bat assembleDebug assembleRelease` | `gradlew.bat assembleDebug assembleRelease` |
| GitHub Actions | Jalankan workflow **build**. | Run the **build** workflow. | Ejecuta el flujo **build**. |
| APK publik / Public APK / APK público | Tandatangani APK rilis dengan keystore penerbit dan simpan kuncinya untuk pembaruan. | Sign the release APK with the publisher’s keystore and keep the key for updates. | Firma el APK de publicación con el almacén de claves del editor y conserva la clave para futuras actualizaciones. |

[libxposed API](https://libxposed.github.io/api/) · [KernelSU](https://kernelsu.org/)
