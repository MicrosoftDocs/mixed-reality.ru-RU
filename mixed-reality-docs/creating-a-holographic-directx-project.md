---
title: Создание проекта с помощью DirectX holographic
description: Описание процесса создания нового приложения holographic на основе шаблона приложения Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holographic приложение, новое приложение, приложение UWP, шаблон приложения, голограммы, новый проект, пошаговое руководство, Загрузка, пример кода
ms.openlocfilehash: 1a6071d692d4a2470493b8f5dc2af6e234aca6f2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435750"
---
# <a name="creating-a-holographic-directx-project"></a>Создание проекта с помощью DirectX holographic

Созданное вами приложение для HoloLens будет иметь <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">универсальная платформа Windows (UWP)</a>.  При нацеливании на Настольные гарнитуры Windows Mixed Reality можно создать приложение UWP или приложение Win32.

Шаблон приложения с DirectX 11 holographic в целом похож на шаблон приложения UWP DirectX 11. Он включает цикл программы (или "игровой цикл"), класс **DeviceResources** для управления устройством и контекстом Direct3D, а также упрощенный класс модуля подготовки содержимого. Он также имеет <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, как и любое другое приложение UWP.

Однако приложение Mixed Reality имеет некоторые дополнительные возможности, отсутствующие в типичном приложении UWP Direct3D 11. Шаблон приложения Windows holographic может:
* Обрабатывайте ресурсы устройства Direct3D, связанные с Holographic.
* Извлечение задних буферов камеры из системы.
* Обработайте входные данные [взгляда](gaze-and-commit.md) и распознают простой [жест](gaze-and-commit.md#composite-gestures).
* Переход к полноэкранному режиму отображения.

## <a name="how-do-i-get-started"></a>Разделы справки начать?

Сначала [установите средства](install-the-tools.md), следуя инструкциям в статье Загрузка Visual Studio 2019 и эмулятора Microsoft HoloLens. Шаблоны holographic приложений включены в тот же установщик, что и эмулятор Microsoft HoloLens. Также убедитесь, что выбран параметр для установки шаблонов перед установкой.

Теперь вы готовы создать приложение Windows Mixed Reality для DirectX 11! Обратите внимание, что для удаления образца содержимого закомментируйте директиву препроцессора **DRAW_SAMPLE_CONTENT** в *PCH. h*.

## <a name="creating-a-uwp-project"></a>Создание проекта UWP

После [установки средств](install-the-tools.md) можно создать проект HOLOGRAPHIC DirectX UWP.

Чтобы создать новый проект, выполните следующие действия.
1. Запустите **Visual Studio**.
2. В меню **файл** наведите указатель мыши на пункт **создать** и выберите **проект** в контекстном меню. Откроется диалоговое окно **Новый проект** .
3. Разверните узел **установленные** слева и разверните узел язык **визуального C++**  элемента.
4. Перейдите к узлу **Windows Universal > holographic** и выберите **приложение holographic DirectX 11 (универсальные приложения для Windows) (C++/WinRT)** .
   Снимок экрана с ![шаблоном проекта приложения C++UWP с помощью DirectX 11/WinRT в Visual Studio](images/holographic-directx-app-cpp-new-project.png)<br>
   *Шаблон проекта приложения UWP C++с DirectX 11/WinRT в Visual Studio*
   >[!IMPORTANT]
   >Убедитесь, что имя шаблона проекта содержит "(C++/WinRT)".  Если нет, то у вас установлена старая версия шаблонов проектов Holographic.  Чтобы получить последние шаблоны проектов, [установите последний эмулятор HoloLens](using-the-hololens-emulator.md).
5. Заполните текстовые поля **имя** и **Расположение** и нажмите кнопку **ОК**. Создается проект holographic приложения.
6. Для разработки, предназначенной только для HoloLens 2, убедитесь, что **Целевая** и **Минимальная версии** установлены на **Windows 10, версия 1903**.  Если вы также настраиваете гарнитуры на основе HoloLens (1-го поколения) или настольных компьютеров Windows Mixed Reality, можно установить **минимальную версию** **Windows 10, а не версию 1809** , хотя это потребует некоторых <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">адаптивных проверок версии</a> в коде при использовании новых функции HoloLens 2.
   ![снимок экрана: Настройка Windows 10, версия 1903 в качестве целевой и минимальной версий](images/new-uwp-project.png)<br>
   *Настройка **Windows 10, версии 1903** в качестве целевой и минимальной версий*
   >[!IMPORTANT]
   >Если вы не видите **Windows 10 версии 1903** , вы не установили последнюю версию пакета SDK для Windows 10.  Чтобы отобразить этот параметр, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">установите версию 10.0.18362.0 или более позднюю версию пакета SDK для Windows 10</a>.

Шаблон создает проект с помощью <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, c++ 17-языковой проекции Среда выполнения Windows API-интерфейсов, поддерживающих любой стандарт, совместимый с c++ 17 компилятор.  В проекте показано, как создать куб, заблокированный по всему миру, который располагает двумя счетчиками от пользователя. Пользователь может [прикоснуться воздушного](gaze-and-commit.md#composite-gestures) меню или нажать кнопку на контроллере, чтобы поместить куб в другую позицию, указанную с помощью [взгляда](gaze-and-commit.md)пользователя. Вы можете изменить этот проект, чтобы создать любое приложение смешанной реальности.

Кроме того, можно создать новый проект, используя шаблон **проекта C# Visual** holographic, основанный на шарпдкс.  Если C# проект holographic не был запущен из шаблона приложения Windows holographic, необходимо скопировать файл MS. фкскомпиле. targets из проекта шаблона Windows Mixed Reality C# и импортировать его в CSPROJ-файл, чтобы скомпилировать HLSL файлы, добавляемые в проект.

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

|  Метод  |  Объяснение | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Загружает шейдеры и создает сетку Куба. | 
|  `PositionHologram` |  Помещает голограмму в расположение, указанное предоставленным <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">спатиалпоинтерпосе</a>. | 
|  `Update` |  Поворачивает куб и задает матрицу модели. | 
|  `Render` |  Визуализирует кадр с помощью шейдеров вершин и пикселей. | 

Вложенная папка **шейдеров** содержит четыре реализации шейдера по умолчанию:

|  Шейдера  |  Объяснение | 
|----------|----------|
|  `GeometryShader.hlsl` |  Сквозной объект, который оставляет геометрию неизменной. | 
|  `PixelShader.hlsl` |  Проходит через данные цвета. Данные цвета интерполируются и назначаются пикселу на шаге растрирования. | 
|  `VertexShader.hlsl` |  Простой шейдер для обработки вершин на GPU. | 
|  `VPRTVertexShader.hlsl` |  Простой шейдер для обработки вершин на GPU, оптимизированный для отображения стереозвука Windows Mixed Reality. | 

`VertexShaderShared.hlsl` содержит общий код, совместно используемый `VertexShader.hlsl` и `VPRTVertexShader.hlsl`.

Шейдеры компилируются при построении проекта и загружаются в метод **спиннингкуберендерер:: креатедевицедепендентресаурцес** .

## <a name="interact-with-your-holograms"></a>Взаимодействие с голограммами

Входные данные пользователя обрабатываются в классе **спатиалинпусандлер** , который получает экземпляр <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">спатиалинтерактионманажер</a> и подписывается на событие <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">саурцепрессед</a> . Это позволяет обнаруживать жесты касания и другие пространственные события ввода.

## <a name="update-holographic-content"></a>Обновление holographic

Приложение смешанной реальности обновляется в цикле игры, который по умолчанию реализован в методе **Update** в `AppMain.cpp`. Метод **Update** обновляет объекты сцены, например вращающийся куб, и возвращает объект <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> , который используется для получения актуальных матриц представления и проекции, а также для представления цепочки буферов обмена.

Метод **Render** в `AppMain.cpp` принимает <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">холографикфраме</a> и визуализирует текущий кадр на каждой из holographic камер в соответствии с текущим приложением и состоянием пространственного позиционирования.

## <a name="see-also"></a>См. также
* [Получение HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">холографикспаце</a>
* [Отрисовка в DirectX](rendering-in-directx.md)
* [Развертывание и отладка с помощью Visual Studio](using-visual-studio.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
* [Использование XAML с голографическими приложениями DirectX](using-xaml-with-holographic-directx-apps.md)
