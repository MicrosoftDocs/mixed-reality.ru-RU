---
title: Подготовка к просмотру в DirectX
description: Описание holographic отрисовки для смешанной реальности Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, голограммы, подготовки к просмотру, 3D-графики, HolographicFrame, просмотру цикла, цикл обновления, пошаговое руководство, пример кода
ms.openlocfilehash: 6edcaf808f2d7d48f480169e5579adb8984678a0
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629038"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="17a5a-104">Подготовка к просмотру в DirectX</span><span class="sxs-lookup"><span data-stu-id="17a5a-104">Rendering in DirectX</span></span>

<span data-ttu-id="17a5a-105">Смешанная реальность Windows построена на DirectX для создания полнофункциональных, трехмерные графические возможности для пользователей.</span><span class="sxs-lookup"><span data-stu-id="17a5a-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="17a5a-106">Абстракции отрисовки находится непосредственно над DirectX и позволяет рассматривать приложения положение и ориентацию одному или нескольким наблюдателям holographic сцены, как прогнозируемые системой.</span><span class="sxs-lookup"><span data-stu-id="17a5a-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="17a5a-107">Разработчик может найдите их голограммы по отношению к каждой камеры, позволяя визуализации этих голограммы в различных Пространственные системы координат при перемещении приложения.</span><span class="sxs-lookup"><span data-stu-id="17a5a-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="17a5a-108">Обновления для текущего кадра</span><span class="sxs-lookup"><span data-stu-id="17a5a-108">Update for the current frame</span></span>

<span data-ttu-id="17a5a-109">Чтобы обновить состояние приложения для голограммы, один раз в кадре, приложение выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="17a5a-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="17a5a-110">Получить <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> из системы управления для отображения.</span><span class="sxs-lookup"><span data-stu-id="17a5a-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="17a5a-111">Обновление текущего прогноза где представления камеры будет после завершения отрисовки сцены.</span><span class="sxs-lookup"><span data-stu-id="17a5a-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="17a5a-112">Обратите внимание, что может существовать несколько камеры для holographic сцены.</span><span class="sxs-lookup"><span data-stu-id="17a5a-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="17a5a-113">Для подготовки к просмотру с представлениями holographic камеры, один раз в кадре, приложение выполняет следующие действия:</span><span class="sxs-lookup"><span data-stu-id="17a5a-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="17a5a-114">Для каждой камеры визуализации сцены для текущего кадра, используя матриц представления и проекции камеры из системы.</span><span class="sxs-lookup"><span data-stu-id="17a5a-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="17a5a-115">Создание нового кадра holographic и получение прогноза</span><span class="sxs-lookup"><span data-stu-id="17a5a-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="17a5a-116"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> содержит информацию, необходимую для приложения для обновления и отрисовки текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="17a5a-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="17a5a-117">Каждый новый пакет начала приложения, вызвав **CreateNextFrame** метод.</span><span class="sxs-lookup"><span data-stu-id="17a5a-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="17a5a-118">При вызове этого метода, прогнозы выполняются с помощью данных датчиков доступен и инкапсулированные в **CurrentPrediction** объекта.</span><span class="sxs-lookup"><span data-stu-id="17a5a-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="17a5a-119">Объект кадра необходимо использовать для каждого отображаемого кадра, так как он допустим только для обмена мгновенными во времени.</span><span class="sxs-lookup"><span data-stu-id="17a5a-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="17a5a-120">**CurrentPrediction** свойство содержит сведения, такие как положение камеры.</span><span class="sxs-lookup"><span data-stu-id="17a5a-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="17a5a-121">Данные определяется в тот момент, когда во времени, когда кадр должен быть видимым для пользователя.</span><span class="sxs-lookup"><span data-stu-id="17a5a-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="17a5a-122">Следующий код — отрывок из **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="17a5a-123">Процесс обновления камеры</span><span class="sxs-lookup"><span data-stu-id="17a5a-123">Process camera updates</span></span>

