# <a name="setting-up"></a>Einrichten

Erste Schritte mit der Azure-Kinect DK-API? Suchen Sie nicht weiter! In diesem Dokument erhalten einsatzbereit mit Zugriff auf das Gerät Sie!

Zunächst herunterladen und Installieren der [DK-API von Azure Kinect](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) aus Github.

**Inhalt**  
[Header](#Headers)  
[Suchen nach einem Kinect-Geräts](#Finding-a-Kinect-Device)  
[Starten Sie den Kameras](#Starting-the-Cameras)  
[Fehlerbehandlung](#Error-Handling)  
[Vollständige Quelle](#Full-Source)  

**Hier sind die Funktionen, die verwendet wird:**  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a>Header
Es gibt nur einen Header, die Sie benötigen, und das k4a.h ist! Stellen Sie sicher, dass der Compiler Ihrer Wahl mit SDK Lib eingerichtet ist, und schließen Sie Ordner ein. Sie benötigen auch die k4a.lib und k4a.dll-Dateien, die verknüpft wird.
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a>Suchen nach einem Kinect-Geräts

![](img/Serial.png)

Mehrere Azure Kinect DK Geräte können auf Ihrem Computer verbunden sein. Wir beginnen zunächst mit herausfindet, wie viele oder alle verbunden sind, mit der [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) Funktion. Diese Funktion sollte sofort, ohne zusätzliche Einrichtung funktionieren!

```C
uint32_t count = k4a_device_get_installed_count();
```

Wenn Sie sich es ermittelt haben, ist tatsächlich ein Gerät mit dem Computer verbunden, können Sie öffnen Sie sie in [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open). Sie können angeben, dass den Index des Geräts Sie öffnen möchten, oder Sie können nur [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) für den ersten.

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
Als bei den meisten der in der API k4a sollten beim Öffnen von etwas, Sie auch diese schließen, wenn Sie damit fertig sind! Wenn Sie heruntergefahren sind, denken Sie daran, einen Aufruf von [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).

```C
k4a_device_close(device);
```

Sobald das Gerät geöffnet ist, können wir machen einen sehr einfachen Test um sicherzustellen, dass es endlich ist. Wir lesen Seriennummer des Geräts.

```C
// Get the size of the serial number
size_t serial_size = 0;
k4a_device_get_serialnum(device, NULL, &serial_size);

// Allocate memory for the serial, then acquire it
char *serial = static_cast<char*>(malloc(serial_size));
k4a_device_get_serialnum(device, serial, &serial_size);
printf("Opened device: %s\n", serial);
free(serial);
```

## <a name="starting-the-cameras"></a>Starten Sie den Kameras

Wenn Sie das Gerät geöffnet haben, müssen Sie die Kamera mit Konfigurieren einer [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) Objekt! Kamera-Konfiguration bietet eine Reihe von Möglichkeiten, und Sie müssen die Einstellungen auswählen, die Ihrem Szenario am besten geeignet.

```C
// Configure a stream of 4096x3072 BRGA color data at 15 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_15;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

// Start the camera with the given configuration
k4a_device_start_cameras(device, &config)

// ...Camera capture and application specific code would go here...

// Shut down the camera when finished with application logic
k4a_device_stop_cameras(device);
```

Details zur Konfiguration über die __Farbe__ Kamera [sehen Sie sich in diesem Dokument]()!  
Details zur Konfiguration über die __Tiefe__ Kamera [sehen Sie sich in diesem Dokument]()!

## <a name="error-handling"></a>Fehlerbehandlung

Aus Gründen der Übersichtlichkeit und Verständlichkeit nicht wir für die Fehlerbehandlung in einigen Beispielen Inline angezeigt. Fehlerbehandlung ist jedoch immer wichtig! Viele Funktionen werden ein allgemeiner Erfolg/Fehler zurückgeben [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), oder eine spezifischere Variante mit detaillierten Informationen wie z. B. [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t). Achten Sie darauf, dass Sie die Dokumentation zu überprüfen oder Intellisense einer bestimmten Funktion, welche Fehlermeldungen möglicherweise erwarten, daraus!

Zusammen mit die Fehlertypen, es gibt auch die [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) und [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) Makros, die Sie mit ihnen verwenden können. Daher kann allein das Öffnen eines Geräts k4a, wir es folgendermaßen schützen:

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a>Vollständige Quelle

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

int main()
{
    uint32_t count = k4a_device_get_installed_count();
    if (count == 0)
    {
        printf("No k4a devices attached!\n");
        return 0;
    }

    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    if (K4A_FAILED(k4a_device_open(K4A_DEVICE_DEFAULT, &device)))
    {
        printf("Failed to open k4a device!\n");
        return 0;
    }

    // Get the size of the serial number
    size_t serial_size = 0;
    k4a_device_get_serialnum(device, NULL, &serial_size);

    // Allocate memory for the serial, then acquire it
    char* serial = static_cast<char*>(malloc(serial_size));
    k4a_device_get_serialnum(device, serial, &serial_size);
    printf("Opened device: %s\n", serial);
    free(serial);

    // Configure a stream of 4096x3072 BRGA color data at 15 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_15;
    config.color_format = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

    // Start the camera with the given configuration
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
    {
        printf("Failed to start cameras!\n");
        k4a_device_close(device);
        return 0;
    }

    // ...Camera capture and application specific code would go here...

    // Shut down the camera when finished with application logic
    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}
```

## <a name="next-lab---reading-depth-datareaddepthmd"></a>Nächste Übungseinheit - [Tiefe Daten lesen](ReadDepth.md)
