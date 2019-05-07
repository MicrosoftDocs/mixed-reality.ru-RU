# <a name="mixing-color-and-depth-data"></a><span data-ttu-id="f0dac-101">Смешивание цвет и глубина данных</span><span class="sxs-lookup"><span data-stu-id="f0dac-101">Mixing Color and Depth Data</span></span>

<span data-ttu-id="f0dac-102">Ресурсы, полученной от камеры цвет и глубина камера у различных форм и размеров!</span><span class="sxs-lookup"><span data-stu-id="f0dac-102">The resources you get from the color camera and the depth camera have different shapes and sizes!</span></span> <span data-ttu-id="f0dac-103">Если требуется объединить два, есть несколько вещей, которые можно сделать, чтобы выровнять их друг с другом.</span><span class="sxs-lookup"><span data-stu-id="f0dac-103">If you want to combine the two, there's a number of things you can do to align them to each other.</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="f0dac-104">**Содержимое:**</span><span class="sxs-lookup"><span data-stu-id="f0dac-104">**Contents:**</span></span>  
[<span data-ttu-id="f0dac-105">Установка и настройка</span><span class="sxs-lookup"><span data-stu-id="f0dac-105">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="f0dac-106">Получение данных</span><span class="sxs-lookup"><span data-stu-id="f0dac-106">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="f0dac-107">Преобразование данных</span><span class="sxs-lookup"><span data-stu-id="f0dac-107">Transforming Data</span></span>](#Transforming-Data)  
[<span data-ttu-id="f0dac-108">Создание сетки из облака точки</span><span class="sxs-lookup"><span data-stu-id="f0dac-108">Creating a Mesh From the Point Cloud</span></span>](#Creating-a-Mesh-From-the-Point-Cloud)  
[<span data-ttu-id="f0dac-109">Создание образа на основе глубины и цвет</span><span class="sxs-lookup"><span data-stu-id="f0dac-109">Creating an Image From Depth and Color</span></span>](#Creating-an-Image-From-Depth-and-Color)  
[<span data-ttu-id="f0dac-110">Очистка</span><span class="sxs-lookup"><span data-stu-id="f0dac-110">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="f0dac-111">Полный исходный код</span><span class="sxs-lookup"><span data-stu-id="f0dac-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="f0dac-112">**Ниже приведены функции, которые мы будем использовать.**</span><span class="sxs-lookup"><span data-stu-id="f0dac-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_calibration()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-calibration)  
[`k4a_transformation_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-create)  
[`k4a_image_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-create)  
[`k4a_transformation_depth_image_to_color_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-color-camera)  
[`k4a_transformation_color_image_to_depth_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-color-image-to-depth-camera)  
[`k4a_transformation_depth_image_to_point_cloud()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-point-cloud)  

## <a name="configuration-and-setup"></a><span data-ttu-id="f0dac-113">Установка и настройка</span><span class="sxs-lookup"><span data-stu-id="f0dac-113">Configuration and Setup</span></span>

<span data-ttu-id="f0dac-114">Хотя мы могли бы использовать практически любую конфигурацию, которую нам нужно было здесь, мы свое низких разрешениях, так как мы начну несжатых данных в файл.</span><span class="sxs-lookup"><span data-stu-id="f0dac-114">While we could use just about any configuration we wanted here, we're sticking to smaller resolutions since we'll be writing uncompressed data to file.</span></span> <span data-ttu-id="f0dac-115">Проверка документов на чтение из [камеры цвет]() и [камеры глубина]() Дополнительные сведения о конфигурациях!</span><span class="sxs-lookup"><span data-stu-id="f0dac-115">Check the documents on reading from the [color camera]() and [depth camera]() for more information about configurations!</span></span>

<span data-ttu-id="f0dac-116">Является еще одним элементом здесь `synchronized_images_only` параметр!</span><span class="sxs-lookup"><span data-stu-id="f0dac-116">One additional element here is the `synchronized_images_only` option!</span></span> <span data-ttu-id="f0dac-117">Задание значения `true` указывает, что нам нужен только записей, имеющих оба цвет <i>и</i> глубины заполнен.</span><span class="sxs-lookup"><span data-stu-id="f0dac-117">Setting it to `true` specifies that we only want captures that have both color <i>and</i> depth populated.</span></span> <span data-ttu-id="f0dac-118">Если мы не используем это, несколькими фиксирует из `k4a_device_get_capture` может либо недостает или цветных изображений.</span><span class="sxs-lookup"><span data-stu-id="f0dac-118">If we don't use this, the first few captures from `k4a_device_get_capture` may lack either depth, or color images.</span></span>

```C
// Configure the Kinect to open a stream of 512x512 wide field of view
// 16 bit depth data + 1280x720 BRGA color at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;
config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
config.synchronized_images_only = true;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="f0dac-119">Теперь, когда у нас есть наши сведения о конфигурации, необходимо настроить объект калибровки, будут переданы все наши функции преобразования!</span><span class="sxs-lookup"><span data-stu-id="f0dac-119">Now that we have our configuration information, we need to set up a calibration object that will be passed into all of our transformation functions!</span></span> <span data-ttu-id="f0dac-120">Этот объект содержит предварительно вычисленные ресурсы, используемые для преобразования координат в и из цветового пространства камеры на место и visa глубины.</span><span class="sxs-lookup"><span data-stu-id="f0dac-120">This object contains precalculated resources used for transforming coordinates to and from color camera space to depth space and visa versa.</span></span> <span data-ttu-id="f0dac-121">Что делает одной довольно прост:</span><span class="sxs-lookup"><span data-stu-id="f0dac-121">Making one is pretty simple:</span></span>

```C
k4a_calibration_t calibration;
k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration);
k4a_transformation_t transform = k4a_transformation_create(&calibration);
```

## <a name="getting-data"></a><span data-ttu-id="f0dac-122">Получение данных</span><span class="sxs-lookup"><span data-stu-id="f0dac-122">Getting Data</span></span>

<span data-ttu-id="f0dac-123">Теперь нам нужно получить образ цвет и изображение глубины!</span><span class="sxs-lookup"><span data-stu-id="f0dac-123">Now we need to acquire both a color image, and a depth image!</span></span> <span data-ttu-id="f0dac-124">Так что здесь получение один кадр и соответствующие данные из него.</span><span class="sxs-lookup"><span data-stu-id="f0dac-124">So here's grabbing a single frame and the relevant data from it.</span></span> <span data-ttu-id="f0dac-125">Если изображения поступают обратно в значение null, убедитесь, вы использовали `synchronized_images_only` в конфигурацию!</span><span class="sxs-lookup"><span data-stu-id="f0dac-125">If one of your images is coming back null, ensure you used `synchronized_images_only` in your configuration!</span></span>

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Grab image data from the Kinect
k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
int32_t color_w = k4a_image_get_width_pixels (raw_colors);
int32_t color_h = k4a_image_get_height_pixels(raw_colors);
printf("Captured depth image, %dx%d\n", depth_w, depth_h);
printf("Captured rgb image, %dx%d\n", color_w, color_h);
```

## <a name="transforming-data"></a><span data-ttu-id="f0dac-126">Преобразование данных</span><span class="sxs-lookup"><span data-stu-id="f0dac-126">Transforming Data</span></span>

<span data-ttu-id="f0dac-127">`k4a_transform_` Функции преобразует данные изображения из одного камеры пространства в другое!</span><span class="sxs-lookup"><span data-stu-id="f0dac-127">The `k4a_transform_` functions will transform your image data from one camera space to another!</span></span> <span data-ttu-id="f0dac-128">Итоговые образы будет соответствовать искажение и способы их устранения целевого пространства камеры, может помочь сопоставить цвет и глубина сведения друг с другом без труда.</span><span class="sxs-lookup"><span data-stu-id="f0dac-128">Resulting images will match the distortion and resolution of the target camera space, so you can correlate color and depth information together easily.</span></span>

<span data-ttu-id="f0dac-129">Например!</span><span class="sxs-lookup"><span data-stu-id="f0dac-129">For example!</span></span> <span data-ttu-id="f0dac-130">Довольно часто вы можете цветное изображение с камеры, соответствующий глубины для каждого цвета пикселя!</span><span class="sxs-lookup"><span data-stu-id="f0dac-130">Quite often, you might want a color image from the camera, with a corresponding depth for each color pixel!</span></span> <span data-ttu-id="f0dac-131">Для этого будет преобразовывать глубины в цветовом пространстве камеры.</span><span class="sxs-lookup"><span data-stu-id="f0dac-131">For this, you would transform the depth data into color camera space.</span></span>

<span data-ttu-id="f0dac-132">Кроме того может потребоваться создать облако трехмерной точки данных от камеры, глубины и знать, какой цвет каждой точки.</span><span class="sxs-lookup"><span data-stu-id="f0dac-132">Alternatively, you might want to create a cloud of 3D point data from the depth camera, and know what color each point is.</span></span> <span data-ttu-id="f0dac-133">Для этого мы преобразования данных глубины в облачной точке и преобразования в пространство камеры глубины цвета изображения!</span><span class="sxs-lookup"><span data-stu-id="f0dac-133">For this, we can transform the depth data into a point cloud, and transform the color image into depth camera space!</span></span> <span data-ttu-id="f0dac-134">Получить буфер значения XYZ и соответствующего буфера цветов.</span><span class="sxs-lookup"><span data-stu-id="f0dac-134">Then you'll have a buffer of XYZ values, and a corresponding buffer of colors.</span></span>

### <a name="depth-data-in-color-space"></a><span data-ttu-id="f0dac-135">Глубины в цветовом пространстве</span><span class="sxs-lookup"><span data-stu-id="f0dac-135">Depth Data in Color Space</span></span>

<span data-ttu-id="f0dac-136">Этот алгоритм преобразует глубины в соответствии с выходной цвет камеры!</span><span class="sxs-lookup"><span data-stu-id="f0dac-136">This transforms depth data to match the color camera's output!</span></span> <span data-ttu-id="f0dac-137">Получившимся буфером будет иметь значение глубины 16-разрядных систем для каждого пикселя в изображении цвет.</span><span class="sxs-lookup"><span data-stu-id="f0dac-137">The resulting buffer will have a 16 bit depth value for each pixel in the color image.</span></span>
 
```C
k4a_image_t depth_color_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_DEPTH16, 
    color_w, color_h, color_w * sizeof(uint16_t), 
    &depth_color_space))
k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

uint16_t *depth_data = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_color_space));
```

### <a name="creating-a-point-cloud"></a><span data-ttu-id="f0dac-138">Создание точки облака</span><span class="sxs-lookup"><span data-stu-id="f0dac-138">Creating a Point Cloud</span></span>

<span data-ttu-id="f0dac-139">Точка облака, также сохраняются в графических ресурсов!</span><span class="sxs-lookup"><span data-stu-id="f0dac-139">Point clouds are also stored in image resources!</span></span> <span data-ttu-id="f0dac-140">Здесь мы создадим образ формат `K4A_IMAGE_FORMAT_CUSTOM`, поскольку точка облака точно не является изображением.</span><span class="sxs-lookup"><span data-stu-id="f0dac-140">Here, we create an image of format `K4A_IMAGE_FORMAT_CUSTOM`, since a point cloud is not exactly an image.</span></span> <span data-ttu-id="f0dac-141">Каждый «» из пикселей изображение будет состоять из 3 `int16_t` значения, представляющие координаты XYZ, поэтому мы также указать правильный размер для этого.</span><span class="sxs-lookup"><span data-stu-id="f0dac-141">Each 'pixel' in the image will be composed of 3 `int16_t` values representing XYZ coordinates, so we also specify the correct size for that.</span></span>

```C
k4a_image_t point_cloud_xyz;
k4a_image_create(
    K4A_IMAGE_FORMAT_CUSTOM, 
    depth_w, depth_h, depth_w * 3 * sizeof(int16_t), 
    &point_cloud_xyz);
