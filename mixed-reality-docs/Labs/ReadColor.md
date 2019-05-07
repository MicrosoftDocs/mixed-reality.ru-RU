# <a name="reading-rgb-data"></a><span data-ttu-id="a6c55-101">Чтение данных RGB</span><span class="sxs-lookup"><span data-stu-id="a6c55-101">Reading RGB Data</span></span>

<span data-ttu-id="a6c55-102">**Содержимое**</span><span class="sxs-lookup"><span data-stu-id="a6c55-102">**Contents**</span></span>  
[<span data-ttu-id="a6c55-103">Настройка устройства</span><span class="sxs-lookup"><span data-stu-id="a6c55-103">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="a6c55-104">Начало цвет рамки</span><span class="sxs-lookup"><span data-stu-id="a6c55-104">Getting a Color Frame</span></span>](#Getting-a-Color-Frame)  
[<span data-ttu-id="a6c55-105">Очистка</span><span class="sxs-lookup"><span data-stu-id="a6c55-105">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="a6c55-106">Полный исходный код</span><span class="sxs-lookup"><span data-stu-id="a6c55-106">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="a6c55-107">**Ниже приведены функции, которые мы будем использовать.**</span><span class="sxs-lookup"><span data-stu-id="a6c55-107">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a><span data-ttu-id="a6c55-108">Настройка устройства</span><span class="sxs-lookup"><span data-stu-id="a6c55-108">Configuring the Device</span></span>

<span data-ttu-id="a6c55-109">После [открытия устройства k4a](), нам нужно будет настроить камеры, чтобы скопировать данные о цвете!</span><span class="sxs-lookup"><span data-stu-id="a6c55-109">After [opening a k4a device](), we'll need to set up the cameras to grab color data!</span></span> <span data-ttu-id="a6c55-110">Поэтому мы разберем их, есть множество вариантов здесь.</span><span class="sxs-lookup"><span data-stu-id="a6c55-110">There's a lot of options here as well, so we'll go through them.</span></span> <span data-ttu-id="a6c55-111">Ниже приведен краткий пример как выглядит для запуска веб-камеры действительно основного цвета.</span><span class="sxs-lookup"><span data-stu-id="a6c55-111">Here's a quick example of what it looks like to start up a really basic color camera.</span></span>

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="a6c55-112">`color_format` Позволяет нас просят способ наши сведения о цвете, сохраненного в буфере изображения!</span><span class="sxs-lookup"><span data-stu-id="a6c55-112">The `color_format` allows us to say how we want our color information stored in the image buffer!</span></span> <span data-ttu-id="a6c55-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` было бы 32 бита на пиксель, хранятся в виде 8 бит для синий, зеленый, красный и альфа-канала.</span><span class="sxs-lookup"><span data-stu-id="a6c55-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` would be 32 bits per pixel, stored as 8 bits each for Blue, Green, Red, and Alpha.</span></span> <span data-ttu-id="a6c55-114">В примерах из-за его удобства мы используем этот формат, но если вы хотите быть concious использования памяти, другие форматы, может быть превосходную варианты!</span><span class="sxs-lookup"><span data-stu-id="a6c55-114">We use this format in the examples due to its convenience, but if you want to be concious of memory usage, other formats may be superior choices!</span></span>

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|<span data-ttu-id="a6c55-115">Цвет данных будет находиться в [формат JPEG движения](https://en.wikipedia.org/wiki/Motion_JPEG)</span><span class="sxs-lookup"><span data-stu-id="a6c55-115">Color data will be in [Motion JPEG format](https://en.wikipedia.org/wiki/Motion_JPEG)</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|<span data-ttu-id="a6c55-116">[YUV](https://en.wikipedia.org/wiki/YUV) цветовые пространства 4:2: формат 0, NV12, доступны только с разрешением 720 p.</span><span class="sxs-lookup"><span data-stu-id="a6c55-116">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:0 format, NV12, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|<span data-ttu-id="a6c55-117">[YUV](https://en.wikipedia.org/wiki/YUV) цветовые пространства 4:2:2 формате YUY2, доступны только с разрешением 720 p.</span><span class="sxs-lookup"><span data-stu-id="a6c55-117">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:2 format, YUY2, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|<span data-ttu-id="a6c55-118">Необработанных данных цветового, 32 бита на пиксель, упорядочены в том, как синий, зеленый, красный, альфа-канала</span><span class="sxs-lookup"><span data-stu-id="a6c55-118">Raw color data, 32 bits per pixel, ordered as Blue, Green, Red, Alpha</span></span>|

<span data-ttu-id="a6c55-119">При записи собственное преобразование YUV может быть достаточно, просто быстрый и надежный библиотеки для преобразования YUV можно найти в [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span><span class="sxs-lookup"><span data-stu-id="a6c55-119">While writing your own YUV conversion may be easy enough, a fast, robust library for YUV conversion can be found at [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span></span>

<span data-ttu-id="a6c55-120">`color_resolution` Также имеет несколько вариантов!</span><span class="sxs-lookup"><span data-stu-id="a6c55-120">The `color_resolution` also has a couple of options!</span></span>

|`color_resolution`|<span data-ttu-id="a6c55-121">Разрешение</span><span class="sxs-lookup"><span data-stu-id="a6c55-121">resolution</span></span>|<span data-ttu-id="a6c55-122">Аспект</span><span class="sxs-lookup"><span data-stu-id="a6c55-122">aspect</span></span>|<span data-ttu-id="a6c55-123">поле зрения</span><span class="sxs-lookup"><span data-stu-id="a6c55-123">field of view</span></span>| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | <span data-ttu-id="a6c55-124">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="a6c55-124">1280 x 720</span></span>  | <span data-ttu-id="a6c55-125">16:9</span><span class="sxs-lookup"><span data-stu-id="a6c55-125">16:9</span></span> | <span data-ttu-id="a6c55-126">90 x 59</span><span class="sxs-lookup"><span data-stu-id="a6c55-126">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1080P` | <span data-ttu-id="a6c55-127">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="a6c55-127">1920 x 1080</span></span> | <span data-ttu-id="a6c55-128">16:9</span><span class="sxs-lookup"><span data-stu-id="a6c55-128">16:9</span></span> | <span data-ttu-id="a6c55-129">90 x 59</span><span class="sxs-lookup"><span data-stu-id="a6c55-129">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1440P` | <span data-ttu-id="a6c55-130">2560 x 1440</span><span class="sxs-lookup"><span data-stu-id="a6c55-130">2560 x 1440</span></span> | <span data-ttu-id="a6c55-131">16:9</span><span class="sxs-lookup"><span data-stu-id="a6c55-131">16:9</span></span> | <span data-ttu-id="a6c55-132">90 x 59</span><span class="sxs-lookup"><span data-stu-id="a6c55-132">90x59</span></span>
|`K4A_COLOR_RESOLUTION_2160P` | <span data-ttu-id="a6c55-133">3840 x 2160</span><span class="sxs-lookup"><span data-stu-id="a6c55-133">3840 x 2160</span></span> | <span data-ttu-id="a6c55-134">16:9</span><span class="sxs-lookup"><span data-stu-id="a6c55-134">16:9</span></span> | <span data-ttu-id="a6c55-135">90 x 59</span><span class="sxs-lookup"><span data-stu-id="a6c55-135">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1536P` | <span data-ttu-id="a6c55-136">2048 x 1536</span><span class="sxs-lookup"><span data-stu-id="a6c55-136">2048 x 1536</span></span> | <span data-ttu-id="a6c55-137">4:3</span><span class="sxs-lookup"><span data-stu-id="a6c55-137">4:3</span></span>  | <span data-ttu-id="a6c55-138">90x74.3</span><span class="sxs-lookup"><span data-stu-id="a6c55-138">90x74.3</span></span> 
|`K4A_COLOR_RESOLUTION_3072P` | <span data-ttu-id="a6c55-139">4096 x 3072</span><span class="sxs-lookup"><span data-stu-id="a6c55-139">4096 x 3072</span></span> | <span data-ttu-id="a6c55-140">4:3</span><span class="sxs-lookup"><span data-stu-id="a6c55-140">4:3</span></span>  | <span data-ttu-id="a6c55-141">90x74.3</span><span class="sxs-lookup"><span data-stu-id="a6c55-141">90x74.3</span></span> | <span data-ttu-id="a6c55-142">Максимальная частота кадров 15.</span><span class="sxs-lookup"><span data-stu-id="a6c55-142">Max framerate 15.</span></span>

<span data-ttu-id="a6c55-143">И, конечно `camera_fps` также.</span><span class="sxs-lookup"><span data-stu-id="a6c55-143">And of course, the `camera_fps` as well.</span></span>

|<span data-ttu-id="a6c55-144">camera_fps</span><span class="sxs-lookup"><span data-stu-id="a6c55-144">camera_fps</span></span>||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a><span data-ttu-id="a6c55-145">Начало цвет рамки</span><span class="sxs-lookup"><span data-stu-id="a6c55-145">Getting a Color Frame</span></span>

<span data-ttu-id="a6c55-146">Получение данных для фрейма цвет и глубина кадр — это процесс, очень похожа.</span><span class="sxs-lookup"><span data-stu-id="a6c55-146">Getting data for a color frame and a depth frame is a very similar process!</span></span> <span data-ttu-id="a6c55-147">Сначала мы получаем сбор данных с устройства, а затем мы извлечь изображение цвет из него, а затем мы переместить необработанные данные из этого образа.</span><span class="sxs-lookup"><span data-stu-id="a6c55-147">First we get a capture from the device, then we extract the color image from it, and then we pull the raw data out of that image.</span></span>

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

<span data-ttu-id="a6c55-148">Данные, теперь хранится в `colorDataBRGA` зависит от формата, указанном в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a6c55-148">The data now stored in `colorDataBRGA` is dependant on the format we indicated in configuration.</span></span> <span data-ttu-id="a6c55-149">Так как мы спрашивали `K4A_IMAGE_FORMAT_COLOR_BGRA32`, у нас есть массиве, состоящем из значения цвета 32-разрядная версия, хранящиеся в BGRA order!</span><span class="sxs-lookup"><span data-stu-id="a6c55-149">Since we asked for `K4A_IMAGE_FORMAT_COLOR_BGRA32`, we have an array full of 32 bit color values stored in BGRA order!</span></span>

<span data-ttu-id="a6c55-150">В этом случае TGA-файлов содержат цвета в BGR порядке уже!</span><span class="sxs-lookup"><span data-stu-id="a6c55-150">In this case, .tga files store colors in BGR order already!</span></span> <span data-ttu-id="a6c55-151">И поскольку нашу функцию сохранение можно пропустить альфа-канал с этими аргументами, мы просто передать данные изображения как есть!</span><span class="sxs-lookup"><span data-stu-id="a6c55-151">And since our saving function can skip the alpha channel with these arguments, we can just pass the image data as is!</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="a6c55-152">Очистка</span><span class="sxs-lookup"><span data-stu-id="a6c55-152">Cleaning Up</span></span>

<span data-ttu-id="a6c55-153">И как всегда, помните освободить ресурсы, после завершения работы с ними!</span><span class="sxs-lookup"><span data-stu-id="a6c55-153">And as always, remember to release your resources when you're done with them!</span></span>
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a><span data-ttu-id="a6c55-154">Полный исходный код</span><span class="sxs-lookup"><span data-stu-id="a6c55-154">Full Source</span></span>

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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a><span data-ttu-id="a6c55-155">Далее лабораторное занятие — [смешивание цвет и глубина данных](MixDepthAndRGB.md)</span><span class="sxs-lookup"><span data-stu-id="a6c55-155">Next Lab - [Mixing Color and Depth Data](MixDepthAndRGB.md)</span></span>