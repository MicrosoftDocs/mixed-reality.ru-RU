---
title: Подготовка к просмотру в DirectX
description: Описание более holographic для Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, голограммы, отрисовка, трехмерная графика, Холографикфраме, цикл отрисовки, цикл обновления, пошаговое руководство, пример кода, Direct3D
ms.openlocfilehash: 6b2e2dca9115d7093e94019d5ed91201f6ee3424
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375981"
---
# <a name="rendering-in-directx"></a>Подготовка к просмотру в DirectX

Windows Mixed Reality построена на основе DirectX для создания полнофункциональных трехмерных графических интерфейсов для пользователей. Абстракция отрисовки располагается непосредственно над DirectX и позволяет приложению определить положение и ориентацию одного или нескольких наблюдателей holographic-сцены, прогнозируемой системой. После этого разработчик может размещать свои голограммы относительно каждой камеры, позволяя приложению визуализировать эти голограммы в различных пространственных системах координат по мере перемещения пользователя.

Примечание. в этом пошаговом руководстве описывается обработка в Direct3D 11 более Holographic. Шаблон приложения Windows Mixed Reality с Direct3D 12 также предоставляется с расширением шаблонов приложений смешанной реальности.

## <a name="update-for-the-current-frame"></a>Обновление текущего кадра

Чтобы обновить состояние приложения для голограмм, один раз для каждого кадра приложение будет выполнять следующие действия:
* Получение <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> из системы управления отображением.
* Обновите сцену, используя текущий прогноз, где будет отображаться представление камеры после завершения подготовки к просмотру. Обратите внимание, что для «holographic» сцены может существовать более одной камеры.

Для отображения в представлениях с Камером holographic, один раз для каждого кадра, приложение будет выполнять следующие действия:
* Для каждой камеры Визуализируйте сцену для текущего кадра, используя матрицы представления камеры и проекции из системы.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Создание нового пакета holographic и получение его прогноза

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">Холографикфраме</a> содержит сведения, необходимые приложению для обновления и отрисовки текущего кадра. Приложение начинает каждый новый кадр, вызывая метод **креатенекстфраме** . При вызове этого метода прогнозы выполняются с использованием последних доступных данных датчика и инкапсулированы в объект **куррентпредиктион** .

Для каждого отображаемого кадра должен использоваться новый объект Frame, так как он действителен только для мгновенного выполнения. Свойство **куррентпредиктион** содержит такие сведения, как расположение камеры. Данные выделяются на конкретный момент времени, когда фрейм должен быть видимым для пользователя.

Следующий код взят из **аппмаин:: Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Обработка обновлений камеры

Задние буферы могут меняться от кадра к кадру. Приложению необходимо проверить задний буфер для каждой камеры, а также освободить и повторно создать представления ресурсов и буферы глубины по мере необходимости. Обратите внимание, что набор элементов прогноза является полномочным списком камер, используемых в текущем кадре. Обычно этот список используется для итерации по набору камер.

Из **аппмаин:: Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Из **DeviceResources:: енсурекамераресаурцес**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Получение системы координат для использования в качестве основания для подготовки к просмотру

Windows Mixed Reality позволяет вашему приложению создавать различные [системы координат](coordinate-systems-in-directx.md) по мере необходимости, например присоединенный фрейм ссылки и стационарный опорный фрейм, которые отслеживанием расположения в физическом мире. Приложение может использовать эти системы координат в качестве причины, по которой следует визуализировать голограммы каждого кадра. При запросе координат из API вы всегда будете передавать <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">спатиалкурдинатесистем</a> , внутри которых должны выражаться эти координаты.

Из **аппмаин:: Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Эти системы координат можно затем использовать для создания матрицы стерео View при отрисовке содержимого в сцене.

Из **камераресаурцес:: упдатевиевпрожектионбуффер**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Обработка взгляда и ввод с жестом

Ввод с помощью [взгляда](gaze-in-directx.md) и [руки](hands-and-motion-controllers-in-directx.md) не основан на времени, поэтому их не нужно обновлять в функции **стептимер** . Однако эти входные данные — это то, что приложению нужно взглянуть на каждый кадр.