<span data-ttu-id="17a5a-124">Задние буферы можно изменить из фрейма.</span><span class="sxs-lookup"><span data-stu-id="17a5a-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="17a5a-125">Потребностями приложения для проверки на задний план буфер для каждой камеры и выпуска, а также повторно создать представления ресурсов и буферов глубины, при необходимости.</span><span class="sxs-lookup"><span data-stu-id="17a5a-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="17a5a-126">Обратите внимание, что набор создает в прогноз заслуживающим доверия списком камер, используемых в текущем фрейме.</span><span class="sxs-lookup"><span data-stu-id="17a5a-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="17a5a-127">Как правило его использовать для выполнения итерации на наборе камеры.</span><span class="sxs-lookup"><span data-stu-id="17a5a-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="17a5a-128">Из **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="17a5a-129">Из **DeviceResources::EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="17a5a-130">Получить систему координат для использования в качестве основы для подготовки к просмотру</span><span class="sxs-lookup"><span data-stu-id="17a5a-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="17a5a-131">Смешанная реальность Windows позволяет создавать различные приложения [системы координат](coordinate-systems-in-directx.md) при необходимости, например присоединенная ссылка и стационарных ссылку кадром, отслеживающие расположения в реальном мире.</span><span class="sxs-lookup"><span data-stu-id="17a5a-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="17a5a-132">Приложение затем может использовать эти системы координат делать выводы о том, где для отрисовки каждого кадра голограммы.</span><span class="sxs-lookup"><span data-stu-id="17a5a-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="17a5a-133">При запросе координаты от API, вы всегда будет передавать в <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> в котором будут эти координаты можно выразить.</span><span class="sxs-lookup"><span data-stu-id="17a5a-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="17a5a-134">Из **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="17a5a-135">Затем эти системы координат можно использовать для создания стерео представление матрицы при отрисовке содержимого в сцене.</span><span class="sxs-lookup"><span data-stu-id="17a5a-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="17a5a-136">Из **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="17a5a-137">Процесс взглядом и жест ввода</span><span class="sxs-lookup"><span data-stu-id="17a5a-137">Process gaze and gesture input</span></span>

<span data-ttu-id="17a5a-138">[Помощи](gaze-in-directx.md) и [руки](hands-and-motion-controllers-in-directx.md) входные данные не создаются на основе времени и не имеют для обновления в **StepTimer** функции.</span><span class="sxs-lookup"><span data-stu-id="17a5a-138">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="17a5a-139">Тем не менее эти входные данные — это то, что приложение должно выглядеть в каждом кадре.</span><span class="sxs-lookup"><span data-stu-id="17a5a-139">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="17a5a-140">Обработка обновлений по времени</span><span class="sxs-lookup"><span data-stu-id="17a5a-140">Process time-based updates</span></span>

