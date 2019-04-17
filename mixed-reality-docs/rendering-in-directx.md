---
title: Подготовка к просмотру в DirectX
description: Описание holographic отрисовки для смешанной реальности Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, голограммы, подготовки к просмотру, 3D-графики, HolographicFrame, просмотру цикла, цикл обновления, пошаговое руководство, пример кода
ms.openlocfilehash: fd35f971af4c3c9dfd7f21ee396c92216b3246e9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605163"
---
# <a name="rendering-in-directx"></a>Подготовка к просмотру в DirectX

Смешанная реальность Windows построена на DirectX для создания полнофункциональных, трехмерные графические возможности для пользователей. Абстракции отрисовки находится непосредственно над DirectX и позволяет рассматривать приложения положение и ориентацию одному или нескольким наблюдателям holographic сцены, как прогнозируемые системой. Разработчик может найдите их голограммы по отношению к каждой камеры, позволяя визуализации этих голограммы в различных Пространственные системы координат при перемещении приложения.

## <a name="update-for-the-current-frame"></a>Обновления для текущего кадра

Чтобы обновить состояние приложения для голограммы, один раз в кадре, приложение выполняет следующие действия:
* Получить <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> из системы управления для отображения.
* Обновление текущего прогноза где представления камеры будет после завершения отрисовки сцены. Обратите внимание, что может существовать несколько камеры для holographic сцены.

Для подготовки к просмотру с представлениями holographic камеры, один раз в кадре, приложение выполняет следующие действия:
* Для каждой камеры визуализации сцены для текущего кадра, используя матриц представления и проекции камеры из системы.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Создание нового кадра holographic и получение прогноза

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> содержит информацию, необходимую для приложения для обновления и отрисовки текущего кадра. Каждый новый пакет начала приложения, вызвав **CreateNextFrame** метод. При вызове этого метода, прогнозы выполняются с помощью данных датчиков доступен и инкапсулированные в **CurrentPrediction** объекта.

Объект кадра необходимо использовать для каждого отображаемого кадра, так как он допустим только для обмена мгновенными во времени. **CurrentPrediction** свойство содержит сведения, такие как положение камеры. Данные определяется в тот момент, когда во времени, когда кадр должен быть видимым для пользователя.

Следующий код — отрывок из **AppMain::Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Процесс обновления камеры

Задние буферы можно изменить из фрейма. Потребностями приложения для проверки на задний план буфер для каждой камеры и выпуска, а также повторно создать представления ресурсов и буферов глубины, при необходимости. Обратите внимание, что набор создает в прогноз заслуживающим доверия списком камер, используемых в текущем фрейме. Как правило его использовать для выполнения итерации на наборе камеры.

Из **AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Из **DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Получить систему координат для использования в качестве основы для подготовки к просмотру

Смешанная реальность Windows позволяет создавать различные приложения [системы координат](coordinate-systems-in-directx.md) при необходимости, например присоединенная ссылка и стационарных ссылку кадром, отслеживающие расположения в реальном мире. Приложение затем может использовать эти системы координат делать выводы о том, где для отрисовки каждого кадра голограммы. При запросе координаты от API, вы всегда будет передавать в <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> в котором будут эти координаты можно выразить.

Из **AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Затем эти системы координат можно использовать для создания стерео представление матрицы при отрисовке содержимого в сцене.

Из **CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Процесс взглядом и жест ввода

[Помощи](gaze.md) и [жест](gestures.md) входные данные не создаются на основе времени и не имеют для обновления в **StepTimer** функции. Тем не менее [вводимых](gaze,-gestures,-and-motion-controllers-in-directx.md) является то, что приложение должно выглядеть в каждом кадре.

### <a name="process-time-based-updates"></a>Обработка обновлений по времени