### <a name="process-time-based-updates"></a>Обработка обновлений на основе времени

Любому приложению отрисовки в режиме реального времени потребуется какой-то способ обработки обновлений на основе времени; Мы предоставляем способ сделать это в шаблоне приложения Windows holographic с помощью реализации **стептимер** . Это похоже на Стептимер, предоставляемый в шаблоне приложения UWP DirectX 11, поэтому, если вы уже рассматривали этот шаблон, вы должны быть знакомы со знакомым заземлением. Этот пример вспомогательного класса Стептимер способен предоставлять фиксированные обновления времени, а также выполнять изменения в переменных времени, а режим по умолчанию — с переменным шагом.

В случае с holographic, мы выбрали не слишком много времени на функцию таймера. Это связано с тем, что вы можете настроить его как фиксированный шаг времени. в этом случае он может вызываться более одного раза для каждого кадра, а не вообще — для некоторых кадров, а наши обновления данных — по одному на кадр.


Из **аппмаин:: Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Размещение и поворот голограмм в системе координат

Если вы работаете в одной системе координат, так как шаблон работает с **спатиалстатионариреференцефраме**, этот процесс не отличается от того, что используется в трехмерной графике. Здесь мы вращающим куб и устанавливаем матрицу модели относительно положения в стационарной системе координат.

Из **спиннингкуберендерер:: Update**:

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

**Примечание о расширенных сценариях:** Вращающийся куб — это очень простой пример того, как разместить голограмму в пределах одного опорного кадра. Кроме того, можно одновременно [использовать несколько спатиалкурдинатесистемс](coordinate-systems-in-directx.md) в одном и том же подготовленном фрейме.

### <a name="update-constant-buffer-data"></a>Обновление данных буфера констант

Преобразования модели для содержимого обновляются обычным образом. К этому моменту вы получите вычисленные Допустимые преобразования для системы координат, в которой будет выполняться отрисовка.

Из **спиннингкуберендерер:: Update**:

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

Как насчет преобразований представлений и проекций? Для достижения лучших результатов мы хотим подождать, пока мы почти готовы к вызовам Draw, прежде чем они будут получены.

## <a name="render-the-current-frame"></a>Отобразить текущий кадр

Отрисовка в Windows Mixed Reality не намного отличается от отрисовки на 2D Mono, но есть некоторые различия, которые необходимо учитывать:
* Важны прогнозы с Holographic. Чем ближе прогноз к представлению вашей рамки, тем лучше будет выглядеть голограмма.
* Windows Mixed Reality управляет представлениями камеры. Необходимо выполнить рендеринг для каждого из них, так как в holographic кадр будет демонстрироваться позже.
* Рекомендуется выполнить отрисовку стерео с помощью экземпляра Drawing в массиве целевых объектов прорисовки. Шаблон holographic App использует Рекомендуемый подход экземпляра Drawing к целевому массиву прорисовки, который использует представление целевого объекта отрисовки в **Texture2DArray**.
* Если вы хотите подготовиться к просмотру без использования стереосистемы, необходимо создать два Рендертаржетвиевс, не являющихся массивами (один для каждого взгляда), каждый из которых ссылается на один из двух срезов в **Texture2DArray** , предоставленных приложению из системы. Это не рекомендуется, так как обычно значительно медленнее, чем использование создания экземпляров.

### <a name="get-an-updated-holographicframe-prediction"></a>Получение обновленного прогноза Холографикфраме

Обновление прогноза кадров повышает эффективность стабилизации изображений и обеспечивает более точное позиционирование голограмм из-за более короткого промежутка времени между прогнозом и отображением кадра для пользователя. В идеале перед отрисовкой обновите прогнозирование кадров.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Подготовка к просмотру на каждой камере

Цикл по набору камер в прогнозе и отрисовка на каждой камере в этом наборе.

**Настройка этапа подготовки к просмотру**