k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

int16_t *xyz_data = reinterpret_cast<int16_t*>(k4a_image_get_buffer(point_cloud_xyz))
```

### <a name="color-data-in-depth-space"></a><span data-ttu-id="f0dac-142">Данные о цвете в пространстве глубины</span><span class="sxs-lookup"><span data-stu-id="f0dac-142">Color Data in Depth Space</span></span>

<span data-ttu-id="f0dac-143">Этот алгоритм преобразует данных о цвете для сопоставления выходных данных от камеры, глубина!</span><span class="sxs-lookup"><span data-stu-id="f0dac-143">This transforms color data to match the output from the depth camera!</span></span> <span data-ttu-id="f0dac-144">Каждое значение цвета с получившимся буфером будет соответствовать со значением из образа глубины.</span><span class="sxs-lookup"><span data-stu-id="f0dac-144">Each color value from the resulting buffer will correspond with a value from the depth image.</span></span>

```C
k4a_image_t color_depth_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_COLOR_BGRA32, 
    depth_w, depth_h, depth_w * sizeof(uint32_t), 
    &color_depth_space);
k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

uint8_t *color_data = static_cast<uint8_t*>(k4a_image_get_buffer(color_depth_space));
```

## <a name="creating-a-mesh-from-the-point-cloud"></a><span data-ttu-id="f0dac-145">Создание сетки из облака точки</span><span class="sxs-lookup"><span data-stu-id="f0dac-145">Creating a Mesh From the Point Cloud</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="f0dac-146">Мы начнем с преобразованием данных облачной точки в формате, который немного более подробно ознакомиться.</span><span class="sxs-lookup"><span data-stu-id="f0dac-146">We'll start by converting the point cloud data into a format that's a little more familiar.</span></span> <span data-ttu-id="f0dac-147">Мы конвертировать в миллиметрах метров и переместить его в числа с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="f0dac-147">We'll convert it from millimeters to meters, and move it over to floats.</span></span>

```C
// Convert the point cloud from millimeters to meters
float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
for (int32_t i = 0; i < depth_w*depth_h; i++)
{
    vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
    vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
    vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
}
```

<span data-ttu-id="f0dac-148">Теперь мы будем совместить вверх этими вершинами с некоторой информацией лиц!</span><span class="sxs-lookup"><span data-stu-id="f0dac-148">Now we'll stitch up these vertices with some face information!</span></span> <span data-ttu-id="f0dac-149">Так как все, что выводится как сетка, это простой процесс связывания вверх углов каждой ячейки.</span><span class="sxs-lookup"><span data-stu-id="f0dac-149">Since everything is laid out as a grid, this is a straightforward process of linking up the corners of each cell.</span></span> <span data-ttu-id="f0dac-150">Только дополнительные, что мы здесь делаем пропускает любое лицо, содержащий пустые данные.</span><span class="sxs-lookup"><span data-stu-id="f0dac-150">The only additional thing we're doing here is skipping any face that contains empty data.</span></span> <span data-ttu-id="f0dac-151">Если Kinect не удалось найти данные глубины точки в облаке точки, он помещает его в < 0,0,0 >!</span><span class="sxs-lookup"><span data-stu-id="f0dac-151">If the Kinect couldn't find depth data for a point in the point cloud, it places it at <0,0,0>!</span></span> <span data-ttu-id="f0dac-152">Становится блочным довольно hedgehog, при добавлении их в список индексов.</span><span class="sxs-lookup"><span data-stu-id="f0dac-152">It turns into quite the hedgehog if you add those to the index list.</span></span>

```C
// Make mesh faces as quads across the image. Skip the 
// face if any part of its data is empty.
vector<uint32_t> indices;
for (int32_t y = 0; y < depth_h; y++)
{
    for (int32_t x = 0; x < depth_w; x++)
    {
        int32_t row1 = x +       y * depth_w;
        int32_t row2 = x + (y + 1) * depth_w;

        // If all corners of this quad have depth data
        if (xyz_data[ row1      * 3 + 1] != 0 && 
            xyz_data[(row1 + 1) * 3 + 1] != 0 && 
            xyz_data[ row2      * 3 + 1] != 0 && 
            xyz_data[(row2 + 1) * 3 + 1] != 0)
        {
            // ..then add indices for this quad
            indices.push_back(row2);
            indices.push_back(row2+1);
            indices.push_back(row1+1);
            indices.push_back(row1);
        }
    }
}
```

<span data-ttu-id="f0dac-153">Затем мы просто можно записывать полученную информацию в файл!</span><span class="sxs-lookup"><span data-stu-id="f0dac-153">Then we can just write this information to file!</span></span> <span data-ttu-id="f0dac-154">Мы не удаляя неиспользуемые цвета или позиций из-за дополнительными сложностями при создании индексов, поэтому можно просто передать в буферах, мы создали ранее.</span><span class="sxs-lookup"><span data-stu-id="f0dac-154">We aren't removing unused colors or positions due to added complexity in creating indices, so we can just pass in the buffers we've created so far.</span></span>

```C
// Write geometry data to a .PLY, and clean up
ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, indices.size() / 4, &indices[0]);
free(vertex_positions);
```

## <a name="creating-an-image-from-depth-and-color"></a><span data-ttu-id="f0dac-155">Создание образа на основе глубины и цвет</span><span class="sxs-lookup"><span data-stu-id="f0dac-155">Creating an Image From Depth and Color</span></span>

![](img/ColorandDepthSmall.png)

<span data-ttu-id="f0dac-156">С цветами это гораздо проще сделать!</span><span class="sxs-lookup"><span data-stu-id="f0dac-156">With colors, this is much easier to do!</span></span> <span data-ttu-id="f0dac-157">Здесь мы сделаем простой исчезания в черный цвет в расстояние, но удалось выполнить все виды интересных вещей, такие как обрезки out определенные диапазоны глубина или хранение глубины в альфа-канала для использования в качестве маски в средством работы с фотографиями!</span><span class="sxs-lookup"><span data-stu-id="f0dac-157">Here, we'll do a simple fade to black in the distance, but you could do all sorts of interesting things, like clipping out certain depth ranges, or storing depth in the alpha channel for use as a mask in a photo manipulation tool!</span></span>

```C
// Create an RGB image where we fade color values to black as they recede into the distance
uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
for (int32_t i = 0; i < color_w*color_h; i++)
{
    // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
    float depth = 1 - depth_data[i]/4000.0f;
    depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

    // Fade this pixel, and assign it to our new buffer
    mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
    mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
    mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
}
// Write the image to file
tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
free(mixed_colors);
```

## <a name="cleaning-up"></a><span data-ttu-id="f0dac-158">Очистка</span><span class="sxs-lookup"><span data-stu-id="f0dac-158">Cleaning Up</span></span>

<span data-ttu-id="f0dac-159">И как всегда, отпустите кнопку все, что когда вы закончите :)</span><span class="sxs-lookup"><span data-stu-id="f0dac-159">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(point_cloud_xyz);
k4a_image_release(depth_color_space);
k4a_image_release(color_depth_space);
k4a_image_release(raw_colors);
k4a_image_release(raw_depth);
k4a_capture_release(capture);
k4a_transformation_destroy(transform);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="f0dac-160">Полный исходный код</span><span class="sxs-lookup"><span data-stu-id="f0dac-160">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

#include <vector>
using namespace std;

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices);
void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 512x512 wide field of view
    // 16 bit depth data + 1280x720 BRGA color at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;
    config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
    config.synchronized_images_only = true;
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
        printf("Failed to start cameras!\n");

    // Prep data for transforming depth information to color camera space
    k4a_calibration_t calibration;
    if (K4A_FAILED(k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration)))
        printf("Failed to get calibration!\n");
    k4a_transformation_t transform = k4a_transformation_create(&calibration);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    if (K4A_FAILED(k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE)))
        printf("Failed to capture image!\n");

    // Grab image data from the Kinect
    k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
    k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
    int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
    int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
    int32_t color_w = k4a_image_get_width_pixels (raw_colors);
    int32_t color_h = k4a_image_get_height_pixels(raw_colors);
    printf("Captured depth image, %dx%d\n", depth_w, depth_h);
    printf("Captured rgb image, %dx%d\n", color_w, color_h);

    // Transform the raw depth data into color camera space
    k4a_image_t depth_color_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_DEPTH16, color_w, color_h, color_w * sizeof(uint16_t), &depth_color_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

    // Get the point cloud
    k4a_image_t point_cloud_xyz;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_CUSTOM, depth_w, depth_h, depth_w * 3 * sizeof(int16_t), &point_cloud_xyz)))
        printf("Failed to create a point cloud image resource!\n");
    k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

    // Transform the raw color data into depth camera space
    k4a_image_t color_depth_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_COLOR_BGRA32, depth_w, depth_h, depth_w * sizeof(uint32_t), &color_depth_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

    // Get access to the raw color and point cloud data.
    uint8_t  *raw_color_data = static_cast     <uint8_t  *>(k4a_image_get_buffer(raw_colors));
    uint8_t  *color_data     = static_cast     <uint8_t  *>(k4a_image_get_buffer(color_depth_space));
    uint16_t *depth_data     = reinterpret_cast<uint16_t *>(k4a_image_get_buffer(depth_color_space));
    int16_t  *xyz_data       = reinterpret_cast<int16_t  *>(k4a_image_get_buffer(point_cloud_xyz));

    // Turn the point cloud into a mesh, and write it to file!

    // Convert the point cloud from millimeters to meters
    float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
    for (int32_t i = 0; i < depth_w*depth_h; i++)
    {
        vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
        vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
        vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
    }

    // Make mesh faces as quads across the image. Skip the
    // face if any part of its data is empty.
    vector<uint32_t> indices;
    for (int32_t y = 0; y < depth_h; y++)
    {
        for (int32_t x = 0; x < depth_w; x++)
        {
            int32_t row1 = x +       y * depth_w;
            int32_t row2 = x + (y + 1) * depth_w;

            // If all corners of this quad have depth data
            if (xyz_data[ row1      * 3 + 1] != 0 && 
                xyz_data[(row1 + 1) * 3 + 1] != 0 && 
                xyz_data[ row2      * 3 + 1] != 0 && 
                xyz_data[(row2 + 1) * 3 + 1] != 0)
            {
                // ..then add indices for this quad
                indices.push_back(row2);
                indices.push_back(row2+1);
                indices.push_back(row1+1);
                indices.push_back(row1);
            }
        }
    }

    // Write geometry data to a .PLY, and clean up
    ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, static_cast<uint32_t>(indices.size()) / 4, &indices[0]);
    free(vertex_positions);
    
    // Create an RGB image where we fade color values to black as they recede into the distance
    uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
    for (int32_t i = 0; i < color_w*color_h; i++)
    {
        // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
        float depth = 1 - depth_data[i]/4000.0f;
        depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

        // Fade this pixel, and assign it to our new buffer
        mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
        mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
        mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
    }
    // Write the image to file
    tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
    free(mixed_colors);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(point_cloud_xyz);
    k4a_image_release(depth_color_space);
    k4a_image_release(color_depth_space);
    k4a_image_release(raw_colors);
    k4a_image_release(raw_depth);
    k4a_capture_release(capture);
    k4a_transformation_destroy(transform);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices)
{
    FILE *fp = nullptr;
    fopen_s(&fp, filename, "w");

    // Write the .PLY header information
    fprintf(fp, "ply\nformat ascii 1.0\n");
    fprintf(fp, "element vertex %d\nproperty float x\nproperty float y\nproperty float z\nproperty uchar red\nproperty uchar green\nproperty uchar blue\n", vertex_count);
    fprintf(fp, "element face %d\nproperty list uchar int vertex_index\n", index_quad_count);
    fprintf(fp, "end_header\n");

    // Write each vertex with color information!
    for (uint32_t i = 0; i < vertex_count; i++)
    {
        fprintf(fp, "%g %g %g %d %d %d\n", 
            vertex_positions[i*3    ],
            vertex_positions[i*3 + 1],
            vertex_positions[i*3 + 2], 
            vertex_colors_bgra[i*4 + 2], 
            vertex_colors_bgra[i*4 + 1], 
            vertex_colors_bgra[i*4    ]);
    }

    // Write faces as quads.
    for (size_t i = 0; i < index_quad_count; i++)
    {
        fprintf(fp, "4 %d %d %d %d\n", quad_indices[i*4], quad_indices[i*4 + 1], quad_indices[i*4 + 2], quad_indices[i*4 + 3]);
    }
    fclose(fp);
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width%256, (uint8_t)(width/256), height%256, (uint8_t)(height/256), file_channels*8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---accessing-the-imuusingimumd"></a><span data-ttu-id="f0dac-161">Далее лабораторное занятие — [доступ к IMU](UsingIMU.md)</span><span class="sxs-lookup"><span data-stu-id="f0dac-161">Next Lab - [Accessing the IMU](UsingIMU.md)</span></span>