# <a name="setting-up"></a><span data-ttu-id="43c12-101">Настройка</span><span class="sxs-lookup"><span data-stu-id="43c12-101">Setting Up</span></span>

<span data-ttu-id="43c12-102">Приступая к работе с Azure Kinect DK API?</span><span class="sxs-lookup"><span data-stu-id="43c12-102">Getting started with the Azure Kinect DK API?</span></span> <span data-ttu-id="43c12-103">Вот они!</span><span class="sxs-lookup"><span data-stu-id="43c12-103">Look no further!</span></span> <span data-ttu-id="43c12-104">В этом документе вы получите приступить к работе с доступом к устройству!</span><span class="sxs-lookup"><span data-stu-id="43c12-104">This document will get you up and running with access to the device!</span></span>

<span data-ttu-id="43c12-105">Во-первых, скачайте и установите [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) из Github.</span><span class="sxs-lookup"><span data-stu-id="43c12-105">First, download and install the [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) from Github.</span></span>

<span data-ttu-id="43c12-106">**Содержимое**</span><span class="sxs-lookup"><span data-stu-id="43c12-106">**Contents**</span></span>  
[<span data-ttu-id="43c12-107">Заголовки</span><span class="sxs-lookup"><span data-stu-id="43c12-107">Headers</span></span>](#Headers)  
[<span data-ttu-id="43c12-108">Поиск устройств Kinect</span><span class="sxs-lookup"><span data-stu-id="43c12-108">Finding a Kinect Device</span></span>](#Finding-a-Kinect-Device)  
[<span data-ttu-id="43c12-109">Начиная с камеры</span><span class="sxs-lookup"><span data-stu-id="43c12-109">Starting the Cameras</span></span>](#Starting-the-Cameras)  
[<span data-ttu-id="43c12-110">Обработка ошибок</span><span class="sxs-lookup"><span data-stu-id="43c12-110">Error Handling</span></span>](#Error-Handling)  
[<span data-ttu-id="43c12-111">Полный исходный код</span><span class="sxs-lookup"><span data-stu-id="43c12-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="43c12-112">**Ниже приведены функции, которые мы будем использовать.**</span><span class="sxs-lookup"><span data-stu-id="43c12-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a><span data-ttu-id="43c12-113">Заголовки</span><span class="sxs-lookup"><span data-stu-id="43c12-113">Headers</span></span>
<span data-ttu-id="43c12-114">Вот k4a.h, и имеется только один заголовок, который вам!</span><span class="sxs-lookup"><span data-stu-id="43c12-114">There's only one header that you'll need, and that's k4a.h!</span></span> <span data-ttu-id="43c12-115">Убедитесь, что компилятор по выбору настройки с помощью пакета SDK lib и включить папки.</span><span class="sxs-lookup"><span data-stu-id="43c12-115">Make sure your compiler of choice is set up with the SDK's lib and include folders.</span></span> <span data-ttu-id="43c12-116">Вам также потребуется связанному k4a.lib и k4a.dll файлы.</span><span class="sxs-lookup"><span data-stu-id="43c12-116">You'll also need the k4a.lib and k4a.dll files linked up.</span></span>
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a><span data-ttu-id="43c12-117">Поиск устройств Kinect</span><span class="sxs-lookup"><span data-stu-id="43c12-117">Finding a Kinect Device</span></span>

![](img/Serial.png)

<span data-ttu-id="43c12-118">Несколько устройств Azure Kinect DK можно подключить к компьютеру!</span><span class="sxs-lookup"><span data-stu-id="43c12-118">Multiple Azure Kinect DK devices can be connected to your computer!</span></span> <span data-ttu-id="43c12-119">Сначала мы начнем с поиск out сколько, или если любой подключены на базе [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) функции.</span><span class="sxs-lookup"><span data-stu-id="43c12-119">We'll first start by finding out how many, or if any are connected at all using the [`k4a_device_get_installed_count`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) function.</span></span> <span data-ttu-id="43c12-120">Эта функция должна работать без дополнительных настроек прямо сейчас!</span><span class="sxs-lookup"><span data-stu-id="43c12-120">This function should work right away, without any additional setup!</span></span>

```C
uint32_t count = k4a_device_get_installed_count();
```

<span data-ttu-id="43c12-121">После определения существует фактически устройство подключено к компьютеру, его можно открыть с помощью [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span><span class="sxs-lookup"><span data-stu-id="43c12-121">Once you've determined there is actually a device connected to the computer, you can open it using [`k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span></span> <span data-ttu-id="43c12-122">Можно указать индекс устройства нужно открыть, или можно просто использовать [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) для первого из них.</span><span class="sxs-lookup"><span data-stu-id="43c12-122">You can provide the index of the device you want to open, or you can just use [`K4A_DEVICE_DEFAULT`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) for the first one.</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
<span data-ttu-id="43c12-123">Как в большинстве других задач в k4a API при открытии, необходимо также закрыть его после завершения работы с ним!</span><span class="sxs-lookup"><span data-stu-id="43c12-123">As with most things in the k4a API, when you open something, you should also close it when you're finished with it!</span></span> <span data-ttu-id="43c12-124">Если завершение работы, помните, что вызов [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span><span class="sxs-lookup"><span data-stu-id="43c12-124">When you're shutting down, remember to make a call to [`k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span></span>

```C
k4a_device_close(device);
```

<span data-ttu-id="43c12-125">Если устройство уже открыт, мы можем сделать очень простой тест, чтобы убедиться, что это все в порядке.</span><span class="sxs-lookup"><span data-stu-id="43c12-125">Once the device is open, we can make a really simple test to ensure it's all good.</span></span> <span data-ttu-id="43c12-126">Так что давайте считать серийный номер устройства!</span><span class="sxs-lookup"><span data-stu-id="43c12-126">So let's read the device's serial number!</span></span>

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

## <a name="starting-the-cameras"></a><span data-ttu-id="43c12-127">Начиная с камеры</span><span class="sxs-lookup"><span data-stu-id="43c12-127">Starting the Cameras</span></span>

<span data-ttu-id="43c12-128">После открытия устройства, вам потребуется настроить камеры с [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) объект!</span><span class="sxs-lookup"><span data-stu-id="43c12-128">Once you've opened the device, you'll need to configure the camera with a [`k4a_device_configuration_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) object!</span></span> <span data-ttu-id="43c12-129">Камера конфигурация имеет несколько различных вариантов, и необходимо будет выбрать параметры, которые лучше всего соответствуют конкретной ситуацией.</span><span class="sxs-lookup"><span data-stu-id="43c12-129">Camera configuration has a number of different options, and you'll need to choose the settings that best fit your own scenario.</span></span>

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

<span data-ttu-id="43c12-130">Для сведения о настройке __цвет__ камеры, [извлечь этот документ]()!</span><span class="sxs-lookup"><span data-stu-id="43c12-130">For configuration details about the __color__ camera, [check out this document]()!</span></span>  
<span data-ttu-id="43c12-131">Для сведения о настройке __глубина__ камеры, [извлечь этот документ]()!</span><span class="sxs-lookup"><span data-stu-id="43c12-131">For configuration details about the __depth__ camera, [check out this document]()!</span></span>

## <a name="error-handling"></a><span data-ttu-id="43c12-132">Обработка ошибок</span><span class="sxs-lookup"><span data-stu-id="43c12-132">Error Handling</span></span>

<span data-ttu-id="43c12-133">Ради краткости и наглядности мы больше не показывать в некоторые встроенные Примеры обработки ошибок.</span><span class="sxs-lookup"><span data-stu-id="43c12-133">For the sake of brevity and clarity, we don't show error handling in some inline examples.</span></span> <span data-ttu-id="43c12-134">Тем не менее обработка ошибок всегда имеет огромное значение!</span><span class="sxs-lookup"><span data-stu-id="43c12-134">However, error handling is always important!</span></span> <span data-ttu-id="43c12-135">Многие функции возвращает тип, общий успех или сбой [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), или более конкретного варианта с подробные сведения, такие как [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span><span class="sxs-lookup"><span data-stu-id="43c12-135">Many functions will return a general success/failure type [`k4a_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), or a more specific variant with detailed information such as [`k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span></span> <span data-ttu-id="43c12-136">Не забудьте проверить документы или intellisense до конкретной функции, чтобы узнать, какие сообщения об ошибках могут ожидать от него!</span><span class="sxs-lookup"><span data-stu-id="43c12-136">Be sure to check the docs or intellisense of a specific function to see what error messages you might expect to see from it!</span></span>

<span data-ttu-id="43c12-137">А также типы ошибок, имеется также [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) и [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) макросы, которые можно использовать с ними.</span><span class="sxs-lookup"><span data-stu-id="43c12-137">Along with the error types, there's also the [`K4A_SUCCEEDED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) and [`K4A_FAILED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros that you can use with them.</span></span> <span data-ttu-id="43c12-138">Поэтому вместо просто открытия устройства k4a, мы может защищаться следующим образом:</span><span class="sxs-lookup"><span data-stu-id="43c12-138">So instead of just opening a k4a device, we might guard it like this:</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a><span data-ttu-id="43c12-139">Полный исходный код</span><span class="sxs-lookup"><span data-stu-id="43c12-139">Full Source</span></span>

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

## <a name="next-lab---reading-depth-datareaddepthmd"></a><span data-ttu-id="43c12-140">Далее лабораторное занятие — [чтение данных глубины](ReadDepth.md)</span><span class="sxs-lookup"><span data-stu-id="43c12-140">Next Lab - [Reading Depth Data](ReadDepth.md)</span></span>