Windows Mixed Reality использует стереоскопикную визуализацию для улучшения иллюзии глубины и визуализации стереоскопикалли, поэтому активно и правое отображение активны. При отрисовке стереоскопик между двумя дисплеями имеется смещение, которое мозг может согласовать как фактическую глубину. В этом разделе описывается визуализация стереоскопик с помощью создания экземпляров с помощью кода из шаблона приложения Windows Holographic.

У каждой камеры есть собственный целевой буфер рендеринга (заднего буфера), а также матрицы просмотра и проекции в Holographic. Приложению потребуется создать любые другие ресурсы на основе камеры, такие как буфер глубины, для каждой камеры. В шаблоне приложения Windows holographic мы предоставляем вспомогательный класс для объединения этих ресурсов в DX:: Камераресаурцес. Начните с настройки представлений целевого объекта прорисовки:

Из **аппмаин:: Render**:

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

**Использование прогноза для получения матриц представления и проекции для камеры**

Матрицы представления и проекции для каждой из этих камер Изменятся с каждым кадром. Обновите данные в буфере констант для каждой камеры Holographic. Сделайте это после обновления прогноза и перед выполнением вызовов рисования для этой камеры.

Из **аппмаин:: Render**:

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

Здесь мы покажем, как можно получить матрицы от самой камеры. В ходе этого процесса мы также получаем текущее окно просмотра для камеры. Обратите внимание на то, как мы предоставляем систему координат: это та же система координат, которая использовалась для понимания взгляда, и это то же самое, что мы использовали для размещения вращающегося куба.


Из **камераресаурцес:: упдатевиевпрожектионбуффер**:

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

Окно просмотра должно быть задано для каждого кадра. Как правило, шейдеру вершин (по крайней мере) необходим доступ к данным представления или проекции.


Из **камераресаурцес:: аттачвиевпрожектионбуффер**:

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

**Подготавливается к просмотру в фоновом буфере камеры и зафиксируйте буфер глубины**:

Прежде чем пытаться использовать данные представления или проекции, рекомендуется проверить, что **трижетвиевтрансформ** успешно выполнен, так как если система координат не размещаемыеа (например, отслеживание было прервано), приложение не сможет визуализировать его для этого кадра. Шаблон вызывает **визуализацию** только для вращающегося куба, если класс **камераресаурцес** указывает на успешное обновление.

Для сохранения голограмм, в которых разработчик или пользователь помещает их в мир, Windows Mixed Reality включает функции для [стабилизации изображений](hologram-stability.md). Образ стабилизации помогает скрыть задержку, присущую конвейеру отрисовки, чтобы обеспечить наилучший опыт для пользователей. можно указать точку фокусировки, чтобы улучшить стабилизации изображений, или можно предоставить буфер глубины для стабилизации оптимизированного изображения в режиме реального времени.

Для получения лучших результатов приложение должно предоставить буфер глубины с помощью API <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> . Затем Windows Mixed Reality может использовать сведения об геометрии из буфера глубины для оптимизации стабилизации изображений в режиме реального времени. Шаблон приложения Windows holographic по умолчанию фиксирует буфер глубины приложения, помогая оптимизировать стабильность.

Из **аппмаин:: Render**:

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
>Windows обработает текстуру глубины на GPU, поэтому в качестве ресурса шейдера необходимо использовать буфер глубины. Создаваемый ID3D11Texture2D должен быть в формате без типа, и его следует привязать как представление ресурсов шейдера. Ниже приведен пример создания текстуры глубины, которую можно зафиксировать для изображения стабилизации.

Код для **создания ресурсов буфера глубины для CommitDirect3D11DepthBuffer**:

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

**Нарисуйте holographic, содержимое**

Шаблон приложения Windows holographic визуализирует содержимое на стереосистеме, используя рекомендуемый способ рисования экземпляра geometry в Texture2DArray размера 2. Давайте рассмотрим эту часть и то, как она работает в Windows Mixed Reality.

Из **спиннингкуберендерер:: Render**:

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

Каждый экземпляр обращается к другой матрице представления или проекции из буфера констант. Ниже приведена структура буфера констант, которая представляет собой просто массив из двух матриц.

