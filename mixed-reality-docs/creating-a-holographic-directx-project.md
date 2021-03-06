---
title: Создание проекта с помощью DirectX holographic
description: Описание процесса создания нового приложения holographic на основе шаблона приложения Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holographic приложение, новое приложение, приложение UWP, шаблон приложения, голограммы, новый проект, пошаговое руководство, Загрузка, пример кода
ms.openlocfilehash: 30f2c630b2919fbc304dc96d13cab74e22ed4adc
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277922"
---
# <a name="creating-a-holographic-directx-project"></a>Создание проекта с помощью DirectX holographic

Созданное вами приложение для HoloLens будет иметь <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">универсальная платформа Windows (UWP)</a>.  При нацеливании на Настольные гарнитуры Windows Mixed Reality можно создать приложение UWP или приложение Win32.

Шаблон приложения с DirectX 11 holographic в целом похож на шаблон приложения UWP DirectX 11. Он включает цикл программы (или "игровой цикл"), класс **DeviceResources** для управления устройством и контекстом Direct3D, а также упрощенный класс модуля подготовки содержимого. Он также имеет <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, как и любое другое приложение UWP.

Однако приложение Mixed Reality имеет некоторые дополнительные возможности, отсутствующие в типичном приложении UWP для платформы Direct3D. Шаблон приложения Windows Mixed Reality может:
* Обрабатывайте ресурсы устройства Direct3D, связанные с Holographic.
* Извлеките буферы камеры из системы или (в случае Direct3D12) создайте ресурсы с адресными буферами holographic и Управляйте временем существования ресурсов.
* Обработайте входные данные [взгляда](gaze-and-commit.md) и распознают простой [жест](gaze-and-commit.md#composite-gestures).
* Переход к полноэкранному режиму отображения.

## <a name="how-do-i-get-started"></a>Разделы справки начать?

Сначала [установите средства](install-the-tools.md), следуя инструкциям в статье Загрузка Visual Studio 2019 и шаблонов приложений Windows Mixed Reality. Шаблоны приложений смешанной реальности доступны в Visual Studio Marketplace как [загружаемые веб-](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)файлы или устанавливаются в виде расширения с помощью пользовательского интерфейса Visual Studio.

Теперь вы готовы создать приложение Windows Mixed Reality для DirectX 11! Обратите внимание, что для удаления образца содержимого закомментируйте директиву препроцессора **DRAW_SAMPLE_CONTENT** в *PCH. h*.

## <a name="creating-a-uwp-project"></a>Создание проекта UWP

После [установки средств](install-the-tools.md) можно создать проект HOLOGRAPHIC DirectX UWP.

Чтобы создать новый проект в Visual Studio 2019, выполните следующие действия.
1. Запустите **Visual Studio**.
2. В разделе Начало **работы** справа выберите **создать новый проект**.
3. В раскрывающихся меню диалогового окна **Создание нового проекта** выберите **C++** , **Windows Mixed Reality**и **UWP**.
4. Выберите **приложение holographic DirectX 11 (универсальные приложения для WindowsC++) (/WinRT)** .
   Снимок экрана ![шаблона проекта приложения UWP с C++шаблоном Windows holographic с помощью DirectX 11 в Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Шаблон проекта приложения UWP C++с DirectX 11/WinRT в Visual Studio 2019*
   >[!IMPORTANT]
   >Убедитесь, что имя шаблона проекта содержит "(C++/WinRT)".  Если нет, то у вас установлена старая версия шаблонов проектов Holographic.  Чтобы получить последние шаблоны проектов, [установите их](install-the-tools.md) в качестве расширения Visual Studio 2019.
5. Нажмите кнопку **Далее**.
5. Заполните текстовые поля **имя проекта** и **Расположение** и нажмите кнопку **создать**. Создается проект holographic приложения.
6. Для разработки, предназначенной только для HoloLens 2, убедитесь, что **Целевая** и **Минимальная версии** установлены на **Windows 10, версия 1903**.  Если вы также нацелены на гарнитуры HoloLens (1-го поколения) или настольные компьютеры Windows Mixed Reality, вы можете установить **минимальную версию** **Windows 10, а не версию 1809** , хотя при использовании новых функций HoloLens 2 в коде потребуется использовать <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">адаптивные проверки версии</a> .
   ![снимок экрана: Настройка Windows 10, версия 1903 в качестве целевой и минимальной версий](images/new-uwp-project.png)<br>
   *Настройка **Windows 10, версии 1903** в качестве целевой и минимальной версий*
   >[!IMPORTANT]
   >Если вы не видите **Windows 10 версии 1903** , вы не установили последнюю версию пакета SDK для Windows 10.  Чтобы отобразить этот параметр, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">установите версию 10.0.18362.0 или более позднюю версию пакета SDK для Windows 10</a>.

Чтобы создать новый проект в Visual Studio 2017, выполните следующие действия.
1. Запустите **Visual Studio**.
2. В меню **файл** наведите указатель мыши на пункт **создать** и выберите **проект** в контекстном меню. Появится диалоговое окно **Создать проект**.
3. Разверните узел **установленные** слева и разверните узел язык **визуального C++**  элемента.
4. Перейдите к узлу **Windows Universal > holographic** и выберите **приложение holographic DirectX 11 (универсальные приложения для Windows) (C++/WinRT)** .
   Снимок экрана ![шаблона проекта приложения UWP с C++шаблоном Windows holographic с помощью DirectX 11 в Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)<br>
   *Шаблон проекта приложения UWP C++с DirectX 11/WinRT в Visual Studio 2017*
   >[!IMPORTANT]
   >Убедитесь, что имя шаблона проекта содержит "(C++/WinRT)".  Если нет, то у вас установлена старая версия шаблонов проектов Holographic.  Чтобы получить последние шаблоны проектов, [установите их](install-the-tools.md) в качестве расширения Visual Studio 2017.
5. Заполните текстовые поля **имя** и **Расположение** и нажмите кнопку **ОК**. Создается проект holographic приложения.
6. Для разработки, предназначенной только для HoloLens 2, убедитесь, что **Целевая** и **Минимальная версии** установлены на **Windows 10, версия 1903**.  Если вы также нацелены на гарнитуры HoloLens (1-го поколения) или настольные компьютеры Windows Mixed Reality, вы можете установить **минимальную версию** **Windows 10, а не версию 1809** , хотя при использовании новых функций HoloLens 2 в коде потребуется использовать <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">адаптивные проверки версии</a> .
   ![снимок экрана: Настройка Windows 10, версия 1903 в качестве целевой и минимальной версий](images/new-uwp-project.png)<br>
   *Настройка **Windows 10, версии 1903** в качестве целевой и минимальной версий*
   >[!IMPORTANT]
   >Если вы не видите **Windows 10 версии 1903** , вы не установили последнюю версию пакета SDK для Windows 10.  Чтобы отобразить этот параметр, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">установите версию 10.0.18362.0 или более позднюю версию пакета SDK для Windows 10</a>.

Шаблон создает проект с помощью <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, c++ 17-языковой проекции Среда выполнения Windows API-интерфейсов, поддерживающих любой стандарт, совместимый с c++ 17 компилятор.  В проекте показано, как создать куб, заблокированный по всему миру, который располагает двумя счетчиками от пользователя. Пользователь может [прикоснуться воздушного](gaze-and-commit.md#composite-gestures) меню или нажать кнопку на контроллере, чтобы поместить куб в другую позицию, указанную с помощью [взгляда](gaze-and-commit.md)пользователя. Вы можете изменить этот проект, чтобы создать любое приложение смешанной реальности.

Кроме того, можно создать новый проект, используя шаблон **проекта C# Visual** holographic, основанный на шарпдкс.  Если C# проект holographic не был запущен из шаблона приложения Windows holographic, необходимо скопировать файл MS. фкскомпиле. targets из проекта шаблона Windows Mixed Reality C# и импортировать его в CSPROJ-файл, чтобы скомпилировать файлы HLSL, добавленные в проект. Шаблон Direct3D 12 также предоставляется в расширении шаблонов приложений Windows Mixed Reality в Visual Studio.

Ознакомьтесь [с разворачиванием и отладкой в Visual Studio](using-visual-studio.md) для получения сведений о том, как создать и развернуть пример на HOLOLENS, ПК с подключенным иммерсивное устройство или в эмуляторе.

В остальных инструкциях ниже предполагается, что вы используете C++ для сборки приложения.

### <a name="uwp-app-entry-point"></a>Точка входа приложения UWP

Приложение holographic с UWP запускается в функции **wWinMain** в аппвиев. cpp. Функция **wWinMain** создает <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> приложения и запускает <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> с ним.

Из **аппвиев. cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

С этого момента класс Аппвиев обрабатывает взаимодействие с событиями ввода Windows Basic, событиями CoreWindow и обменом сообщениями и т. д. Он также создаст Холографикспаце, используемый приложением.

## <a name="creating-a-win32-project"></a>Создание проекта Win32

Самый простой способ приступить к созданию проекта Win32 holographic — адаптировать <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">пример *басичолограм* Win32</a>.

В этом примере Win32 используется <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>— проекция языка c++ 17 интерфейсов Среда выполнения Windows API, поддерживающих любой стандартный компилятор c++ 17.  В проекте показано, как создать куб, заблокированный по всему миру, который располагает двумя счетчиками от пользователя. Пользователь может нажать кнопку на контроллере, чтобы поместить куб в другую позицию, указанную с помощью [взгляда](gaze-and-commit.md)пользователя. Вы можете изменить этот проект, чтобы создать любое приложение смешанной реальности.

### <a name="win32-app-entry-point"></a>Точка входа приложения Win32

Приложение с holographic Win32 запускается в функции **wWinMain** в аппмаин. cpp. Функция **wWinMain** создает HWND приложения и запускает его цикл обработки сообщений.

Из **аппмаин. cpp**:

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

С этого момента класс Аппмаин обрабатывает взаимодействие с основными сообщениями окон и т. д. Он также создаст Холографикспаце, используемый приложением.

## <a name="render-holographic-content"></a>Прорисовка с holographic содержимым

Папка **содержимого** проекта содержит классы для отрисовки голограмм в [holographic пространстве](getting-a-holographicspace.md). Голограмма по умолчанию в шаблоне является вращающимся кубом, который размещается на двух метрах от пользователя. Рисование этого Куба реализовано в **спиннингкуберендерер. cpp**, который имеет следующие ключевые методы:

|  Метод  |  Пояснение | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Загружает шейдеры и создает сетку Куба. | 
|  `PositionHologram` |  Помещает голограмму в расположение, указанное предоставленным <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">спатиалпоинтерпосе</a>. | 
|  `Update` |  Поворачивает куб и задает матрицу модели. | 
|  `Render` |  Визуализирует кадр с помощью шейдеров вершин и пикселей. | 

Вложенная папка **шейдеров** содержит четыре реализации шейдера по умолчанию:

|  Шейдера  |  Пояснение | 
|----------|----------|
|  `GeometryShader.hlsl` |  Сквозной объект, который оставляет геометрию неизменной. | 
|  `PixelShader.hlsl` |  Проходит через данные цвета. Данные цвета интерполируются и назначаются пикселу на шаге растрирования. | 
|  `VertexShader.hlsl` |  Простой шейдер для обработки вершин на GPU. | 
|  `VPRTVertexShader.hlsl` |  Простой шейдер для обработки вершин на GPU, оптимизированный для отображения стереозвука Windows Mixed Reality. | 

`VertexShaderShared.hlsl` содержит общий код, совместно используемый `VertexShader.hlsl` и `VPRTVertexShader.hlsl`.

Примечание. шаблон приложения Direct3D 12 также включает `ViewInstancingVertexShader.hlsl`. Этот вариант использует дополнительные функции D3D12 для более эффективного отображения стерео изображений.

Шейдеры компилируются при построении проекта и загружаются в метод **спиннингкуберендерер:: креатедевицедепендентресаурцес** .

## <a name="interact-with-your-holograms"></a>Взаимодействие с голограммами

Входные данные пользователя обрабатываются в классе **спатиалинпусандлер** , который получает экземпляр <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">спатиалинтерактионманажер</a> и подписывается на событие <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">саурцепрессед</a> . Это позволяет обнаруживать жесты касания и другие пространственные события ввода.

## <a name="update-holographic-content"></a>Обновление holographic

Приложение смешанной реальности обновляется в цикле игры, который по умолчанию реализован в методе **Update** в `AppMain.cpp`. Метод **Update** обновляет объекты сцены, например вращающийся куб, и возвращает объект <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> , который используется для получения актуальных матриц представления и проекции, а также для представления цепочки буферов обмена.

Метод **Render** в `AppMain.cpp` принимает <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> и визуализирует текущий кадр на каждой из holographic камер в соответствии с текущим приложением и состоянием пространственного позиционирования.

## <a name="notes"></a>Примечания

Шаблон приложения Windows Mixed Reality теперь поддерживает компиляцию с включенным флагом защиты устранением рисков Spectre (/Qspectre). Обязательно установите версию библиотек среды выполнения Microsoft Visual C++ (компилятором MSVC) с устранением рисков Spectre-смягчением перед компиляцией конфигурации с включенным устранением устранением рисков Spectre. Чтобы установить C++ библиотеки, снижающие опасность устранением рисков Spectre, запустите Visual Studio Installer и выберите **изменить**. Перейдите к **отдельным компонентам** и выполните поиск по запросу "устранением рисков Spectre". Выберите поля, соответствующие целевым платформам и версии КОМПИЛЯТОРОМ MSVC, для которых необходимо скомпилировать устранением рисков Spectre код для, и нажмите кнопку **изменить** , чтобы начать установку.

## <a name="see-also"></a>См. также:
* [Получение HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">холографикспаце</a>
* [Отрисовка в DirectX](rendering-in-directx.md)
* [Развертывание и отладка с помощью Visual Studio](using-visual-studio.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
* [Использование XAML с голографическими приложениями DirectX](using-xaml-with-holographic-directx-apps.md)
