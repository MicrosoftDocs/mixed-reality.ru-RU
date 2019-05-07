# <a name="reading-depth-data"></a>Чтение данных глубины

Необходимо считывать глубины данные с устройства? Легко!

**Содержимое**  
[Настройка устройства](#Configuring-the-Device)  
[Доступ к глубины](#Acessing-Depth-Data)  
[Очистка](#Cleaning-Up)  
[Полный исходный код](#Full-Source)  

**Ниже приведены функции, которые мы будем использовать.**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a>Настройка устройства

После [Открытие интерфейс]() на устройстве Azure Kinect DK необходимо настроить камеры для записи данных глубины. Имеется только один элемент, вы должны знать о при настройке глубины, и что `depth_mode`!

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

Здесь `depth_mode` имеет несколько вариантов! В зависимости от контекста наше приложение мы можете запросить наши данные глубины в различных форматах.

Вы используете алгоритмы ограниченное время глубина данных? Возможно, отбирать режим 2X2BINNED, меньшее количество данных для работы с! Учитываете ли вы более о том, что гораздо out непосредственно вперед, вместо того чтобы Какова закрыть и периферии? Используйте сузить поле зрения с режимами NFOV!
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | description |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|Угловой представление (120 x 120), неполную глубины (0,25-2.21 m), решение высокого уровня данных (1024 x 1024). Имеет максимальную частоту кадров из 15.|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|Угловой представление (120 x 120), неполную глубины (0,25 — 2,88 МБ), разрешение данных низкая (512 x 512).|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|Узкий угол представления (75 x 65), дальней глубины (0,5-3.86 m), высокий уровень данных разрешением (640 x 576).|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|Угол узкое представление (75 x 65), дальней глубины (0,5-5,46 m), данных самого низкого разрешения (320 x 288).|
|`K4A_DEPTH_MODE_PASSIVE_IR`|RAW, веб-канала с камеры IR (1024 x 1024)|
||Глубина будет предоставляться за пределы указанного диапазона в зависимости от отражательную объекта.|

## <a name="acessing-depth-data"></a>Доступ к глубины

![](img/Depth.png)

Когда мы захвата кадра с устройства, мы используем `k4a_capture_get_depth_image` и `k4a_image_get_buffer` для получения данных необработанные глубины!

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

Данные о глубине предоставляется как массив целых чисел без знака 16 бит, представляющий миллиметрах от камеры. Массив будет содержать ноль, если отсутствует значение глубины для определенной точки.

В этом примере мы будем просто преобразовать данные глубины в оттенках серого изображение и сохраните как файл!

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

## <a name="cleaning-up"></a>Очистка

Не забудьте завершить работу и освободить все выделенные или вы брали! Помните, что захват кадра необходимо освободить после завершения, с ними и до получения другого кадра.

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a>Полный исходный код

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

## <a name="next-lab---reading-rgb-datareadcolormd"></a>Далее лабораторное занятие — [чтение данных RGB](ReadColor.md)