Из **вертексшадершаред. HLSL**, входящего в **впртвертексшадер. HLSL**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

Индекс целевого массива прорисовки должен быть задан для каждого пикселя. В следующем фрагменте кода Output. viewId сопоставляется с семантикой **SV_RenderTargetArrayIndex** . Обратите внимание, что для этого требуется поддержка необязательной функции Direct3D 11,3, которая позволяет задать семантику индекса целевого массива прорисовки на любом этапе шейдера.

Из **впртвертексшадер. HLSL**:

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

Из **вертексшадершаред. HLSL**, входящего в **впртвертексшадер. HLSL**:

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

Если вы хотите использовать существующие методы рисования экземпляров с помощью этого метода рисования в массиве нацеливания на стерео прорисовки, достаточно дважды нарисовать число экземпляров, которые у вас есть. В шейдере разделите **input. куст Instid** на 2, чтобы получить идентификатор исходного экземпляра, который можно проиндексировать в (например,) буфер данных для каждого объекта: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Важное примечание о визуализации стерео содержимого в HoloLens

Windows Mixed Reality поддерживает возможность установки индекса массива целевых объектов прорисовки с любого этапа шейдера. как правило, это задача, которая может быть выполнена только на этапе шейдера геометрии из-за способа определения семантики для Direct3D 11. Здесь представлен полный пример настройки конвейера отрисовки с набором стадий вершин и шейдеров пикселей. Код шейдера описан выше.

Из **спиннингкуберендерер:: Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Важное замечание о подготовке к просмотру на устройствах, не являющихся HoloLens

Для задания индекса массива целевых объектов прорисовки в шейдере вершин требуется, чтобы графический драйвер поддерживал дополнительную функцию Direct3D 11,3, которая поддерживает HoloLens. Приложение может безопасно реализовать только этот метод для подготовки к просмотру, и все требования будут выполнены для работы в Microsoft HoloLens.

Это может быть тот случай, когда вы хотите использовать эмулятор HoloLens, который может быть мощным средством разработки для holographic приложений, и поддерживать иммерсивное устройство в Windows Mixed Reality, подключенное к компьютерам под управлением Windows 10. Поддержка пути визуализации не в HoloLens, поэтому для всех Windows Mixed Reality также встроена в шаблон приложения Windows Holographic. В коде шаблона вы найдете код, позволяющий запускать приложение holographic на GPU на компьютере разработчика. Ниже показано, как класс **DeviceResources** проверяет наличие этой дополнительной поддержки компонентов.

Из **DeviceResources:: креатедевицересаурцес**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Для поддержки отрисовки без этой дополнительной функции приложение должно использовать шейдер Geometry для задания индекса целевого массива прорисовки. Этот фрагмент кода будет добавлен *после* **вссетконстантбуфферс**и *перед* **PSSetShader** в примере, приведенном в предыдущем разделе, в котором объясняется, как визуализировать стерео в HoloLens.

Из **спиннингкуберендерер:: Render**:

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

**HLSL Примечание**. в этом случае необходимо также загрузить немного измененный шейдер вершин, передающий индекс массива целевых объектов отрисовки шейдеру Geometry с помощью семантики шейдера, которая всегда разрешена, например TEXCOORD0. Шейдер геометрии не должен выполнять никаких действий. Шейдер геометрии шаблона проходит через все данные, за исключением индекса целевого массива прорисовки, который используется для задания семантической SV_RenderTargetArrayIndex.

Код шаблона приложения для **жеометришадер. HLSL**:

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

## <a name="present"></a>Present

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Включение в holographic фрейма цепочки буферов

В Windows Mixed Reality система управляет цепочкой буферов обмена. Затем система управляет показом кадров на каждой из holographic камер для обеспечения высокого качества взаимодействия с пользователем. Он также предоставляет окно просмотра, которое обновляет каждый кадр для каждой камеры для оптимизации аспектов системы, таких как изображение стабилизации или запись смешанной реальности. Таким образом, holographic приложение, использующее DirectX, не вызывает **Present** в цепочке подкачки DXGI. Вместо этого используйте класс <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> , чтобы показать все цепочек переключений для кадра после завершения его рисования.