Любое приложение отрисовки в реальном времени будет нужен способ обработки обновлений на основе времени; Мы предоставляем способ это сделать в шаблоне приложения с Windows Holographic с помощью **StepTimer** реализации. Это похоже на StepTimer, предоставленный в шаблоне приложения универсальной платформы Windows DirectX 11, поэтому если вы уже были также рассмотрены этого шаблона можно на основе знакомых. Этот вспомогательный класс StepTimer образец может предоставить фиксированный интервал времени обновления, а также переменной временной шаг обновления, а режим по умолчанию представляет собой последовательность шагов переменных времени.

В случае holographic визуализации мы явным образом выбрали не получать слишком много, в функцию таймера. Это обусловлено тем, можно настроить его, чтобы быть шаг фиксированное время, в противном случае его может вызываться несколько раз покадровая — или вообще не, для некоторых кадры — и наши обновления holographic данных должны быть выполнены после каждого кадра.


Из **AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Положения и поворота голограммы в вашей системе координат

Если вы работаете в одной системы координат, а шаблон выполнит все с **SpatialStationaryReferenceFrame**, этот процесс не отличается от нужной в противном случае можно в области трехмерной графики. Здесь мы поворот куба и задайте матрицы модели относительно положения в стационарные системе координат.

Из **SpinningCubeRenderer::Update**:

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

**Обратите внимание на то, о расширенных сценариях:** Вращающегося куба является очень простой пример того, как разместить голограмма в рамке одна ссылка. Существует также возможность [использовать несколько SpatialCoordinateSystems](coordinate-systems-in-directx.md) в том же Отрисованный кадр, в то же время.

### <a name="update-constant-buffer-data"></a>Обновление данных буфера констант

Как обычно обновляются преобразования модели для содержимого. К этому моменту будут обработаны допустимые преобразования для системы координат, которые вы будете отрисовку в.

Из **SpinningCubeRenderer::Update**:

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

Как насчет представления и проекции преобразования? Для получения наилучших результатов необходимо подождать, пока мы все почти готово для наших вызовов draw, прежде чем углубиться в эти.

## <a name="render-the-current-frame"></a>Отрисовки текущего кадра

Отрисовки со смешанной реальностью Windows не сильно отличается от отрисовки на дисплее 2D mono, но есть некоторые различия, которые необходимо учитывать:
* Прогнозы holographic кадра важны. Чем ближе прогноза — при появлении кадре, тем лучше будет выглядеть ваш голограммы.
* Смешанная реальность Windows управляет представления камеры. Необходимые для отображения к каждой из них, так как кадр holographic позволяет представить их для вас более поздней версии.
* Стерео отрисовки рекомендуется сделать с помощью внутренне рисунка в массив целевой объект отрисовки. В шаблоне holographic приложения используется рекомендуемый подход внутренне отрисовки в массив целевой объект отрисовки, использующего целевой объект прорисовки на **массивы Texture2DArray**.
* Если требуется для подготовки к просмотру без использования стерео создание экземпляров, необходимо создать два вектора RenderTargetViews (по одному для каждого глаза), каждая ссылка, один из двух срезов в **массивы Texture2DArray** предоставить приложению, из системы. Это не рекомендуется, так как это обычно значительно медленнее, чем создание экземпляров.

### <a name="get-an-updated-holographicframe-prediction"></a>Получить обновленный прогноз HolographicFrame

Обновление прогноза кадров также эффективность стабилизацию изображения и обеспечивает более точное расположение голограммы из-за короткое время между прогноза, и если кадр является видимым для пользователя. В идеале обновите прогнозировании кадр только что перед отрисовкой.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Визуализации для каждой камеры

Цикла на наборе создает камеры в прогноз и отображать для каждой камеры в этом наборе.

**Настройка вашей прохода отрисовки**

Windows Mixed Reality использует stereoscopic отрисовки для улучшения иллюзию глубины и для подготовки к просмотру stereoscopically, поэтому левый и правый отображение активны. При визуализации stereoscopic имеется смещение между двумя экранов, мозг согласовать как фактический глубины. Этот раздел охватывает stereoscopic визуализация с использованием создание экземпляров, с помощью кода из Windows Holographic шаблон приложения.

