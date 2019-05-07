# <a name="accessing-the-imu"></a><span data-ttu-id="1117d-101">Zugreifen auf die IMU</span><span class="sxs-lookup"><span data-stu-id="1117d-101">Accessing the IMU</span></span>

<span data-ttu-id="1117d-102">Azure Kinect DK enthält ein eingestellten Messung-Einheit (IMU)!</span><span class="sxs-lookup"><span data-stu-id="1117d-102">Azure Kinect DK contains an Inertial Measurement Unit (IMU)!</span></span> <span data-ttu-id="1117d-103">Dies kann helfen, um zu bestimmen, während der Übertragung und die Ausrichtung des Geräts während der Erfassung nützlich sein.</span><span class="sxs-lookup"><span data-stu-id="1117d-103">This can be useful for helping to determine motion and orientation of the device during capture.</span></span> <span data-ttu-id="1117d-104">Insbesondere dann, wenn Ihr Gerät nicht stationär ist!</span><span class="sxs-lookup"><span data-stu-id="1117d-104">Especially if you device isn't stationary!</span></span>

<span data-ttu-id="1117d-105">**Inhalt:**</span><span class="sxs-lookup"><span data-stu-id="1117d-105">**Contents:**</span></span>  
[<span data-ttu-id="1117d-106">Konfiguration und Einrichtung</span><span class="sxs-lookup"><span data-stu-id="1117d-106">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="1117d-107">Abrufen von Daten</span><span class="sxs-lookup"><span data-stu-id="1117d-107">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="1117d-108">Bereinigen</span><span class="sxs-lookup"><span data-stu-id="1117d-108">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="1117d-109">Vollständige Quelle</span><span class="sxs-lookup"><span data-stu-id="1117d-109">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="1117d-110">**Hier sind die Funktionen, die verwendet wird:**</span><span class="sxs-lookup"><span data-stu-id="1117d-110">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-imu)  
[`k4a_device_stop_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-imu)  
[`k4a_device_get_imu_sample()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-imu-sample)  

## <a name="configuration-and-setup"></a><span data-ttu-id="1117d-111">Konfiguration und Einrichtung</span><span class="sxs-lookup"><span data-stu-id="1117d-111">Configuration and Setup</span></span>

<span data-ttu-id="1117d-112">Konfiguration hier ist recht einfach!</span><span class="sxs-lookup"><span data-stu-id="1117d-112">Configuration here is pretty simple!</span></span> <span data-ttu-id="1117d-113">Es sind keine Elemente, die Sie angeben müssen die Stichprobenentnahme, um die Arbeit, aber Sie müssen in der Gerätekonfiguration für IMU Aufrufen `k4a_device_start_cameras` vor dem sie arbeiten!</span><span class="sxs-lookup"><span data-stu-id="1117d-113">There are no items you need to specify the in the device configuration for IMU sampling to work, but you will need to call `k4a_device_start_cameras` before it'll work!</span></span> <span data-ttu-id="1117d-114">Stattdessen erstellen Sie einen Aufruf von `k4a_device_start_imu` nach dem Starten der Kameras.</span><span class="sxs-lookup"><span data-stu-id="1117d-114">Instead, you'll make a call to `k4a_device_start_imu` after starting the cameras.</span></span>

```C
// Cameras need to be 'started' even if all we want is the IMU
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
k4a_device_start_cameras(device, &config);

// Start up the IMU sensors
k4a_device_start_imu(device);
```

## <a name="getting-data"></a><span data-ttu-id="1117d-115">Abrufen von Daten</span><span class="sxs-lookup"><span data-stu-id="1117d-115">Getting Data</span></span>

<span data-ttu-id="1117d-116">![IMU app Beispielbild](img/IMU.png "sieht, was wir als Beispiel erstellen.")</span><span class="sxs-lookup"><span data-stu-id="1117d-116">![IMU sample app image](img/IMU.png "Here's what we'll build as an example!")</span></span>

<span data-ttu-id="1117d-117">Die IMU stellt die Daten mit einer Rate von 1.6 kHz bereit!</span><span class="sxs-lookup"><span data-stu-id="1117d-117">The IMU provides data at a rate of 1.6kHz!</span></span> <span data-ttu-id="1117d-118">Das ist eine Menge von Daten, und dies bedeutet, dass wenn Sie nur suchen sich jedes Mal ein Frame Tiefe/Farbe verfügbar ist, müssen Sie wahrscheinlich eine Warteschlange von IMU Beispiele warten, bis Sie!</span><span class="sxs-lookup"><span data-stu-id="1117d-118">That's a lot of data, and this means that if you're only looking at it each time a depth/color frame is available, you'll likely have quite a queue of IMU samples waiting for you!</span></span> <span data-ttu-id="1117d-119">Beachten Sie, dass diese Daten nicht Ausrichtung oder Position, sondern vielmehr ein Maß für die erzwingen, die derzeit auf das Gerät angewendet.</span><span class="sxs-lookup"><span data-stu-id="1117d-119">Note that this data is not an orientation or position, but rather, a measure of the force currently applied to the device.</span></span>

