---
title: Создание проекта holographic DirectX
description: В этой статье описывается создание нового holographic приложения на основе шаблона приложения Windows смешанной реальности.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Смешанная реальность Windows holographic приложения, новое приложение, приложение универсальной платформы Windows, приложения шаблона, голограммы, новый проект, пошаговое руководство, загрузки, пример кода
ms.openlocfilehash: a7eac9d8056fe5f7bcc442d6441f71331fa96cf6
ms.sourcegitcommit: 19c9bff21061d485821b61c9f3498daef8fa8235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828130"
---
# <a name="creating-a-holographic-directx-project"></a>Создание проекта holographic DirectX

Holographic приложения, создаваемые для HoloLens будут <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">приложения универсальной платформы Windows (UWP)</a>.  Если для рабочего стола Windows Mixed Reality гарнитуры, можно создать приложение универсальной платформы Windows или приложения Win32.

Шаблон приложения универсальной платформы Windows holographic DirectX 11 очень напоминает шаблон приложения универсальной платформы Windows DirectX 11; он включает в себя программы цикла (или «цикла игры»), **DeviceResources** класса для управления устройство Direct3D и контекста, а также класс упрощенный обработчик содержимого. Есть также <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>точно так же, как любое другое приложение универсальной платформы Windows.

Приложение смешанной реальности, однако имеет некоторые дополнительные возможности, которые не присутствуют в типичном приложении Direct3D 11 UWP. Windows Holographic шаблон приложения возможность:
* Обработка ресурсов устройства Direct3D, связанных с holographic камеры.
* Получить камеры задние буферы из системы.
* Обрабатывать [помощи](gaze.md) ввода и распознавания простой [жест](gestures.md).
* Перейти в режим полноэкранной отрисовке стерео.

## <a name="how-do-i-get-started"></a>Как начать работу?

Первый [установить средства](install-the-tools.md), следующие инструкции по скачиванию Visual Studio 2017 и в эмуляторе Microsoft HoloLens. Шаблоны holographic приложения включены в тот же установщик, что и эмулятор Microsoft HoloLens. Также убедитесь, что перед установкой выбран параметр, чтобы установить шаблоны.

Теперь вы готовы создать приложение DirectX 11 Windows смешанной реальности. Обратите внимание на то, чтобы удалить этот пример содержимого, закомментируйте **DRAW_SAMPLE_CONTENT** директивы препроцессора в *pch.h*.

## <a name="creating-a-uwp-project"></a>Создание проекта UWP

Один раз [установлены средства](install-the-tools.md) затем созданием holographic проекта DirectX UWP.

Чтобы создать новый проект:
1. Запуск **Visual Studio**.
2. Из **файл** последовательно выберите пункты **New** и выберите **проекта** в контекстном меню. **Новый проект** откроется диалоговое окно.
3. Разверните **установленные** слева и разверните **Visual C++**  узел языка.
4. Перейдите к **универсальной Windows > Holographic** узел и выберите **Holographic приложение DirectX 11 (универсальные Windows) (C++/WinRT)**.
   ![Снимок экрана Holographic DirectX 11 C++шаблона проекта приложения WinRT UWP в Visual Studio](images/holographic-directx-app-cpp-new-project.png)<br>
   *Holographic DirectX 11 C++шаблона проекта приложения WinRT UWP в Visual Studio*
   >[!IMPORTANT]
   >Убедитесь, что имя шаблона проекта включает «(C++/WinRT)».  В противном случае у вас есть более старой версии holographic шаблонов проектов установки.  Чтобы получить последние шаблоны проекта, [установить последнюю эмулятор HoloLens](using-the-hololens-emulator.md).
5. Заполните **имя** и **расположение** текстовые поля и нажмите кнопку **ОК**. Создается проект holographic приложения.
6. Для разработки приложений для различных версий только 2 HoloLens, убедитесь, что **целевой версии** и **Минимальная версия** присваивается **Windows 10, версия 1903**.  Если планируется также HoloLens (1-го поколения) или рабочего стола гарнитуры смешанной реальности Windows, можно задать **Минимальная версия** для **Windows 10, версия 1809** вместо этого, несмотря на то, что это потребует некоторых <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"> Адаптивная проверки версии</a> в коде при использовании новые возможности HoloLens 2.
   ![Снимок экрана: параметр Windows 10, версия 1903 как целевую и минимальную версии](images/new-uwp-project.png)<br>
   *Установка **Windows 10, версия 1903** как целевую и минимальную версии*
   >[!IMPORTANT]
   >Если вы не видите **Windows 10, версия 1903** свободен, у вас последняя версия Windows 10 SDK установлен.  Чтобы получить этот параметр для отображения, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">установить версию 10.0.18362.0 или более поздняя версия пакета SDK для Windows 10</a>.

