# <a name="setting-up"></a><span data-ttu-id="7e14d-101">Einrichten</span><span class="sxs-lookup"><span data-stu-id="7e14d-101">Setting Up</span></span>

<span data-ttu-id="7e14d-102">Erste Schritte mit der Azure-Kinect DK-API?</span><span class="sxs-lookup"><span data-stu-id="7e14d-102">Getting started with the Azure Kinect DK API?</span></span> <span data-ttu-id="7e14d-103">Suchen Sie nicht weiter!</span><span class="sxs-lookup"><span data-stu-id="7e14d-103">Look no further!</span></span> <span data-ttu-id="7e14d-104">In diesem Dokument erhalten einsatzbereit mit Zugriff auf das Gerät Sie!</span><span class="sxs-lookup"><span data-stu-id="7e14d-104">This document will get you up and running with access to the device!</span></span>

<span data-ttu-id="7e14d-105">Zunächst herunterladen und Installieren der [DK-API von Azure Kinect](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) aus Github.</span><span class="sxs-lookup"><span data-stu-id="7e14d-105">First, download and install the [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) from Github.</span></span>

<span data-ttu-id="7e14d-106">**Inhalt**</span><span class="sxs-lookup"><span data-stu-id="7e14d-106">**Contents**</span></span>  
[<span data-ttu-id="7e14d-107">Header</span><span class="sxs-lookup"><span data-stu-id="7e14d-107">Headers</span></span>](#Headers)  
[<span data-ttu-id="7e14d-108">Suchen nach einem Kinect-Geräts</span><span class="sxs-lookup"><span data-stu-id="7e14d-108">Finding a Kinect Device</span></span>](#Finding-a-Kinect-Device)  
[<span data-ttu-id="7e14d-109">Starten Sie den Kameras</span><span class="sxs-lookup"><span data-stu-id="7e14d-109">Starting the Cameras</span></span>](#Starting-the-Cameras)  
[<span data-ttu-id="7e14d-110">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="7e14d-110">Error Handling</span></span>](#Error-Handling)  
[<span data-ttu-id="7e14d-111">Vollständige Quelle</span><span class="sxs-lookup"><span data-stu-id="7e14d-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="7e14d-112">**Hier sind die Funktionen, die verwendet wird:**</span><span class="sxs-lookup"><span data-stu-id="7e14d-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a><span data-ttu-id="7e14d-113">Header</span><span class="sxs-lookup"><span data-stu-id="7e14d-113">Headers</span></span>
<span data-ttu-id="7e14d-114">Es gibt nur einen Header, die Sie benötigen, und das k4a.h ist!</span><span class="sxs-lookup"><span data-stu-id="7e14d-114">There's only one header that you'll need, and that's k4a.h!</span></span> <span data-ttu-id="7e14d-115">Stellen Sie sicher, dass der Compiler Ihrer Wahl mit SDK Lib eingerichtet ist, und schließen Sie Ordner ein.</span><span class="sxs-lookup"><span data-stu-id="7e14d-115">Make sure your compiler of choice is set up with the SDK's lib and include folders.</span></span> <span data-ttu-id="7e14d-116">Sie benötigen auch die k4a.lib und k4a.dll-Dateien, die verknüpft wird.</span><span class="sxs-lookup"><span data-stu-id="7e14d-116">You'll also need the k4a.lib and k4a.dll files linked up.</span></span>
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a><span data-ttu-id="7e14d-117">Suchen nach einem Kinect-Geräts</span><span class="sxs-lookup"><span data-stu-id="7e14d-117">Finding a Kinect Device</span></span>

![](img/Serial.png)

<span data-ttu-id="7e14d-118">Mehrere Azure Kinect DK Geräte können auf Ihrem Computer verbunden sein.</span><span class="sxs-lookup"><span data-stu-id="7e14d-118">Multiple Azure Kinect DK devices can be connected to your computer!</span></span> <span data-ttu-id="7e14d-119">Wir beginnen zunächst mit herausfindet, wie viele oder alle verbunden sind, mit der [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) Funktion.</span><span class="sxs-lookup"><span data-stu-id="7e14d-119">We'll first start by finding out how many, or if any are connected at all using the [`k4a_device_get_installed_count`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) function.</span></span> <span data-ttu-id="7e14d-120">Diese Funktion sollte sofort, ohne zusätzliche Einrichtung funktionieren!</span><span class="sxs-lookup"><span data-stu-id="7e14d-120">This function should work right away, without any additional setup!</span></span>

```C
uint32_t count = k4a_device_get_installed_count();
```

<span data-ttu-id="7e14d-121">Wenn Sie sich es ermittelt haben, ist tatsächlich ein Gerät mit dem Computer verbunden, können Sie öffnen Sie sie in [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span><span class="sxs-lookup"><span data-stu-id="7e14d-121">Once you've determined there is actually a device connected to the computer, you can open it using [`k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span></span> <span data-ttu-id="7e14d-122">Sie können angeben, dass den Index des Geräts Sie öffnen möchten, oder Sie können nur [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) für den ersten.</span><span class="sxs-lookup"><span data-stu-id="7e14d-122">You can provide the index of the device you want to open, or you can just use [`K4A_DEVICE_DEFAULT`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) for the first one.</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
<span data-ttu-id="7e14d-123">Als bei den meisten der in der API k4a sollten beim Öffnen von etwas, Sie auch diese schließen, wenn Sie damit fertig sind!</span><span class="sxs-lookup"><span data-stu-id="7e14d-123">As with most things in the k4a API, when you open something, you should also close it when you're finished with it!</span></span> <span data-ttu-id="7e14d-124">Wenn Sie heruntergefahren sind, denken Sie daran, einen Aufruf von [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span><span class="sxs-lookup"><span data-stu-id="7e14d-124">When you're shutting down, remember to make a call to [`k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span></span>

```C
k4a_device_close(device);
```

<span data-ttu-id="7e14d-125">Sobald das Gerät geöffnet ist, können wir machen einen sehr einfachen Test um sicherzustellen, dass es endlich ist.</span><span class="sxs-lookup"><span data-stu-id="7e14d-125">Once the device is open, we can make a really simple test to ensure it's all good.</span></span> <span data-ttu-id="7e14d-126">Wir lesen Seriennummer des Geräts.</span><span class="sxs-lookup"><span data-stu-id="7e14d-126">So let's read the device's serial number!</span></span>

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

## <a name="starting-the-cameras"></a><span data-ttu-id="7e14d-127">Starten Sie den Kameras</span><span class="sxs-lookup"><span data-stu-id="7e14d-127">Starting the Cameras</span></span>

<span data-ttu-id="7e14d-128">Wenn Sie das Gerät geöffnet haben, müssen Sie die Kamera mit Konfigurieren einer [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) Objekt!</span><span class="sxs-lookup"><span data-stu-id="7e14d-128">Once you've opened the device, you'll need to configure the camera with a [`k4a_device_configuration_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) object!</span></span> <span data-ttu-id="7e14d-129">Kamera-Konfiguration bietet eine Reihe von Möglichkeiten, und Sie müssen die Einstellungen auswählen, die Ihrem Szenario am besten geeignet.</span><span class="sxs-lookup"><span data-stu-id="7e14d-129">Camera configuration has a number of different options, and you'll need to choose the settings that best fit your own scenario.</span></span>

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

<span data-ttu-id="7e14d-130">Details zur Konfiguration über die __Farbe__ Kamera [sehen Sie sich in diesem Dokument]()!</span><span class="sxs-lookup"><span data-stu-id="7e14d-130">For configuration details about the __color__ camera, [check out this document]()!</span></span>  
<span data-ttu-id="7e14d-131">Details zur Konfiguration über die __Tiefe__ Kamera [sehen Sie sich in diesem Dokument]()!</span><span class="sxs-lookup"><span data-stu-id="7e14d-131">For configuration details about the __depth__ camera, [check out this document]()!</span></span>

## <a name="error-handling"></a><span data-ttu-id="7e14d-132">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="7e14d-132">Error Handling</span></span>

<span data-ttu-id="7e14d-133">Aus Gründen der Übersichtlichkeit und Verständlichkeit nicht wir für die Fehlerbehandlung in einigen Beispielen Inline angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7e14d-133">For the sake of brevity and clarity, we don't show error handling in some inline examples.</span></span> <span data-ttu-id="7e14d-134">Fehlerbehandlung ist jedoch immer wichtig!</span><span class="sxs-lookup"><span data-stu-id="7e14d-134">However, error handling is always important!</span></span> <span data-ttu-id="7e14d-135">Viele Funktionen werden ein allgemeiner Erfolg/Fehler zurückgeben [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), oder eine spezifischere Variante mit detaillierten Informationen wie z. B. [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span><span class="sxs-lookup"><span data-stu-id="7e14d-135">Many functions will return a general success/failure type [`k4a_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), or a more specific variant with detailed information such as [`k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span></span> <span data-ttu-id="7e14d-136">Achten Sie darauf, dass Sie die Dokumentation zu überprüfen oder Intellisense einer bestimmten Funktion, welche Fehlermeldungen möglicherweise erwarten, daraus!</span><span class="sxs-lookup"><span data-stu-id="7e14d-136">Be sure to check the docs or intellisense of a specific function to see what error messages you might expect to see from it!</span></span>

<span data-ttu-id="7e14d-137">Zusammen mit die Fehlertypen, es gibt auch die [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) und [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) Makros, die Sie mit ihnen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7e14d-137">Along with the error types, there's also the [`K4A_SUCCEEDED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) and [`K4A_FAILED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros that you can use with them.</span></span> <span data-ttu-id="7e14d-138">Daher kann allein das Öffnen eines Geräts k4a, wir es folgendermaßen schützen:</span><span class="sxs-lookup"><span data-stu-id="7e14d-138">So instead of just opening a k4a device, we might guard it like this:</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a><span data-ttu-id="7e14d-139">Vollständige Quelle</span><span class="sxs-lookup"><span data-stu-id="7e14d-139">Full Source</span></span>

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

## <a name="next-lab---reading-depth-datareaddepthmd"></a><span data-ttu-id="7e14d-140">Nächste Übungseinheit - [Tiefe Daten lesen](ReadDepth.md)</span><span class="sxs-lookup"><span data-stu-id="7e14d-140">Next Lab - [Reading Depth Data](ReadDepth.md)</span></span>
