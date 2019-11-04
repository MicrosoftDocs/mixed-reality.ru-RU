---
title: Взгляд на головной взгляд и глаз в DirectX
description: Рекомендации для разработчиков по использованию головного взгляда и отслеживания взгляда в собственных приложениях DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: глаз-взгляд, руководитель-взгляд, отслеживание головок, отслеживание глаз, DirectX, ввод, голограммы
ms.openlocfilehash: 78a6190c18c8b92dd1d6f3d7a340b54d07b7feea
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435339"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="93e21-104">Ввод с взгляда на глаза в DirectX</span><span class="sxs-lookup"><span data-stu-id="93e21-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="93e21-105">В Windows Mixed Reality для определения того, что просматривает пользователь, используется ввод с глазом и взглядом на головной взгляд.</span><span class="sxs-lookup"><span data-stu-id="93e21-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="93e21-106">Это можно использовать для создания первичных входных моделей, таких как [head-взгляд и Commit](gaze-and-commit.md), а также для предоставления контекста для типов взаимодействий.</span><span class="sxs-lookup"><span data-stu-id="93e21-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="93e21-107">Есть два типа векторов взгляда, доступных через API: «Head-взгляд» и «глаз-взгляд».</span><span class="sxs-lookup"><span data-stu-id="93e21-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="93e21-108">Оба значения предоставляются в виде трехмерного луча с исходным и направленным координатами.</span><span class="sxs-lookup"><span data-stu-id="93e21-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="93e21-109">Приложения могут райкаст в фоновом режиме или в реальном мире, а также определить назначение пользователя.</span><span class="sxs-lookup"><span data-stu-id="93e21-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="93e21-110">**Заголовок-взгляд** представляет направление, на которое указывает заголовок пользователя.</span><span class="sxs-lookup"><span data-stu-id="93e21-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="93e21-111">Это следует рассматривать как расположение и направление вперед самого устройства, а также позицию, представляющую центральную точку между двумя дисплеями.</span><span class="sxs-lookup"><span data-stu-id="93e21-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="93e21-112">Головной взгляд доступен на всех устройствах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="93e21-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="93e21-113">**Глаз** . Наблюдатель представляет направление, в котором просматриваются глаза пользователя.</span><span class="sxs-lookup"><span data-stu-id="93e21-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="93e21-114">Источник располагается между глазами пользователя.</span><span class="sxs-lookup"><span data-stu-id="93e21-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="93e21-115">Она доступна на устройствах смешанной реальности, включающих систему отслеживания взгляда.</span><span class="sxs-lookup"><span data-stu-id="93e21-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="93e21-116">И те, и другие лучи доступны через API [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="93e21-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="93e21-117">Просто вызовите [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) , чтобы получить новый объект спатиалпоинтерпосе в указанной метке времени и [системе координат](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="93e21-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="93e21-118">Этот Спатиалпоинтерпосе содержит источник и направление головного взгляда.</span><span class="sxs-lookup"><span data-stu-id="93e21-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="93e21-119">Он также содержит источник глаза и направление взгляда, если отслеживание взгляда доступно.</span><span class="sxs-lookup"><span data-stu-id="93e21-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="93e21-120">Использование Head-взгляда</span><span class="sxs-lookup"><span data-stu-id="93e21-120">Using head-gaze</span></span>

<span data-ttu-id="93e21-121">Чтобы получить доступ к Head, начните с вызова [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) , чтобы получить новый объект спатиалпоинтерпосе.</span><span class="sxs-lookup"><span data-stu-id="93e21-121">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="93e21-122">Необходимо передать следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="93e21-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="93e21-123">Объект [спатиалкурдинатесистем](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) , представляющий нужную систему координат для головного взгляда.</span><span class="sxs-lookup"><span data-stu-id="93e21-123">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="93e21-124">Он представлен переменной *курдинатесистем* в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="93e21-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="93e21-125">Дополнительные сведения см. в нашем разделе, посвященном разработчику [систем координат](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="93e21-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="93e21-126">[Отметка времени](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , представляющая точное время запроса Head.</span><span class="sxs-lookup"><span data-stu-id="93e21-126">A [Timestamp](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="93e21-127">Обычно используется метка времени, соответствующая времени, когда будет отображаться текущий кадр.</span><span class="sxs-lookup"><span data-stu-id="93e21-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="93e21-128">Эту прогнозируемую отметку экрана можно получить из объекта [холографикфрамепредиктион](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , доступного через текущий [холографикфраме](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="93e21-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="93e21-129">Этот объект Холографикфрамепредиктион представляется переменной *прогноза* в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="93e21-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="93e21-130">После получения допустимого Спатиалпоинтерпосе расположение головного и прямого направления можно получить в виде свойств.</span><span class="sxs-lookup"><span data-stu-id="93e21-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="93e21-131">В следующем коде показано, как получить доступ к ним.</span><span class="sxs-lookup"><span data-stu-id="93e21-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="93e21-132">Использование глаза-взгляд</span><span class="sxs-lookup"><span data-stu-id="93e21-132">Using eye-gaze</span></span>

<span data-ttu-id="93e21-133">API взгляда на глаза очень похож на голову.</span><span class="sxs-lookup"><span data-stu-id="93e21-133">The eye-gaze API is very similar to head-gaze.</span></span>  <span data-ttu-id="93e21-134">Он использует тот же API [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , который предоставляет происхождение и направление луча, которые можно райкаст на сцене.</span><span class="sxs-lookup"><span data-stu-id="93e21-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="93e21-135">Единственное отличие заключается в том, что необходимо явно включить отслеживание взгляда перед его использованием.</span><span class="sxs-lookup"><span data-stu-id="93e21-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="93e21-136">Для этого необходимо выполнить два действия:</span><span class="sxs-lookup"><span data-stu-id="93e21-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="93e21-137">Запрос разрешения пользователя на использование отслеживания взгляда в приложении.</span><span class="sxs-lookup"><span data-stu-id="93e21-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="93e21-138">Включите функцию "Ввод взгляда" в манифесте пакета.</span><span class="sxs-lookup"><span data-stu-id="93e21-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="93e21-139">Запрос доступа к входным данным взгляда</span><span class="sxs-lookup"><span data-stu-id="93e21-139">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="93e21-140">При запуске приложения вызовите [эйеспосе:: рекуестакцессасинк](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) , чтобы запросить доступ к отслеживанию глаз.</span><span class="sxs-lookup"><span data-stu-id="93e21-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="93e21-141">Система запросит пользователя при необходимости и возвратит [газеинпутакцессстатус:: Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) после предоставления доступа.</span><span class="sxs-lookup"><span data-stu-id="93e21-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="93e21-142">Это асинхронный вызов, поэтому для него требуется некоторое дополнительное управление.</span><span class="sxs-lookup"><span data-stu-id="93e21-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="93e21-143">В следующем примере выполняется вращение отсоединенного std:: Thread для ожидания результата, который сохраняется в переменную-член с именем *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="93e21-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="93e21-144">Запуск отсоединенного потока — это только один вариант для обработки асинхронных вызовов.</span><span class="sxs-lookup"><span data-stu-id="93e21-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="93e21-145">Кроме того, можно использовать новые функции [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) , поддерживаемые C++/винрт.</span><span class="sxs-lookup"><span data-stu-id="93e21-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="93e21-146">Вот еще один пример для запроса разрешения пользователя:</span><span class="sxs-lookup"><span data-stu-id="93e21-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="93e21-147">Эйеспосе:: An () позволяет приложению активировать диалоговое окно разрешения только в том случае, если имеется средство регистрации взгляда.</span><span class="sxs-lookup"><span data-stu-id="93e21-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="93e21-148">Газеинпутакцессстатус m_gazeInputAccessStatus; Это позволяет предотвратить повторное извлечение запроса на разрешение.</span><span class="sxs-lookup"><span data-stu-id="93e21-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="93e21-149">Объявление возможности ввода с помощью *взгляда*</span><span class="sxs-lookup"><span data-stu-id="93e21-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="93e21-150">Дважды щелкните файл AppxManifest в *Обозреватель решений*.</span><span class="sxs-lookup"><span data-stu-id="93e21-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="93e21-151">Затем перейдите к разделу возможностей и проверьте возможность *ввода* с помощью *средства* выбора.</span><span class="sxs-lookup"><span data-stu-id="93e21-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Возможность ввода с клавиатуры](images/gaze-input-capability.png)

<span data-ttu-id="93e21-153">В раздел *пакета* в файле appxmanifest добавляются следующие строки:</span><span class="sxs-lookup"><span data-stu-id="93e21-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="93e21-154">Получение луча с глазом взгляда</span><span class="sxs-lookup"><span data-stu-id="93e21-154">Getting the eye-gaze ray</span></span>
<span data-ttu-id="93e21-155">После получения доступа к ET вы можете бесплатно захватить каждый кадр.</span><span class="sxs-lookup"><span data-stu-id="93e21-155">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="93e21-156">Как и в случае с Head-взглядом, получите [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , вызвав [Спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) с нужной меткой времени и системой координат.</span><span class="sxs-lookup"><span data-stu-id="93e21-156">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="93e21-157">Спатиалпоинтерпосе содержит объект [эйеспосе](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) через свойство [глаза](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="93e21-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="93e21-158">Это значение не равно null, только если включено отслеживание глаз.</span><span class="sxs-lookup"><span data-stu-id="93e21-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="93e21-159">Здесь можно проверить, имеет ли пользователь устройства калибровку отслеживания взгляда, вызвав [эйеспосе:: искалибратионвалид](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="93e21-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="93e21-160">Затем используйте [свойство "наблюдатель",](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) чтобы получить [спатиалрай](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) , контианинг расположение и направление взгляда.</span><span class="sxs-lookup"><span data-stu-id="93e21-160">Next, use the [Gaze](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) contianing the eye-gaze position and direction.</span></span> <span data-ttu-id="93e21-161">Свойство "взгляд" иногда может иметь значение null, поэтому обязательно проверьте это.</span><span class="sxs-lookup"><span data-stu-id="93e21-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="93e21-162">Это может произойти, если калибровка пользователя временно закрывает свои глаза.</span><span class="sxs-lookup"><span data-stu-id="93e21-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="93e21-163">В следующем коде показано, как получить доступ к лучау глаза.</span><span class="sxs-lookup"><span data-stu-id="93e21-163">The following code shows how to access the eye-gaze ray.</span></span>

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
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="93e21-164">Сопоставление взгляда с другими входными данными</span><span class="sxs-lookup"><span data-stu-id="93e21-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="93e21-165">Иногда может оказаться, что требуется [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) , соответствующий событию в прошлом.</span><span class="sxs-lookup"><span data-stu-id="93e21-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="93e21-166">Например, если пользователь выполняет касание Air, приложение может захотеть узнать, что именно оно искало.</span><span class="sxs-lookup"><span data-stu-id="93e21-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="93e21-167">Для этой цели простое использование [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) с прогнозируемым временем кадров будет неточным из-за задержки между системной обработкой входных данных и временем вывода.</span><span class="sxs-lookup"><span data-stu-id="93e21-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="93e21-168">Кроме того, если для нацеливания используется глаз, наши глаза, как правило, переходят даже перед завершением действия фиксации.</span><span class="sxs-lookup"><span data-stu-id="93e21-168">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="93e21-169">Это не является проблемой для простого касания воздуха, но становится более важным при объединении длинных голосовых команд с помощью передвижений с быстрым глазом.</span><span class="sxs-lookup"><span data-stu-id="93e21-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="93e21-170">Одним из способов решения этого сценария является создание дополнительного вызова [спатиалпоинтерпосе:: трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)с использованием метки времени с предысторией, соответствующей входному событию.</span><span class="sxs-lookup"><span data-stu-id="93e21-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="93e21-171">Однако для входных данных, перенаправляющихся через Спатиалинтерактионманажер, существует более простой метод.</span><span class="sxs-lookup"><span data-stu-id="93e21-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="93e21-172">[Спатиалинтерактионсаурцестате](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) имеет собственную функцию [трижетаттиместамп](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="93e21-172">The [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="93e21-173">Вызов, который предоставит вполне коррелированный [спатиалпоинтерпосе](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) без предоставляя.</span><span class="sxs-lookup"><span data-stu-id="93e21-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="93e21-174">Дополнительные сведения о работе с Спатиалинтерактионсаурцестатес см. в документации по [DirectX](hands-and-motion-controllers-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="93e21-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="93e21-175">См. также</span><span class="sxs-lookup"><span data-stu-id="93e21-175">See also</span></span>
* [<span data-ttu-id="93e21-176">Входная модель "Head-взгляд" и "фиксация"</span><span class="sxs-lookup"><span data-stu-id="93e21-176">Head-gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="93e21-177">Глаз — Взгляните на HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="93e21-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="93e21-178">Калибровка</span><span class="sxs-lookup"><span data-stu-id="93e21-178">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="93e21-179">Системы координат в DirectX</span><span class="sxs-lookup"><span data-stu-id="93e21-179">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="93e21-180">Ввод голоса в DirectX</span><span class="sxs-lookup"><span data-stu-id="93e21-180">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="93e21-181">Контроллеры движения и жестов в DirectX</span><span class="sxs-lookup"><span data-stu-id="93e21-181">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
