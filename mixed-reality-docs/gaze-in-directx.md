---
title: HEAD и глаз взглядом в DirectX
description: Руководство разработчика по использованию головной взглядом и отслеживания в собственных приложениях DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: взглядом, головного взглядом, head отслеживания, отслеживания, directx, входные данные и голограммы
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414411"
---
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="b767a-104">HEAD и глаз помощи входных данных в DirectX</span><span class="sxs-lookup"><span data-stu-id="b767a-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="b767a-105">В Windows Mixed Reality, глаз и головной взглядом входных данных используется для определения того, что пользователь просматривает.</span><span class="sxs-lookup"><span data-stu-id="b767a-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="b767a-106">Это может использоваться для диска основных моделей ввода, такие как [головного взглядом и фиксации](gaze-and-commit.md)и Кроме того, чтобы предоставить контекст для типов взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b767a-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="b767a-107">Существует два вида взглядом векторы, которые доступны через API: head взглядом и взглядом глаз.</span><span class="sxs-lookup"><span data-stu-id="b767a-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="b767a-108">Оба языка поставляются как 3 измерений Рэй с начала координат и направление.</span><span class="sxs-lookup"><span data-stu-id="b767a-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="b767a-109">Приложения могут затем raycast в их сцены или реальном мире и определить, что он предназначен.</span><span class="sxs-lookup"><span data-stu-id="b767a-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="b767a-110">**HEAD помощи** представляет направление, в указанном head пользователя.</span><span class="sxs-lookup"><span data-stu-id="b767a-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="b767a-111">Это можно рассматривать как положения и направления переадресации самого устройства, с позиции, представляющий центре точек между двух мониторов.</span><span class="sxs-lookup"><span data-stu-id="b767a-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="b767a-112">HEAD взглядом доступна на всех устройствах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="b767a-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="b767a-113">**Взглядом глаз** представляет направление, в котором глаза пользователя нужны сторону.</span><span class="sxs-lookup"><span data-stu-id="b767a-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="b767a-114">Начало координат находится между глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="b767a-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="b767a-115">Она доступна на устройствах смешанной реальности, включающие за системой отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b767a-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="b767a-116">Head и глаз взглядом лучей, доступны через [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span><span class="sxs-lookup"><span data-stu-id="b767a-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="b767a-117">Просто вызовите [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) для получения объекта SpatialPointerPose в указанной отметке времени и [системы координат](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="b767a-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="b767a-118">Этот SpatialPointerPose содержит origin головной взглядом и направление.</span><span class="sxs-lookup"><span data-stu-id="b767a-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="b767a-119">Он также содержит начала координат глаз взглядом и направление при наличии отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b767a-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="b767a-120">С помощью головного взглядом</span><span class="sxs-lookup"><span data-stu-id="b767a-120">Using head gaze</span></span>

<span data-ttu-id="b767a-121">Чтобы получить доступ к головному взглядом, запустите путем вызова [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) для получения объекта SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="b767a-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="b767a-122">Необходимо передать следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="b767a-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="b767a-123">Объект [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , представляющий требуемой системы координат для головного взглядом.</span><span class="sxs-lookup"><span data-stu-id="b767a-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="b767a-124">Это ограничение задается *система coordinateSystem* переменных в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="b767a-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="b767a-125">Дополнительные сведения см. в статье наших [системы координат](coordinate-systems-in-directx.md) руководство разработчика.</span><span class="sxs-lookup"><span data-stu-id="b767a-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="b767a-126">Объект [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , представляющий точное время Головной позу запрошено.</span><span class="sxs-lookup"><span data-stu-id="b767a-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="b767a-127">Обычно вы будете использовать метку времени, соответствующее времени, когда будет отображаться текущего кадра.</span><span class="sxs-lookup"><span data-stu-id="b767a-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="b767a-128">Вы можете получить эту метку времени отображения прогнозируемых из [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) объект, который можно получить с помощью текущего [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="b767a-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="b767a-129">Этот объект HolographicFramePrediction представлен *прогноза* переменной в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="b767a-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="b767a-130">При наличии допустимых SpatialPointerPose головного положения и направления переадресации доступны как свойства.</span><span class="sxs-lookup"><span data-stu-id="b767a-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="b767a-131">Ниже показано, как получить к ним доступ.</span><span class="sxs-lookup"><span data-stu-id="b767a-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="b767a-132">С помощью взглядом глаз</span><span class="sxs-lookup"><span data-stu-id="b767a-132">Using eye gaze</span></span>

<span data-ttu-id="b767a-133">API взглядом глаз очень похожа на головной взглядом.</span><span class="sxs-lookup"><span data-stu-id="b767a-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="b767a-134">Она использует тот же [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, предоставляющая луча, начало координат и направление, вы можете raycast от сцены.</span><span class="sxs-lookup"><span data-stu-id="b767a-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="b767a-135">Единственная разница в, необходимо явно включить отслеживание глаз перед его использованием.</span><span class="sxs-lookup"><span data-stu-id="b767a-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="b767a-136">Для этого вам необходимо выполнить два действия:</span><span class="sxs-lookup"><span data-stu-id="b767a-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="b767a-137">Запрашивать разрешение пользователя для использования отслеживания в приложении.</span><span class="sxs-lookup"><span data-stu-id="b767a-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="b767a-138">Включите функцию «Помощи Input» в манифесте пакета.</span><span class="sxs-lookup"><span data-stu-id="b767a-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="b767a-139">Запросить доступ к помощи входных данных</span><span class="sxs-lookup"><span data-stu-id="b767a-139">Requesting access to gaze input</span></span>
<span data-ttu-id="b767a-140">При запуске приложения вызовите [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) запрашивать доступ к глаз отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b767a-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="b767a-141">Система будет запрашивать пользователя, при необходимости и возвращают [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) после предоставления доступа.</span><span class="sxs-lookup"><span data-stu-id="b767a-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="b767a-142">Это асинхронный вызов, поэтому она требует некоторого дополнительного управления.</span><span class="sxs-lookup"><span data-stu-id="b767a-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="b767a-143">Следующий пример запускает отсоединенных std::thread ожидания результата, который сохраняется в переменную-член вызывается *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="b767a-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="b767a-144">Запуск отсоединенных поток является только один из вариантов для обработки асинхронных вызовов.</span><span class="sxs-lookup"><span data-stu-id="b767a-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="b767a-145">Кроме того, можно использовать новый [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) функциональные возможности, поддерживаемые C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="b767a-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="b767a-146">Вот еще один пример для запросом разрешения пользователя:</span><span class="sxs-lookup"><span data-stu-id="b767a-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="b767a-147">EyesPose::IsSupported() позволяет приложению для запуска диалогового окна разрешение только в том случае, если имеется tracker глаз.</span><span class="sxs-lookup"><span data-stu-id="b767a-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="b767a-148">GazeInputAccessStatus m_gazeInputAccessStatus; Это необходимо для предотвращения многократного всплывающее окно с запросом разрешения.</span><span class="sxs-lookup"><span data-stu-id="b767a-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="b767a-149">Объявление *помощи ввода* возможностей</span><span class="sxs-lookup"><span data-stu-id="b767a-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="b767a-150">Дважды щелкните файл appxmanifest в *обозревателе решений*.</span><span class="sxs-lookup"><span data-stu-id="b767a-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="b767a-151">Затем перейдите к *возможности* и установите *помощи ввода* возможностей.</span><span class="sxs-lookup"><span data-stu-id="b767a-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Возможность ввода взглядом](images/gaze-input-capability.png)

<span data-ttu-id="b767a-153">Это добавляет следующие строки, чтобы *пакета* раздела appxmanifest-файла:</span><span class="sxs-lookup"><span data-stu-id="b767a-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="b767a-154">Начало Рэй взглядом глаз</span><span class="sxs-lookup"><span data-stu-id="b767a-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="b767a-155">После получения доступа к ET, вы можете свободно скопировать Рэй взглядом глаз каждого кадра.</span><span class="sxs-lookup"><span data-stu-id="b767a-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="b767a-156">Как и в головном взглядом получить [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) путем вызова [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) требуемой отметкой времени и системы координат.</span><span class="sxs-lookup"><span data-stu-id="b767a-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="b767a-157">Содержит SpatialPointerPose [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) объекта через [глаза](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) свойство.</span><span class="sxs-lookup"><span data-stu-id="b767a-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="b767a-158">Это отличное от null, только при включении отслеживания.</span><span class="sxs-lookup"><span data-stu-id="b767a-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="b767a-159">Оттуда можно проверить, есть ли у пользователя на устройстве за отслеживание калибровки, вызвав [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="b767a-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="b767a-160">Затем используйте [помощи](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) свойство для получения [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing глаза помощи положения и направления.</span><span class="sxs-lookup"><span data-stu-id="b767a-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="b767a-161">Свойства взглядом могут иногда иметь значение null, поэтому не забудьте проверить это.</span><span class="sxs-lookup"><span data-stu-id="b767a-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="b767a-162">Это может произойти является, если калиброванных пользователь временно закрывает их глаза.</span><span class="sxs-lookup"><span data-stu-id="b767a-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="b767a-163">Приведенный ниже показано, как получить доступ к Рэй взглядом глаз.</span><span class="sxs-lookup"><span data-stu-id="b767a-163">The following code shows how to access the eye gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="b767a-164">Сопоставление взглядом с других входных данных</span><span class="sxs-lookup"><span data-stu-id="b767a-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="b767a-165">Иногда может оказаться необходимым [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) , соответствующий с событием в прошлом.</span><span class="sxs-lookup"><span data-stu-id="b767a-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="b767a-166">Например если пользователь выполняет Air коснитесь кнопки, приложение может потребоваться знать, что они бы все видели.</span><span class="sxs-lookup"><span data-stu-id="b767a-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="b767a-167">Для этой цели, используя [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) с кадром прогнозируемое время могут быть неточными из-за задержки между системы обработки ввода и отображения времени.</span><span class="sxs-lookup"><span data-stu-id="b767a-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="b767a-168">Кроме того при использовании взглядом глаза для нацеливания на этот момент, как правило, для перемещения еще до завершения действие фиксации.</span><span class="sxs-lookup"><span data-stu-id="b767a-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="b767a-169">Это меньше всего важна для простой Air, коснитесь, но становится более критичной, при объединении долго голосовые команды с быстрой глаз перемещений.</span><span class="sxs-lookup"><span data-stu-id="b767a-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="b767a-170">Один из способов обработки этого сценария — чтобы сделать дополнительный вызов [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), с помощью исторических метку времени, соответствующее событию ввода.</span><span class="sxs-lookup"><span data-stu-id="b767a-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="b767a-171">Однако для входных данных, которая направляет через SpatialInteractionManager, есть более простой метод.</span><span class="sxs-lookup"><span data-stu-id="b767a-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="b767a-172">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) имеет свои собственные [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) функции.</span><span class="sxs-lookup"><span data-stu-id="b767a-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="b767a-173">Вызова метода, предоставляющий вполне коррелированные [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) без догадки.</span><span class="sxs-lookup"><span data-stu-id="b767a-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="b767a-174">Дополнительные сведения о работе с SpatialInteractionSourceStates взгляните на [руки и контроллеры движения в DirectX](hands-and-motion-controllers-in-directx.md) документации.</span><span class="sxs-lookup"><span data-stu-id="b767a-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b767a-175">См. также</span><span class="sxs-lookup"><span data-stu-id="b767a-175">See also</span></span>
* [<span data-ttu-id="b767a-176">Головной модель ввода, взглядом и фиксации</span><span class="sxs-lookup"><span data-stu-id="b767a-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b767a-177">Глаз взглядом на HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b767a-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="b767a-178">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="b767a-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="b767a-179">Голосовой ввод в DirectX</span><span class="sxs-lookup"><span data-stu-id="b767a-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="b767a-180">Контроллеры движения и жестов в DirectX</span><span class="sxs-lookup"><span data-stu-id="b767a-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