<span data-ttu-id="17a5a-141">Любое приложение отрисовки в реальном времени будет нужен способ обработки обновлений на основе времени; Мы предоставляем способ это сделать в шаблоне приложения с Windows Holographic с помощью **StepTimer** реализации.</span><span class="sxs-lookup"><span data-stu-id="17a5a-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="17a5a-142">Это похоже на StepTimer, предоставленный в шаблоне приложения универсальной платформы Windows DirectX 11, поэтому если вы уже были также рассмотрены этого шаблона можно на основе знакомых.</span><span class="sxs-lookup"><span data-stu-id="17a5a-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="17a5a-143">Этот вспомогательный класс StepTimer образец может предоставить фиксированный интервал времени обновления, а также переменной временной шаг обновления, а режим по умолчанию представляет собой последовательность шагов переменных времени.</span><span class="sxs-lookup"><span data-stu-id="17a5a-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="17a5a-144">В случае holographic визуализации мы явным образом выбрали не получать слишком много, в функцию таймера.</span><span class="sxs-lookup"><span data-stu-id="17a5a-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="17a5a-145">Это обусловлено тем, можно настроить его, чтобы быть шаг фиксированное время, в противном случае его может вызываться несколько раз покадровая — или вообще не, для некоторых кадры — и наши обновления holographic данных должны быть выполнены после каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="17a5a-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="17a5a-146">Из **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="17a5a-147">Положения и поворота голограммы в вашей системе координат</span><span class="sxs-lookup"><span data-stu-id="17a5a-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="17a5a-148">Если вы работаете в одной системы координат, а шаблон выполнит все с **SpatialStationaryReferenceFrame**, этот процесс не отличается от нужной в противном случае можно в области трехмерной графики.</span><span class="sxs-lookup"><span data-stu-id="17a5a-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="17a5a-149">Здесь мы поворот куба и задайте матрицы модели относительно положения в стационарные системе координат.</span><span class="sxs-lookup"><span data-stu-id="17a5a-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="17a5a-150">Из **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-150">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="17a5a-151">**Обратите внимание на то, о расширенных сценариях:** Вращающегося куба является очень простой пример того, как разместить голограмма в рамке одна ссылка.</span><span class="sxs-lookup"><span data-stu-id="17a5a-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="17a5a-152">Существует также возможность [использовать несколько SpatialCoordinateSystems](coordinate-systems-in-directx.md) в том же Отрисованный кадр, в то же время.</span><span class="sxs-lookup"><span data-stu-id="17a5a-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="17a5a-153">Обновление данных буфера констант</span><span class="sxs-lookup"><span data-stu-id="17a5a-153">Update constant buffer data</span></span>

<span data-ttu-id="17a5a-154">Как обычно обновляются преобразования модели для содержимого.</span><span class="sxs-lookup"><span data-stu-id="17a5a-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="17a5a-155">К этому моменту будут обработаны допустимые преобразования для системы координат, которые вы будете отрисовку в.</span><span class="sxs-lookup"><span data-stu-id="17a5a-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="17a5a-156">Из **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-156">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="17a5a-157">Как насчет представления и проекции преобразования?</span><span class="sxs-lookup"><span data-stu-id="17a5a-157">What about view and projection transforms?</span></span> <span data-ttu-id="17a5a-158">Для получения наилучших результатов необходимо подождать, пока мы все почти готово для наших вызовов draw, прежде чем углубиться в эти.</span><span class="sxs-lookup"><span data-stu-id="17a5a-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="17a5a-159">Отрисовки текущего кадра</span><span class="sxs-lookup"><span data-stu-id="17a5a-159">Render the current frame</span></span>

<span data-ttu-id="17a5a-160">Отрисовки со смешанной реальностью Windows не сильно отличается от отрисовки на дисплее 2D mono, но есть некоторые различия, которые необходимо учитывать:</span><span class="sxs-lookup"><span data-stu-id="17a5a-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="17a5a-161">Прогнозы holographic кадра важны.</span><span class="sxs-lookup"><span data-stu-id="17a5a-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="17a5a-162">Чем ближе прогноза — при появлении кадре, тем лучше будет выглядеть ваш голограммы.</span><span class="sxs-lookup"><span data-stu-id="17a5a-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="17a5a-163">Смешанная реальность Windows управляет представления камеры.</span><span class="sxs-lookup"><span data-stu-id="17a5a-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="17a5a-164">Необходимые для отображения к каждой из них, так как кадр holographic позволяет представить их для вас более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="17a5a-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="17a5a-165">Стерео отрисовки рекомендуется сделать с помощью внутренне рисунка в массив целевой объект отрисовки.</span><span class="sxs-lookup"><span data-stu-id="17a5a-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="17a5a-166">В шаблоне holographic приложения используется рекомендуемый подход внутренне отрисовки в массив целевой объект отрисовки, использующего целевой объект прорисовки на **массивы Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="17a5a-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="17a5a-167">Если требуется для подготовки к просмотру без использования стерео создание экземпляров, необходимо создать два вектора RenderTargetViews (по одному для каждого глаза), каждая ссылка, один из двух срезов в **массивы Texture2DArray** предоставить приложению, из системы.</span><span class="sxs-lookup"><span data-stu-id="17a5a-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="17a5a-168">Это не рекомендуется, так как это обычно значительно медленнее, чем создание экземпляров.</span><span class="sxs-lookup"><span data-stu-id="17a5a-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="17a5a-169">Получить обновленный прогноз HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="17a5a-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="17a5a-170">Обновление прогноза кадров также эффективность стабилизацию изображения и обеспечивает более точное расположение голограммы из-за короткое время между прогноза, и если кадр является видимым для пользователя.</span><span class="sxs-lookup"><span data-stu-id="17a5a-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="17a5a-171">В идеале обновите прогнозировании кадр только что перед отрисовкой.</span><span class="sxs-lookup"><span data-stu-id="17a5a-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="17a5a-172">Визуализации для каждой камеры</span><span class="sxs-lookup"><span data-stu-id="17a5a-172">Render to each camera</span></span>