Каждой камеры имеет свои собственные визуализации целевой (задний буфер) и представления и проекции матрицы в holographic пространство. Вашему приложению потребуется создать любые другие камеры ресурсы — такие как буфер глубины - на основе-камер. В шаблоне приложения с Windows Holographic мы предоставляем объединить эти ресурсы в DX::CameraResources, вспомогательный класс. Сначала создайте представления целевого объекта отрисовки:

Из **AppMain::Render**:

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

**Использовать этот прогноз для получения матрицы просмотра и проекции для камеры**

Матрицы просмотра и проекции для каждого holographic камеры изменится с каждого кадра. Обновление данных в буфер констант для каждой holographic камеры. Это необходимо сделать в том случае, после того как вы обновили прогноза, и вызывает перед внесением любой draw для этой камеры.

Из **AppMain::Render**:

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

Здесь мы покажем, как матрицы они получены из поза камеры. Во время этого процесса мы также получаем текущей области просмотра для камеры. Обратите внимание на то, как мы предоставляем в системе координат: это же система координат, мы использовали для понимания взглядом и он аналогичен тому, мы использовали для размещения вращающегося куба.


Из **CameraResources::UpdateViewProjectionBuffer**:

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

Окно просмотра должно иметь значение каждого кадра. Шейдер вершин (по крайней мере) обычно требуется доступ к данным представления и проекции.


Из **CameraResources::AttachViewProjectionBuffer**:

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

**Отрисовки для заднего буфера камеры и зафиксируйте буфер глубины**:

Рекомендуется убедиться, что **TryGetViewTransform** выполнена успешно, прежде чем использовать/проекция представления данных, поскольку если система координат не может быть найдена (например, отслеживания была прервана) приложение не может обработать с ним для этого рамка. Шаблон вызывает только **визуализации** на вращающегося куба Если **CameraResources** класс указывает на успешное обновление.

Чтобы сохранить голограммы, где разработчик или пользователь помещает их в мире, смешанной реальности Windows включает функции для [изображения стабилизации](hologram-stability.md). Изображение стабилизации позволяет скрыть задержек, присущих конвейера отрисовки, чтобы обеспечить действия лучше всего holographic, необходимые для пользователей; точку фокуса может быть указан для улучшения изображения стабилизации еще дальше, или буфер глубины могут предоставляться для вычисления оптимизированный образ стабилизации в режиме реального времени.

Для получения наилучших результатов, должно предоставить буфер глубины с помощью метода <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API. Windows Mixed Reality затем можно использовать сведения о геометрии из буфер глубины для оптимизации стабилизацию изображения в режиме реального времени. Windows Holographic шаблон приложения фиксирует буфер глубины приложения по умолчанию, помогает оптимизировать голограмма стабильности.

Из **AppMain::Render**:

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
>Windows будет обрабатывать текстура глубины в GPU, поэтому ее можно использовать в качестве ресурса шейдера в буфер глубины. ID3D11Texture2D, создаваемой должно быть в формате без использования типов, и он должен быть привязан как представление ресурсов шейдера. Вот пример того, как создать текстуру глубины, которая была выделена для стабилизации образа.

Код для **создания ресурса буфера глубины для CommitDirect3D11DepthBuffer**:

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

**Рисование holographic содержимого**

Windows Holographic шаблон приложения отображает содержимое в стерео с помощью рекомендуемого метода рисования экземпляр geometry в массивы Texture2DArray размером 2. Давайте взглянем на создания экземпляров часть это, и как это работает со смешанной реальностью Windows.

Из **SpinningCubeRenderer::Render**:

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

Каждый экземпляр получает доступ к матрицу проекция/различные представления из буфера констант. Ниже представлена структура буфер констант, который является просто массивом 2 матриц.

