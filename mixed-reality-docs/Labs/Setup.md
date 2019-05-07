# <a name="setting-up"></a>Настройка

Приступая к работе с Azure Kinect DK API? Вот они! В этом документе вы получите приступить к работе с доступом к устройству!

Во-первых, скачайте и установите [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) из Github.

**Содержимое**  
[Заголовки](#Headers)  
[Поиск устройств Kinect](#Finding-a-Kinect-Device)  
[Начиная с камеры](#Starting-the-Cameras)  
[Обработка ошибок](#Error-Handling)  
[Полный исходный код](#Full-Source)  

**Ниже приведены функции, которые мы будем использовать.**  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a>Заголовки
Вот k4a.h, и имеется только один заголовок, который вам! Убедитесь, что компилятор по выбору настройки с помощью пакета SDK lib и включить папки. Вам также потребуется связанному k4a.lib и k4a.dll файлы.
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a>Поиск устройств Kinect

![](img/Serial.png)

Несколько устройств Azure Kinect DK можно подключить к компьютеру! Сначала мы начнем с поиск out сколько, или если любой подключены на базе [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) функции. Эта функция должна работать без дополнительных настроек прямо сейчас!

```C
uint32_t count = k4a_device_get_installed_count();
```

После определения существует фактически устройство подключено к компьютеру, его можно открыть с помощью [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open). Можно указать индекс устройства нужно открыть, или можно просто использовать [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) для первого из них.

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
Как в большинстве других задач в k4a API при открытии, необходимо также закрыть его после завершения работы с ним! Если завершение работы, помните, что вызов [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).

```C
k4a_device_close(device);
```

Если устройство уже открыт, мы можем сделать очень простой тест, чтобы убедиться, что это все в порядке. Так что давайте считать серийный номер устройства!

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

## <a name="starting-the-cameras"></a>Начиная с камеры

После открытия устройства, вам потребуется настроить камеры с [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) объект! Камера конфигурация имеет несколько различных вариантов, и необходимо будет выбрать параметры, которые лучше всего соответствуют конкретной ситуацией.

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

Для сведения о настройке __цвет__ камеры, [извлечь этот документ]()!  
Для сведения о настройке __глубина__ камеры, [извлечь этот документ]()!

## <a name="error-handling"></a>Обработка ошибок

Ради краткости и наглядности мы больше не показывать в некоторые встроенные Примеры обработки ошибок. Тем не менее обработка ошибок всегда имеет огромное значение! Многие функции возвращает тип, общий успех или сбой [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), или более конкретного варианта с подробные сведения, такие как [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t). Не забудьте проверить документы или intellisense до конкретной функции, чтобы узнать, какие сообщения об ошибках могут ожидать от него!

А также типы ошибок, имеется также [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) и [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) макросы, которые можно использовать с ними. Поэтому вместо просто открытия устройства k4a, мы может защищаться следующим образом:

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a>Полный исходный код

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

## <a name="next-lab---reading-depth-datareaddepthmd"></a>Далее лабораторное занятие — [чтение данных глубины](ReadDepth.md)
