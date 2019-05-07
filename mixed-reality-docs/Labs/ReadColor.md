# <a name="reading-rgb-data"></a>Lesen Sie die RGB-Daten

**Inhalt**  
[Konfigurieren des Geräts](#Configuring-the-Device)  
[Abrufen eines Frames Farbe](#Getting-a-Color-Frame)  
[Bereinigen](#Cleaning-Up)  
[Vollständige Quelle](#Full-Source)  

**Hier sind die Funktionen, die verwendet wird:**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a>Konfigurieren des Geräts

Nach dem [Öffnen eines Geräts k4a](), müssen wir die Kameras einrichten, um die Farbdaten nehmen! Es gibt viele Optionen zur Verfügung, Sie also. Hier ist ein kurzes Beispiel, wie es aussieht, um eine wirklich Grundfarbe Kamera zu starten.

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

Die `color_format` können wir sagen, wie wir unsere Farbinformationen im Image Puffer gespeichert werden soll. `K4A_IMAGE_FORMAT_COLOR_BGRA32` wäre 32 Bits pro Pixel, die als 8 Bits für Blau, Grün, Rot und Alpha gespeichert. Wir verwenden Sie dieses Format in den Beispielen aufgrund der Einfachheit halber, aber wenn Concious der Auslastung des Arbeitsspeichers werden sollen, möglicherweise andere Formate umfassendes Angebot!

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|Color-Daten werden in [Motion JPEG-Format](https://en.wikipedia.org/wiki/Motion_JPEG)|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|[YUV](https://en.wikipedia.org/wiki/YUV) Farbe Speicherplatz 4:2:0 für das Format, NV12, nur die Auflösung von 720p verfügbar.|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|[YUV](https://en.wikipedia.org/wiki/YUV) Farbe Speicherplatz 4:2:2-Format im YUY2, nur verfügbar, die Auflösung von 720p.|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|Unformatierte Farbdaten 32 Bits pro Pixel sortiert als Blau, Grün, Rot, Alpha|

Beim Schreiben Ihre eigene Konvertierung von YUV möglicherweise allzu schwer, eine schnelle, zuverlässige Bibliothek für die Konvertierung von YUV finden Sie unter [Libyuv](https://chromium.googlesource.com/libyuv/libyuv/).

Die `color_resolution` verfügt auch über mehrere Optionen zur Verfügung!

|`color_resolution`|Auflösung|Aspekt|Blickfeld| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | 1280 x 720  | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1080P` | 1920 x 1080 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1440P` | 2560 x 1440 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_2160P` | 3840 x 2160 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1536P` | 2048 x 1536 | 4:3  | 90x74.3 
|`K4A_COLOR_RESOLUTION_3072P` | 4096 x 3072 | 4:3  | 90x74.3 | Maximale Framerate 15.

Und natürlich die `camera_fps` ebenfalls.

|camera_fps||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a>Abrufen eines Frames Farbe

Abrufen von Daten für eine Farbe und eine Tiefe Frame ist ein sehr ähnlicher Prozess! Wir zunächst eine Erfassung des Geräts dann extrahieren wir das Color-Image aus, und klicken Sie dann wir die unformatierten Daten aus diesem Image abrufen.

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the color data and information from the current capture
k4a_image_t colors      = k4a_capture_get_color_image(capture);
uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
int width  = k4a_image_get_width_pixels (colors);
int height = k4a_image_get_height_pixels(colors);

// Write this capture to file
tga_write("out.tga", width, height, colorDataBGRA, 4, 3);
```

Die jetzt in gespeicherten Daten `colorDataBRGA` hängen von den wir in der Konfiguration aufgeführten Format entsprechen. Da wir aufgefordert `K4A_IMAGE_FORMAT_COLOR_BGRA32`, wir haben ein Array mit 32-Bit-Farbwerte, die in gespeicherten BGRA order!

In diesem Fall Speicherdateien TGA Farben in BGR Reihenfolge bereits! Und da unsere speichern-Funktion den alpha-Kanal mit diesen Argumenten auslassen kann, können wir einfach die Image-Daten unverändert übergeben.

## <a name="cleaning-up"></a>Bereinigen

Und wie immer, denken Sie daran, Ihre Ressourcen freigeben, wenn Sie mit ihnen fertig sind!
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a>Vollständige Quelle

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main() {
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure a stream of 1280x720 BRGA data at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the color data and information from the current capture
    k4a_image_t colors      = k4a_capture_get_color_image(capture);
    uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
    int width  = k4a_image_get_width_pixels (colors);
    int height = k4a_image_get_height_pixels(colors);
    printf("Captured RGB image, %dx%d\n", width, height);

    // Write this capture to file
    tga_write("out.tga", width, height, colors_bgra, 4, 3);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(colors);
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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a>Nächste Übungseinheit - [Kombination von Farbe und Tiefe Daten](MixDepthAndRGB.md)