Из **VertexShaderShared.hlsl**, включенная **VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

Индекс массива целевой объект отрисовки необходимо задать для каждого пикселя. В приведенном ниже фрагменте сопоставляется output.viewId **SV_RenderTargetArrayIndex** семантики. Обратите внимание на то, что это требует поддержки дополнительным компонентом Direct3D 11.3, позволяющий семантической из любой этап шейдера индекс массива целевой объект отрисовки.

Из **VPRTVertexShader.hlsl**:

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

Из **VertexShaderShared.hlsl**, включенная **VPRTVertexShader.hlsl**:

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

Если вы хотите использовать существующие экземпляры методы рисования с помощью этого метода рисунок издавать отрисовки целевого массива, что необходимо сделать всего лишь рисования дважды число экземпляров, которые обычно возникают. В шейдере, разделите **input.instId** по 2 для получения исходного идентификатора экземпляра, какие могут быть проиндексированы в буфер (к примеру) на объект данных: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Важное примечание о сохранении стерео содержимого в HoloLens

Смешанная реальность Windows поддерживает возможность задать индекс массива целевой объект отрисовки из любой этап шейдера; как правило это задача, которая может быть выполнена только в связи с особенностями семантических определен для Direct3D 11 этап шейдеров геометрии. Здесь мы покажем полный пример того, как настроить конвейера отрисовки с только что вершин и пикселей шейдера этапы набором. Код шейдера является, как описано выше.

Из **SpinningCubeRenderer::Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Важное примечание о подготовке к просмотру на устройствах не HoloLens

Установка индекс массива целевой объект отрисовки в шейдер вершин требует, что драйвер поддерживает дополнительный компонент Direct3D 11.3, который поддерживает HoloLens. Приложение может иметь возможность безопасно реализовать только этот прием для подготовки к просмотру, и будут выполняться все требования для запуска в Microsoft HoloLens.

Может оказаться так, что вы хотите использовать HoloLens эмулятор, который может быть средство разработки мощных holographic приложения — и поддержки Windows Mixed Reality иммерсивных гарнитура устройств, подключенных к ПК Windows 10. Поддержка для подготовки к просмотру пути не HoloLens — и таким образом, для всех Windows Mixed Reality — также встроена в Windows Holographic шаблон приложения. В коде шаблона можно найти код, чтобы разрешить приложению holographic выполняются в GPU в Компьютере разработки. Вот как **DeviceResources** класса проверки для этой поддержки дополнительного компонента.

Из **DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Для поддержки визуализации без Эта необязательная возможность, приложение должно использовать шейдер геометрии для задания рендеринга целевой индекс массива. Этот фрагмент кода будет добавляться *после* **VSSetConstantBuffers**, и *перед* **PSSetShader** в примере кода показано в предыдущем раздел, в котором объясняется, как визуализировать стерео на HoloLens.

Из **SpinningCubeRenderer::Render**:

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

**ПРИМЕЧАНИЕ HLSL**: В этом случае необходимо также загрузить слегка измененный вершинный построитель текстуры, который передает индекс массива целевой объект отрисовки в шейдер геометрии, с помощью шейдера всегда разрешено семантики, например TEXCOORD0. Шейдер геометрии не нужно выполнять никаких действий; шейдер геометрии шаблона проходит через все данные, за исключением индекс массива целевой объект отрисовки, который используется для задания SV_RenderTargetArrayIndex семантической.

Код шаблона приложения для **GeometryShader.hlsl**:

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

## <a name="present"></a>Представление

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Включить holographic кадр для представления цепочки буферов

С помощью Windows Mixed Reality система управляет цепочки буферов. Затем система управляет показа презентации кадры для каждого holographic камере, чтобы обеспечить взаимодействие с пользователями высокого качества. Он также предоставляет обновления окна просмотра каждого кадра, для каждой камеры, для оптимизации аспекты работы системы, например стабилизацию изображения или записать смешанной реальности. Таким образом, не вызывает holographic приложения, использующие DirectX **присутствует** на DXGI цепочка буферов. Вместо этого использовать <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> класс для представления всех цепочек переключений кадр, когда все будет готово рисованием.