<span data-ttu-id="17a5a-173">Цикла на наборе создает камеры в прогноз и отображать для каждой камеры в этом наборе.</span><span class="sxs-lookup"><span data-stu-id="17a5a-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="17a5a-174">**Настройка вашей прохода отрисовки**</span><span class="sxs-lookup"><span data-stu-id="17a5a-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="17a5a-175">Windows Mixed Reality использует stereoscopic отрисовки для улучшения иллюзию глубины и для подготовки к просмотру stereoscopically, поэтому левый и правый отображение активны.</span><span class="sxs-lookup"><span data-stu-id="17a5a-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="17a5a-176">При визуализации stereoscopic имеется смещение между двумя экранов, мозг согласовать как фактический глубины.</span><span class="sxs-lookup"><span data-stu-id="17a5a-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="17a5a-177">Этот раздел охватывает stereoscopic визуализация с использованием создание экземпляров, с помощью кода из Windows Holographic шаблон приложения.</span><span class="sxs-lookup"><span data-stu-id="17a5a-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="17a5a-178">Каждой камеры имеет свои собственные визуализации целевой (задний буфер) и представления и проекции матрицы в holographic пространство.</span><span class="sxs-lookup"><span data-stu-id="17a5a-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="17a5a-179">Вашему приложению потребуется создать любые другие камеры ресурсы — такие как буфер глубины - на основе-камер.</span><span class="sxs-lookup"><span data-stu-id="17a5a-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="17a5a-180">В шаблоне приложения с Windows Holographic мы предоставляем объединить эти ресурсы в DX::CameraResources, вспомогательный класс.</span><span class="sxs-lookup"><span data-stu-id="17a5a-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="17a5a-181">Сначала создайте представления целевого объекта отрисовки:</span><span class="sxs-lookup"><span data-stu-id="17a5a-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="17a5a-182">Из **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-182">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="17a5a-183">**Использовать этот прогноз для получения матрицы просмотра и проекции для камеры**</span><span class="sxs-lookup"><span data-stu-id="17a5a-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="17a5a-184">Матрицы просмотра и проекции для каждого holographic камеры изменится с каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="17a5a-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="17a5a-185">Обновление данных в буфер констант для каждой holographic камеры.</span><span class="sxs-lookup"><span data-stu-id="17a5a-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="17a5a-186">Это необходимо сделать в том случае, после того как вы обновили прогноза, и вызывает перед внесением любой draw для этой камеры.</span><span class="sxs-lookup"><span data-stu-id="17a5a-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="17a5a-187">Из **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-187">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="17a5a-188">Здесь мы покажем, как матрицы они получены из поза камеры.</span><span class="sxs-lookup"><span data-stu-id="17a5a-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="17a5a-189">Во время этого процесса мы также получаем текущей области просмотра для камеры.</span><span class="sxs-lookup"><span data-stu-id="17a5a-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="17a5a-190">Обратите внимание на то, как мы предоставляем в системе координат: это же система координат, мы использовали для понимания взглядом и он аналогичен тому, мы использовали для размещения вращающегося куба.</span><span class="sxs-lookup"><span data-stu-id="17a5a-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="17a5a-191">Из **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="17a5a-192">Окно просмотра должно иметь значение каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="17a5a-192">The viewport should be set each frame.</span></span> <span data-ttu-id="17a5a-193">Шейдер вершин (по крайней мере) обычно требуется доступ к данным представления и проекции.</span><span class="sxs-lookup"><span data-stu-id="17a5a-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="17a5a-194">Из **CameraResources::AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="17a5a-195">**Отрисовки для заднего буфера камеры и зафиксируйте буфер глубины**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="17a5a-196">Рекомендуется убедиться, что **TryGetViewTransform** выполнена успешно, прежде чем использовать/проекция представления данных, поскольку если система координат не может быть найдена (например, отслеживания была прервана) приложение не может обработать с ним для этого рамка.</span><span class="sxs-lookup"><span data-stu-id="17a5a-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="17a5a-197">Шаблон вызывает только **визуализации** на вращающегося куба Если **CameraResources** класс указывает на успешное обновление.</span><span class="sxs-lookup"><span data-stu-id="17a5a-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="17a5a-198">Чтобы сохранить голограммы, где разработчик или пользователь помещает их в мире, смешанной реальности Windows включает функции для [изображения стабилизации](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="17a5a-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="17a5a-199">Изображение стабилизации позволяет скрыть задержек, присущих конвейера отрисовки, чтобы обеспечить действия лучше всего holographic, необходимые для пользователей; точку фокуса может быть указан для улучшения изображения стабилизации еще дальше, или буфер глубины могут предоставляться для вычисления оптимизированный образ стабилизации в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="17a5a-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="17a5a-200">Для получения наилучших результатов, должно предоставить буфер глубины с помощью метода <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span><span class="sxs-lookup"><span data-stu-id="17a5a-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="17a5a-201">Windows Mixed Reality затем можно использовать сведения о геометрии из буфер глубины для оптимизации стабилизацию изображения в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="17a5a-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="17a5a-202">Windows Holographic шаблон приложения фиксирует буфер глубины приложения по умолчанию, помогает оптимизировать голограмма стабильности.</span><span class="sxs-lookup"><span data-stu-id="17a5a-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="17a5a-203">Из **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-203">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="17a5a-204">Windows будет обрабатывать текстура глубины в GPU, поэтому ее можно использовать в качестве ресурса шейдера в буфер глубины.</span><span class="sxs-lookup"><span data-stu-id="17a5a-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="17a5a-205">ID3D11Texture2D, создаваемой должно быть в формате без использования типов, и он должен быть привязан как представление ресурсов шейдера.</span><span class="sxs-lookup"><span data-stu-id="17a5a-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="17a5a-206">Вот пример того, как создать текстуру глубины, которая была выделена для стабилизации образа.</span><span class="sxs-lookup"><span data-stu-id="17a5a-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="17a5a-207">Код для **создания ресурса буфера глубины для CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="17a5a-208">**Рисование holographic содержимого**</span><span class="sxs-lookup"><span data-stu-id="17a5a-208">**Draw holographic content**</span></span>

