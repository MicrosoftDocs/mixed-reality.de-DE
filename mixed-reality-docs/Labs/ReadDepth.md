# <a name="reading-depth-data"></a>Lesen von Daten für Tiefe

Müssen Sie die Tiefe Daten vom Gerät gelesen? Es ist ganz einfach!

**Inhalt**  
[Konfigurieren des Geräts](#Configuring-the-Device)  
[Zugreifen auf ausführliche Daten](#Acessing-Depth-Data)  
[Bereinigen](#Cleaning-Up)  
[Vollständige Quelle](#Full-Source)  

**Hier sind die Funktionen, die verwendet wird:**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a>Konfigurieren des Geräts

Nach dem [öffnen eine Schnittstelle]() an das Gerät Azure Kinect DK, müssen Sie so konfigurieren Sie die Kamera für das Erfassen von Daten der Tiefe. Es ist nur ein Element, die Sie nicht unbedingt zu kennen, wenn die Tiefe, konfigurieren und das ist die `depth_mode`!

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

Hier die `depth_mode` verfügt über einige Optionen. Je nach Kontext der Anwendung können wir unsere Tiefe Daten in verschiedenen Formaten anfordern.

Führen Sie zeitlich beschränkt Algorithmen für die Tiefe Daten aus? Wählen Sie vielleicht einen 2X2BINNED-Modus gibt es also weniger Daten verarbeiten! Ist Sie wichtig mehr Informationen zu den Neuheiten weit direkt out ahead, anstatt was schließen ist und in der Peripherie? Verwenden Sie eine schmale Sichtfeld, mit der Modi NFOV!
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | description |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|Große Spitze Ansicht (120 x 120), flache Tiefe (0,25-2.21 m), hohe Auflösung (1024 x 1024). Hat eine maximale Framerate von 15.|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|Große Spitze Ansicht (120 x 120), flache Tiefe (0,25-2,88 m), Daten mit niedriger Auflösung (512 x 512).|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|Schmale Winkel anzeigen (75 x 65) weit Tiefe (0,5-3.86 m), hohe Auflösung (640 x 576).|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|Schmale Winkel anzeigen (75 x 65) weit Tiefe (0,5-5,46 m), Daten mit niedriger Auflösung (320 x 288).|
|`K4A_DEPTH_MODE_PASSIVE_IR`|RAW-feed von der IR-Kamera (1024 x 1024)|
||Tiefe werden außerhalb des angegebenen Bereichs je nach Objekt Reflexionsvermögen bereitgestellt.|

## <a name="acessing-depth-data"></a>Zugreifen auf ausführliche Daten

![](img/Depth.png)

Wenn wir einen Frame vom Gerät erfassen, können wir `k4a_capture_get_depth_image` und `k4a_image_get_buffer` zum Abrufen der Tiefe der unformatierten Daten!

```C
// Capture a frame
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the depth data and information from the current capture
k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
int32_t width  = k4a_image_get_width_pixels (depth_image);
int32_t height = k4a_image_get_height_pixels(depth_image);
```

Ausführliche Informationen dient als ein Array von unsignierten 16-Bit-Ganzzahlen, Millimeter von der Kamera darstellt. Das Array hält eine 0 (null) fest, wenn der Wert für die Tiefe nicht für ein bestimmtes Pixel vorhanden ist.

In diesem Beispiel wir nur die Tiefe Daten in ein Graustufe Image konvertiert, und speichern Sie sie in der Datei!

```C
// Write this depth capture to an image file

// Allocate memory for an 8-bit grayscale image
uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

// Convert each depth value to a shade of gray!
for (int32_t i = 0; i < width*height; i++)
{
    // Make a gray from the depth, white up close, black at 3 meters in the distance
    float depth_gray = 1-(depth_buffer[i] / 3000.0f);
    // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
    depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

    file_color[i] = static_cast<uint8_t>(depth_gray * 255);
}
tga_write("outDepth.tga", width, height, file_color, 1, 3);
free(file_color);
```

## <a name="cleaning-up"></a>Bereinigen

Denken Sie daran, Herunterfahren und freigeben, alles, was Sie nahm zugeordnet, oder haben! Denken Sie daran, dass ein Frame erfasst freigegeben werden soll, nachdem Sie mit ihnen und vor dem Abrufen von einem anderen Frame fertig sind.

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a>Vollständige Quelle

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 1024x1024 wide FOV at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_5;
    config.depth_mode = K4A_DEPTH_MODE_WFOV_UNBINNED;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the depth data and information from the current capture
    k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
    uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
    int32_t width  = k4a_image_get_width_pixels (depth_image);
    int32_t height = k4a_image_get_height_pixels(depth_image);
    printf("Captured depth image, %dx%d\n", width, height);

    // Write this depth capture to an image file

    // Allocate memory for an 8-bit grayscale image
    uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

    // Convert each depth value to a shade of gray!
    for (int32_t i = 0; i < width*height; i++)
    {
        // Make a gray from the depth, white up close, black at 3 meters in the distance
        float depth_gray = 1-(depth_buffer[i] / 3000.0f);
        // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
        depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

        file_color[i] = static_cast<uint8_t>(depth_gray * 255);
    }
    tga_write("outDepth.tga", width, height, file_color, 1, 3);
    free(file_color);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(depth_image);
    k4a_capture_release(capture);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width % 256, (uint8_t)(width / 256), height % 256, (uint8_t)(height / 256), file_channels * 8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---reading-rgb-datareadcolormd"></a>Nächste Übungseinheit - [RGB-Daten lesen](ReadColor.md)