Из **DeviceResources::Present**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

По умолчанию этот интерфейс API ожидает кадр и завершить перед возвращением. Holographic приложений следует подождать предыдущего кадра, прежде чем приступать к работе на новый кадр, так как это сокращает задержку и обеспечивает лучшие результаты из прогнозов holographic кадра. Это не жесткие правила и при наличии кадры, которые происходят дольше одного экрана обновления для подготовки к просмотру, вы можете отключить этот тип ожидания путем передачи параметра HolographicFramePresentWaitBehavior <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>. В этом случае скорее всего используется в потоке асинхронной подготовки к просмотру для обеспечения постоянной нагрузке на GPU. Обратите внимание, что частота обновления устройства HoloLens 60 Гц, где один кадр имеет длительность приблизительно 16 мс. Насыщенные гарнитуры может занимать от 60 Гц до 90 Гц; При обновлении отображение 90 Гц, каждый кадр будет иметь в течение приблизительно 11 мс.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Обработки сценариев DeviceLost вместе с HolographicFrame

Приложения DirectX 11 обычно необходимо проверить значение HRESULT, возвращенное цепочки буферов DXGI **присутствует** функции, чтобы узнать, если произошла **DeviceLost** ошибки. <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> класс обрабатывает это автоматически. Проверьте <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> возвращается, чтобы узнать, если необходимо освободить и повторного создания устройства Direct3D и ресурсы на основе устройств.

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

Обратите внимание, что если устройство Direct3D было потеряно, повторно создать его, вам необходимо сообщить <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> Чтобы приступить к использованию нового устройства. Для этого устройства будут созданы заново цепочки буферов.

Из **DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

После представлен кадре, можно вернуться в основной программе цикла и продолжить выполнение следующий кадр.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>Гибридной графики компьютеров и приложений смешанной реальности

Windows 10 Creators Update ПК могут быть настроены с **оба** дискретных, так и встроенная графических процессоров. С этими типами компьютеров Windows выберет гарнитуры, к которому подключен адаптер. Приложения необходимо убедиться, что устройство DirectX, которые оно создает использует тот же адаптер.

Наиболее общие Direct3D пример кода демонстрирует создание устройства DirectX с помощью адаптера оборудования по умолчанию, который не может совпадать с той, которая использовалась для гарнитуры в гибридной системе.

Чтобы устранить все проблемы, это может вызвать проблему, используйте <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> либо из <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() или <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId(). Этот adapterId может затем использоваться для выбора DXGIAdapter вправо, с помощью IDXGIFactory4.EnumAdapterByLuid.

Из **DeviceResources::InitializeUsingHolographicSpace**:

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

Код для **обновить DeviceResources::CreateDeviceResources использовать IDXGIAdapter**

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

**Гибридной графики и Media Foundation**

С помощью Media Foundation в гибридных системах может вызвать проблемы, где видео не будет отображаться или видео текстуры поврежден. Это может произойти, поскольку по умолчанию принимается Media Foundation поведение системы, как было сказано выше. В некоторых случаях создание отдельных ID3D11Device является обязательным для поддержки работы с множеством потоков и правильного создания установленные флаги.

При инициализации ID3D11Device, флаг D3D11_CREATE_DEVICE_VIDEO_SUPPORT должен быть определен как часть D3D11_CREATE_DEVICE_FLAG. После создания устройства, а затем контекст вызова <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> для включения многопоточности. Чтобы связать устройство с <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, использовать <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> функции.

Код для **связать ID3D11Device с IMFDXGIDeviceManager**:

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

## <a name="see-also"></a>См. также
* [Системы координат в DirectX](coordinate-systems-in-directx.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