<span data-ttu-id="17a5a-209">Windows Holographic шаблон приложения отображает содержимое в стерео с помощью рекомендуемого метода рисования экземпляр geometry в массивы Texture2DArray размером 2.</span><span class="sxs-lookup"><span data-stu-id="17a5a-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="17a5a-210">Давайте взглянем на создания экземпляров часть это, и как это работает со смешанной реальностью Windows.</span><span class="sxs-lookup"><span data-stu-id="17a5a-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="17a5a-211">Из **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-211">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="17a5a-212">Каждый экземпляр получает доступ к матрицу проекция/различные представления из буфера констант.</span><span class="sxs-lookup"><span data-stu-id="17a5a-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="17a5a-213">Ниже представлена структура буфер констант, который является просто массивом 2 матриц.</span><span class="sxs-lookup"><span data-stu-id="17a5a-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="17a5a-214">Из **VertexShaderShared.hlsl**, включенная **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="17a5a-215">Индекс массива целевой объект отрисовки необходимо задать для каждого пикселя.</span><span class="sxs-lookup"><span data-stu-id="17a5a-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="17a5a-216">В приведенном ниже фрагменте сопоставляется output.viewId **SV_RenderTargetArrayIndex** семантики.</span><span class="sxs-lookup"><span data-stu-id="17a5a-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="17a5a-217">Обратите внимание на то, что это требует поддержки дополнительным компонентом Direct3D 11.3, позволяющий семантической из любой этап шейдера индекс массива целевой объект отрисовки.</span><span class="sxs-lookup"><span data-stu-id="17a5a-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="17a5a-218">Из **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-218">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="17a5a-219">Из **VertexShaderShared.hlsl**, включенная **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="17a5a-220">Если вы хотите использовать существующие экземпляры методы рисования с помощью этого метода рисунок издавать отрисовки целевого массива, что необходимо сделать всего лишь рисования дважды число экземпляров, которые обычно возникают.</span><span class="sxs-lookup"><span data-stu-id="17a5a-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="17a5a-221">В шейдере, разделите **input.instId** по 2 для получения исходного идентификатора экземпляра, какие могут быть проиндексированы в буфер (к примеру) на объект данных: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="17a5a-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="17a5a-222">Важное примечание о сохранении стерео содержимого в HoloLens</span><span class="sxs-lookup"><span data-stu-id="17a5a-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="17a5a-223">Смешанная реальность Windows поддерживает возможность задать индекс массива целевой объект отрисовки из любой этап шейдера; как правило это задача, которая может быть выполнена только в связи с особенностями семантических определен для Direct3D 11 этап шейдеров геометрии.</span><span class="sxs-lookup"><span data-stu-id="17a5a-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="17a5a-224">Здесь мы покажем полный пример того, как настроить конвейера отрисовки с только что вершин и пикселей шейдера этапы набором.</span><span class="sxs-lookup"><span data-stu-id="17a5a-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="17a5a-225">Код шейдера является, как описано выше.</span><span class="sxs-lookup"><span data-stu-id="17a5a-225">The shader code is as described above.</span></span>