Из **DeviceResources::P**повторной отправки:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

По умолчанию этот API ожидает завершения кадра перед возвратом. Перед началом работы над новым кадром holographic приложения должны ожидать завершения предыдущего кадра, так как это сокращает задержку и обеспечивает лучшие результаты прогнозов с помощью Holographic. Это не жесткое правило, и если у вас есть кадры, которые занимают больше одного экрана для подготовки к просмотру, можно отключить это время, передав параметр Холографикфрамепресентваитбехавиор в <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">пресентусингкуррентпредиктион</a>. В этом случае, скорее всего, будет использоваться поток асинхронной отрисовки для поддержания непрерывной нагрузки на GPU. Обратите внимание, что частота обновления устройства HoloLens составляет 60 Гц, при этом размер одного кадра составляет примерно 16 мс. Для иммерсивного устройства гарнитуры могут варьироваться от 60 Гц до 90hz; При обновлении экрана с частотой 90 Гц каждый кадр будет иметь длительность примерно 11 мс.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Обрабатывайте сценарии Девицелост в сотрудничество с Холографикфраме

Приложениям DirectX 11 обычно требуется проверить значение HRESULT, возвращаемое функцией **Present** цепочки ПОДкачки DXGI, чтобы определить, была ли ошибка **девицелост** . Класс <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> обрабатывает это за вас. Изучите <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">холографикфрамепресентресулт</a> , которые он возвращает, чтобы узнать, нужно ли освободить и повторно создать ресурсы на основе Direct3D и устройств.

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

Обратите внимание, что если устройство Direct3D было потеряно и вы создали его повторно, вам нужно сообщить <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a> начать использовать новое устройство. Для этого устройства будет создана цепочка буферов.

Из **DeviceResources:: инитиализеусингхолографикспаце**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

После представления кадра можно вернуться к главному циклу программы и разрешить переход к следующему кадру.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>Гибридные графические компьютеры и приложения смешанной реальности

В Windows 10 Creators Update PCS можно настроить **как** дискретные, так и интегрированные GPU. С этими типами компьютеров Windows выберет адаптер, к которому подключена гарнитура. Приложения должны гарантировать, что создаваемое устройство DirectX использует тот же адаптер.

В большинстве общих примеров кода Direct3D демонстрируется создание устройства DirectX с помощью аппаратного адаптера по умолчанию, который в гибридной системе может отличаться от используемого для гарнитуры.

Чтобы обойти все проблемы, которые могут возникнуть, используйте <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">холографикадаптерид</a> из <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">холографикспаце</a>. Примарядаптерид () или <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">холографикдисплай</a>. ИД адаптера (). Этот ИД адаптера можно затем использовать для выбора правильного Дксгиадаптер с помощью IDXGIFactory4. Енумадаптербилуид.

Из **DeviceResources:: инитиализеусингхолографикспаце**:

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

Код для **обновления DeviceResources:: креатедевицересаурцес для использования идксгиадаптер**

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

**Гибридная графика и Media Foundation**

Использование Media Foundation в гибридных системах может вызвать проблемы, когда видео не будет отображаться или текстура видео повреждена. Это может произойти из-за того, что Media Foundation по умолчанию используется поведение системы, как упоминалось выше. В некоторых сценариях для поддержки многопоточности и установки правильных флагов создания требуется создать отдельный ID3D11Device.

При инициализации ID3D11Device должен быть определен флаг D3D11_CREATE_DEVICE_VIDEO_SUPPORT в составе D3D11_CREATE_DEVICE_FLAG. После создания устройства и контекста вызовите <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">сетмултисреадпротектед</a> , чтобы включить многопоточность. Чтобы связать устройство с <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">имфдксгидевицеманажер</a>, используйте функцию <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">Имфдксгидевицеманажер:: ресетдевице</a> .

Код для **связывания ID3D11Device с имфдксгидевицеманажер**:

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

## <a name="see-also"></a>См. также:
* [Системы координат в DirectX](coordinate-systems-in-directx.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
