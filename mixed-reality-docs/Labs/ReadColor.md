# <a name="reading-rgb-data"></a>Чтение данных RGB

**Содержимое**  
[Настройка устройства](#Configuring-the-Device)  
[Начало цвет рамки](#Getting-a-Color-Frame)  
[Очистка](#Cleaning-Up)  
[Полный исходный код](#Full-Source)  

**Ниже приведены функции, которые мы будем использовать.**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a>Настройка устройства

После [открытия устройства k4a](), нам нужно будет настроить камеры, чтобы скопировать данные о цвете! Поэтому мы разберем их, есть множество вариантов здесь. Ниже приведен краткий пример как выглядит для запуска веб-камеры действительно основного цвета.

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

`color_format` Позволяет нас просят способ наши сведения о цвете, сохраненного в буфере изображения! `K4A_IMAGE_FORMAT_COLOR_BGRA32` было бы 32 бита на пиксель, хранятся в виде 8 бит для синий, зеленый, красный и альфа-канала. В примерах из-за его удобства мы используем этот формат, но если вы хотите быть concious использования памяти, другие форматы, может быть превосходную варианты!

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|Цвет данных будет находиться в [формат JPEG движения](https://en.wikipedia.org/wiki/Motion_JPEG)|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|[YUV](https://en.wikipedia.org/wiki/YUV) цветовые пространства 4:2: формат 0, NV12, доступны только с разрешением 720 p.|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|[YUV](https://en.wikipedia.org/wiki/YUV) цветовые пространства 4:2:2 формате YUY2, доступны только с разрешением 720 p.|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|Необработанных данных цветового, 32 бита на пиксель, упорядочены в том, как синий, зеленый, красный, альфа-канала|

При записи собственное преобразование YUV может быть достаточно, просто быстрый и надежный библиотеки для преобразования YUV можно найти в [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).

`color_resolution` Также имеет несколько вариантов!

|`color_resolution`|Разрешение|Аспект|поле зрения| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | 1280 x 720  | 16:9 | 90 x 59
|`K4A_COLOR_RESOLUTION_1080P` | 1920 x 1080 | 16:9 | 90 x 59
|`K4A_COLOR_RESOLUTION_1440P` | 2560 x 1440 | 16:9 | 90 x 59
|`K4A_COLOR_RESOLUTION_2160P` | 3840 x 2160 | 16:9 | 90 x 59
|`K4A_COLOR_RESOLUTION_1536P` | 2048 x 1536 | 4:3  | 90x74.3 
|`K4A_COLOR_RESOLUTION_3072P` | 4096 x 3072 | 4:3  | 90x74.3 | Максимальная частота кадров 15.

И, конечно `camera_fps` также.

|camera_fps||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a>Начало цвет рамки

Получение данных для фрейма цвет и глубина кадр — это процесс, очень похожа. Сначала мы получаем сбор данных с устройства, а затем мы извлечь изображение цвет из него, а затем мы переместить необработанные данные из этого образа.

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

Данные, теперь хранится в `colorDataBRGA` зависит от формата, указанном в конфигурации. Так как мы спрашивали `K4A_IMAGE_FORMAT_COLOR_BGRA32`, у нас есть массиве, состоящем из значения цвета 32-разрядная версия, хранящиеся в BGRA order!

В этом случае TGA-файлов содержат цвета в BGR порядке уже! И поскольку нашу функцию сохранение можно пропустить альфа-канал с этими аргументами, мы просто передать данные изображения как есть!

## <a name="cleaning-up"></a>Очистка

И как всегда, помните освободить ресурсы, после завершения работы с ними!
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a>Полный исходный код

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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a>Далее лабораторное занятие — [смешивание цвет и глубина данных](MixDepthAndRGB.md)