<span data-ttu-id="17a5a-226">Из **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-226">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="17a5a-227">Важное примечание о подготовке к просмотру на устройствах не HoloLens</span><span class="sxs-lookup"><span data-stu-id="17a5a-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="17a5a-228">Установка индекс массива целевой объект отрисовки в шейдер вершин требует, что драйвер поддерживает дополнительный компонент Direct3D 11.3, который поддерживает HoloLens.</span><span class="sxs-lookup"><span data-stu-id="17a5a-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="17a5a-229">Приложение может иметь возможность безопасно реализовать только этот прием для подготовки к просмотру, и будут выполняться все требования для запуска в Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="17a5a-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="17a5a-230">Может оказаться так, что вы хотите использовать HoloLens эмулятор, который может быть средство разработки мощных holographic приложения — и поддержки Windows Mixed Reality иммерсивных гарнитура устройств, подключенных к ПК Windows 10.</span><span class="sxs-lookup"><span data-stu-id="17a5a-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="17a5a-231">Поддержка для подготовки к просмотру пути не HoloLens — и таким образом, для всех Windows Mixed Reality — также встроена в Windows Holographic шаблон приложения.</span><span class="sxs-lookup"><span data-stu-id="17a5a-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="17a5a-232">В коде шаблона можно найти код, чтобы разрешить приложению holographic выполняются в GPU в Компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="17a5a-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="17a5a-233">Вот как **DeviceResources** класса проверки для этой поддержки дополнительного компонента.</span><span class="sxs-lookup"><span data-stu-id="17a5a-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="17a5a-234">Из **DeviceResources::CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="17a5a-235">Для поддержки визуализации без Эта необязательная возможность, приложение должно использовать шейдер геометрии для задания рендеринга целевой индекс массива.</span><span class="sxs-lookup"><span data-stu-id="17a5a-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="17a5a-236">Этот фрагмент кода будет добавляться *после* **VSSetConstantBuffers**, и *перед* **PSSetShader** в примере кода показано в предыдущем раздел, в котором объясняется, как визуализировать стерео на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="17a5a-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="17a5a-237">Из **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-237">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="17a5a-238">**ПРИМЕЧАНИЕ HLSL**: В этом случае необходимо также загрузить слегка измененный вершинный построитель текстуры, который передает индекс массива целевой объект отрисовки в шейдер геометрии, с помощью шейдера всегда разрешено семантики, например TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="17a5a-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="17a5a-239">Шейдер геометрии не нужно выполнять никаких действий; шейдер геометрии шаблона проходит через все данные, за исключением индекс массива целевой объект отрисовки, который используется для задания SV_RenderTargetArrayIndex семантической.</span><span class="sxs-lookup"><span data-stu-id="17a5a-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="17a5a-240">Код шаблона приложения для **GeometryShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-240">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="17a5a-241">Представление</span><span class="sxs-lookup"><span data-stu-id="17a5a-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="17a5a-242">Включить holographic кадр для представления цепочки буферов</span><span class="sxs-lookup"><span data-stu-id="17a5a-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="17a5a-243">С помощью Windows Mixed Reality система управляет цепочки буферов.</span><span class="sxs-lookup"><span data-stu-id="17a5a-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="17a5a-244">Затем система управляет показа презентации кадры для каждого holographic камере, чтобы обеспечить взаимодействие с пользователями высокого качества.</span><span class="sxs-lookup"><span data-stu-id="17a5a-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="17a5a-245">Он также предоставляет обновления окна просмотра каждого кадра, для каждой камеры, для оптимизации аспекты работы системы, например стабилизацию изображения или записать смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="17a5a-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="17a5a-246">Таким образом, не вызывает holographic приложения, использующие DirectX **присутствует** на DXGI цепочка буферов.</span><span class="sxs-lookup"><span data-stu-id="17a5a-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="17a5a-247">Вместо этого использовать <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> класс для представления всех цепочек переключений кадр, когда все будет готово рисованием.</span><span class="sxs-lookup"><span data-stu-id="17a5a-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="17a5a-248">Из **DeviceResources::Present**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="17a5a-249">По умолчанию этот интерфейс API ожидает кадр и завершить перед возвращением.</span><span class="sxs-lookup"><span data-stu-id="17a5a-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="17a5a-250">Holographic приложений следует подождать предыдущего кадра, прежде чем приступать к работе на новый кадр, так как это сокращает задержку и обеспечивает лучшие результаты из прогнозов holographic кадра.</span><span class="sxs-lookup"><span data-stu-id="17a5a-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="17a5a-251">Это не жесткие правила и при наличии кадры, которые происходят дольше одного экрана обновления для подготовки к просмотру, вы можете отключить этот тип ожидания путем передачи параметра HolographicFramePresentWaitBehavior <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="17a5a-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="17a5a-252">В этом случае скорее всего используется в потоке асинхронной подготовки к просмотру для обеспечения постоянной нагрузке на GPU.</span><span class="sxs-lookup"><span data-stu-id="17a5a-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="17a5a-253">Обратите внимание, что частота обновления устройства HoloLens 60 Гц, где один кадр имеет длительность приблизительно 16 мс.</span><span class="sxs-lookup"><span data-stu-id="17a5a-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="17a5a-254">Насыщенные гарнитуры может занимать от 60 Гц до 90 Гц; При обновлении отображение 90 Гц, каждый кадр будет иметь в течение приблизительно 11 мс.</span><span class="sxs-lookup"><span data-stu-id="17a5a-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="17a5a-255">Обработки сценариев DeviceLost вместе с HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="17a5a-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="17a5a-256">Приложения DirectX 11 обычно необходимо проверить значение HRESULT, возвращенное цепочки буферов DXGI **присутствует** функции, чтобы узнать, если произошла **DeviceLost** ошибки.</span><span class="sxs-lookup"><span data-stu-id="17a5a-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="17a5a-257"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> класс обрабатывает это автоматически.</span><span class="sxs-lookup"><span data-stu-id="17a5a-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="17a5a-258">Проверьте <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> возвращается, чтобы узнать, если необходимо освободить и повторного создания устройства Direct3D и ресурсы на основе устройств.</span><span class="sxs-lookup"><span data-stu-id="17a5a-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="17a5a-259">Обратите внимание, что если устройство Direct3D было потеряно, повторно создать его, вам необходимо сообщить <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> Чтобы приступить к использованию нового устройства.</span><span class="sxs-lookup"><span data-stu-id="17a5a-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="17a5a-260">Для этого устройства будут созданы заново цепочки буферов.</span><span class="sxs-lookup"><span data-stu-id="17a5a-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="17a5a-261">Из **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="17a5a-262">После представлен кадре, можно вернуться в основной программе цикла и продолжить выполнение следующий кадр.</span><span class="sxs-lookup"><span data-stu-id="17a5a-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="17a5a-263">Гибридной графики компьютеров и приложений смешанной реальности</span><span class="sxs-lookup"><span data-stu-id="17a5a-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="17a5a-264">Windows 10 Creators Update ПК могут быть настроены с **оба** дискретных, так и встроенная графических процессоров.</span><span class="sxs-lookup"><span data-stu-id="17a5a-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="17a5a-265">С этими типами компьютеров Windows выберет гарнитуры, к которому подключен адаптер.</span><span class="sxs-lookup"><span data-stu-id="17a5a-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="17a5a-266">Приложения необходимо убедиться, что устройство DirectX, которые оно создает использует тот же адаптер.</span><span class="sxs-lookup"><span data-stu-id="17a5a-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="17a5a-267">Наиболее общие Direct3D пример кода демонстрирует создание устройства DirectX с помощью адаптера оборудования по умолчанию, который не может совпадать с той, которая использовалась для гарнитуры в гибридной системе.</span><span class="sxs-lookup"><span data-stu-id="17a5a-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="17a5a-268">Чтобы устранить все проблемы, это может вызвать проблему, используйте <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> либо из <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() или <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId().</span><span class="sxs-lookup"><span data-stu-id="17a5a-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="17a5a-269">Этот adapterId может затем использоваться для выбора DXGIAdapter вправо, с помощью IDXGIFactory4.EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="17a5a-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="17a5a-270">Из **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="17a5a-271">Код для **обновить DeviceResources::CreateDeviceResources использовать IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="17a5a-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="17a5a-272">**Гибридной графики и Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="17a5a-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="17a5a-273">С помощью Media Foundation в гибридных системах может вызвать проблемы, где видео не будет отображаться или видео текстуры поврежден.</span><span class="sxs-lookup"><span data-stu-id="17a5a-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="17a5a-274">Это может произойти, поскольку по умолчанию принимается Media Foundation поведение системы, как было сказано выше.</span><span class="sxs-lookup"><span data-stu-id="17a5a-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="17a5a-275">В некоторых случаях создание отдельных ID3D11Device является обязательным для поддержки работы с множеством потоков и правильного создания установленные флаги.</span><span class="sxs-lookup"><span data-stu-id="17a5a-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="17a5a-276">При инициализации ID3D11Device, флаг D3D11_CREATE_DEVICE_VIDEO_SUPPORT должен быть определен как часть D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="17a5a-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="17a5a-277">После создания устройства, а затем контекст вызова <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> для включения многопоточности.</span><span class="sxs-lookup"><span data-stu-id="17a5a-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="17a5a-278">Чтобы связать устройство с <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, использовать <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> функции.</span><span class="sxs-lookup"><span data-stu-id="17a5a-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="17a5a-279">Код для **связать ID3D11Device с IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="17a5a-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="17a5a-280">См. также</span><span class="sxs-lookup"><span data-stu-id="17a5a-280">See also</span></span>
* [<span data-ttu-id="17a5a-281">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="17a5a-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="17a5a-282">Использование эмулятора HoloLens</span><span class="sxs-lookup"><span data-stu-id="17a5a-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