Шаблон создает проект с использованием <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, C ++ 17 языковых проекцию API среды выполнения Windows, которая поддерживает любой совместимый со стандартами C ++ 17 компилятор.  Проекта показано, как создать куб заблокирован для мира, помещенный два счетчика от пользователя. Пользователь может [жест касания](gestures.md#air-tap) или нажать кнопку на контроллере, чтобы поместить куба в другое место, который задается параметром пользователя [помощи](gaze.md). Вы можете изменить этот проект для создания любого приложения смешанной реальности.

Кроме того, можно создать новый проект с помощью **Visual C#**  шаблона holographic проекта, который основан на SharpDX.  Если ваш holographic C# проекта не запустилась из Windows Holographic шаблон приложения, вам потребуется скопировать файл ms.fxcompile.targets из Windows Mixed Reality C# шаблона проекта и импорта его в ваш .csproj файла для компиляции HLSL файлы, добавляемые в проект.

Просмотрите [с помощью Visual Studio для развертывания и отладки](using-visual-studio.md) сведения о том, как построение и развертывание примера в вашей HoloLens, ПК с иммерсивных устройство или эмулятор.

Остальная часть в инструкциях ниже предполагается, что вы используете C++ к сборке приложения.

### <a name="uwp-app-entry-point"></a>Точка входа для приложения универсальной платформы Windows

Запускает приложения универсальной платформы Windows holographic в **wWinMain** функции в AppView.cpp. **WWinMain** функция создает приложения <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> и запускает <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> с ним.

Из **AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

С этого момента AppView обрабатывает взаимодействие с Windows основные входные события CoreWindow события и обмена сообщениями и т. д. Он также создаст HolographicSpace, используемых приложением.

## <a name="creating-a-win32-project"></a>Создание проекта Win32

Самый простой способ приступить к созданию Win32, holographic проекта — адаптировать <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* пример Win32</a>.

В этом примере Win32 используется <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, C ++ 17 языковых проекцию API среды выполнения Windows, которая поддерживает любой совместимый со стандартами C ++ 17 компилятор.  Проекта показано, как создать куб заблокирован для мира, помещенный два счетчика от пользователя. Пользователь может нажать кнопку на контроллере, чтобы поместить куба в другое место, который задается параметром пользователя [помощи](gaze.md). Вы можете изменить этот проект для создания любого приложения смешанной реальности.

### <a name="win32-app-entry-point"></a>Точка входа приложения Win32

Запускает holographic приложения Win32 в **wWinMain** функции в AppMain.cpp. **WWinMain** функция создает HWND приложения и запускает цикл сообщений.

Из **AppMain.cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

С этого момента AppMain обрабатывает взаимодействие с основные окна сообщений и т. д. Он также создаст HolographicSpace, используемых приложением.

## <a name="render-holographic-content"></a>Визуализации holographic содержимого

Проекта **содержимого** папка содержит классы для подготовки к просмотру голограммы в [holographic пространства](getting-a-holographicspace.md). Голограмма по умолчанию в шаблоне является вращающегося куба, который разместил два метров от пользователя. Рисование этого куба реализуется в **SpinningCubeRenderer.cpp**, который имеет следующие основные методы:

|  Метод  |  Объяснение | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Загружает шейдеры и создает сетку куба. | 
|  `PositionHologram` |  Помещает голограмма в расположении, указанном с использованием указанного <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>. | 
|  `Update` |  Поворачивает куб и задает матрицы модели. | 
|  `Render` |  Прорисовывает кадр, с помощью шейдеров вершин и пикселей. | 

**Шейдеры** вложенная папка содержит четыре реализации шейдера по умолчанию:

|  Построитель текстуры  |  Объяснение | 
|----------|----------|
|  `GeometryShader.hlsl` |  К серверу, который оставляет геометрии без изменений. | 
|  `PixelShader.hlsl` |  Проходит через данные о цвете. Данные о цвете интерполированные и заданы для точки на этапе растеризации. | 
|  `VertexShader.hlsl` |  Простой шейдер для обработки вершин в GPU. | 
|  `VPRTVertexShader.hlsl` |  Простой шейдер для обработки вершин в GPU, оптимизированный для смешанной реальности Windows стерео отрисовки. | 

`VertexShaderShared.hlsl` содержит код, общий между `VertexShader.hlsl` и `VPRTVertexShader.hlsl`.

Шейдеры компилируются при сборке проекта, и они загружены в **SpinningCubeRenderer::CreateDeviceDependentResources** метод.

## <a name="interact-with-your-holograms"></a>Взаимодействовать с вашей голограммы

Ввод данных пользователем обрабатывается в **SpatialInputHandler** класса, который будет <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> экземпляра и подписывается на <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> событий. Это позволяет, определение жеста жест касания и другие Пространственные входных событий.

## <a name="update-holographic-content"></a>Обновление содержимого holographic

Смешанная реальность обновлений в цикл игры, который по умолчанию реализуется в **обновление** метод в `AppMain.cpp`. **Обновление** метод обновляет объектов сцены, например вращающегося куба и возвращает <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> объект, используемый для получения актуальной матриц представления и проекции и представлять цепочки буферов.

**Визуализации** метод в `AppMain.cpp` принимает <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> и прорисовывает текущий кадр для каждого holographic камеры, в соответствии с текущим приложением и пространственных позиционирования состояния.

## <a name="see-also"></a>См. также
* [Получение HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Отрисовка в DirectX](rendering-in-directx.md)
* [Развертывание и отладка с помощью Visual Studio](using-visual-studio.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
* [Использование XAML с голографическими приложениями DirectX](using-xaml-with-holographic-directx-apps.md)