<span data-ttu-id="1117d-120">Wir ziehen Sie ein Beispiel für und aus der Warteschlange entfernt werden, durch den Aufruf `k4a_device_get_imu_sample` mit einem Timeout von 0 Millisekunden.</span><span class="sxs-lookup"><span data-stu-id="1117d-120">We can grab a sample and remove it from the queue by calling `k4a_device_get_imu_sample` with a timeout of 0 milliseconds.</span></span> <span data-ttu-id="1117d-121">Kehren sie `K4A_WAIT_RESULT_SUCCEEDED` solange sie ein Beispiel zur Verfügung hat.</span><span class="sxs-lookup"><span data-stu-id="1117d-121">It'll return `K4A_WAIT_RESULT_SUCCEEDED` as long as it has a sample available!</span></span>

<span data-ttu-id="1117d-122">Hier ist ein Beispiel für alle Beispiele, die sich derzeit in der Warteschlange summieren und zum Drucken des Durchschnitts.</span><span class="sxs-lookup"><span data-stu-id="1117d-122">Here's an example of summing all the samples currently in the queue, and printing the average.</span></span> 

```C
k4a_float3_t gyro_sum  = {0};
k4a_float3_t acc_sum   = {0};
int32_t      sum_count = 0;

// Sum the current queue of IMU samples
k4a_imu_sample_t sample;
while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
{
    gyro_sum.xyz = { 
        gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
        gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
        gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
    acc_sum.xyz = { 
        acc_sum.xyz.x + sample.acc_sample.xyz.x,  
        acc_sum.xyz.y + sample.acc_sample.xyz.y,  
        acc_sum.xyz.z + sample.acc_sample.xyz.z };
    sum_count += 1;
    samples   += 1;
}

// If we got any samples, print out their average!
if (sum_count > 0)
{
    k4a_float3_t gyro_avg = {
        gyro_sum.xyz.x / sum_count,
        gyro_sum.xyz.y / sum_count,
        gyro_sum.xyz.z / sum_count };
    k4a_float3_t acc_avg = {
        acc_sum.xyz.x / sum_count,
        acc_sum.xyz.y / sum_count,
        acc_sum.xyz.z / sum_count };

    printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
    printf("<%6.2f, %6.2f, %6.2f>", acc_avg.xyz.x, acc_avg.xyz.y, acc_avg.xyz.z);

    // Write backspaces so we'll overwrite this line next time
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
}
```

## <a name="cleaning-up"></a><span data-ttu-id="1117d-123">Bereinigen</span><span class="sxs-lookup"><span data-stu-id="1117d-123">Cleaning Up</span></span>

<span data-ttu-id="1117d-124">Und wie immer alles, was nach Abschluss :)</span><span class="sxs-lookup"><span data-stu-id="1117d-124">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_device_stop_imu(device);
k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="1117d-125">Vollständige Quelle</span><span class="sxs-lookup"><span data-stu-id="1117d-125">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Cameras need to be 'started' even if all we want is the IMU
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    k4a_device_start_cameras(device, &config);

    // Start up the IMU sensors
    k4a_device_start_imu(device);

    // Display 10,000 samples as fast as they arrive
    printf("Sampling 10,000 times.\n");
    printf("Gyroscope radians/s:       Accelerometer meters/s^2:\n");
    int32_t samples = 0;
    while (samples < 10000)
    {
        k4a_float3_t gyro_sum  = {0};
        k4a_float3_t accel_sum = {0};
        int32_t      sum_count = 0;

        // Sum the current queue of IMU samples
        k4a_imu_sample_t sample;
        while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
        {
            gyro_sum.xyz = { 
                gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
                gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
                gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
            accel_sum.xyz = { 
                accel_sum.xyz.x + sample.acc_sample.xyz.x,  
                accel_sum.xyz.y + sample.acc_sample.xyz.y,  
                accel_sum.xyz.z + sample.acc_sample.xyz.z };
            sum_count += 1;
            samples   += 1;
        }

        // If we got any samples this loop, print out their average!
        if (sum_count > 0)
        {
            k4a_float3_t gyro_avg = {
                gyro_sum.xyz.x / sum_count,
                gyro_sum.xyz.y / sum_count,
                gyro_sum.xyz.z / sum_count };
            k4a_float3_t accel_avg = {
                accel_sum.xyz.x / sum_count,
                accel_sum.xyz.y / sum_count,
                accel_sum.xyz.z / sum_count };

            printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
            printf("<%6.2f, %6.2f, %6.2f>", accel_avg.xyz.x, accel_avg.xyz.y, accel_avg.xyz.z);

            // Write backspaces so we'll overwrite this line next time
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
        }
    }
    printf("\nShutting down.\n");

    // Release all allocated resources, and shut down the Kinect
    k4a_device_stop_imu(device);
    k4a_device_stop_cameras(device);
    k4a_device_close(device);
}
```