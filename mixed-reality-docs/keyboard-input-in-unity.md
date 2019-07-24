---
title: Ввод с клавиатуры в Unity
description: Unity предоставляет класс Таучскринкэйбоард для приема ввода с клавиатуры при отсутствии доступной физической клавиатуры.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: клавиатура, вход, Unity, таучскринкэйбоард
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515739"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="3c8b7-104">Ввод с клавиатуры в Unity</span><span class="sxs-lookup"><span data-stu-id="3c8b7-104">Keyboard input in Unity</span></span>

<span data-ttu-id="3c8b7-105">**Имен** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="3c8b7-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="3c8b7-106">**Тип**: *[таучскринкэйбоард](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="3c8b7-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="3c8b7-107">Хотя HoloLens поддерживает многие виды входных данных, включая клавиатуры Bluetooth, большинство приложений не может предположить, что у всех пользователей есть физическая клавиатура.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="3c8b7-108">Если приложению требуются текстовые входные данные, следует указать некоторые формы на экранной клавиатуре.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="3c8b7-109">Unity предоставляет класс *[таучскринкэйбоард](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* для приема ввода с клавиатуры при отсутствии доступной физической клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="3c8b7-110">Поведение системной клавиатуры HoloLens в Unity</span><span class="sxs-lookup"><span data-stu-id="3c8b7-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="3c8b7-111">В HoloLens *таучскринкэйбоард* использует экранную клавиатуру системы.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="3c8b7-112">Экранная клавиатура системы не может накладываться поверх представления объемные, поэтому Unity должен создать вторичное 2D-представление XAML, чтобы Показать клавиатуру, а затем вернуться к представлению объемные после отправки ввода.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="3c8b7-113">Поток пользователя выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3c8b7-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="3c8b7-114">Пользователь выполняет действие, вызывающее вызов *таучскринкэйбоард* кодом приложения.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="3c8b7-115">Приложение отвечает за приостановку состояния приложения перед вызовом *таучскринкэйбоард*</span><span class="sxs-lookup"><span data-stu-id="3c8b7-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="3c8b7-116">Приложение может завершить работу, прежде чем когда-либо переключиться обратно в представление объемные</span><span class="sxs-lookup"><span data-stu-id="3c8b7-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="3c8b7-117">Unity переключается на 2D-представление XAML, которое размещается в мире</span><span class="sxs-lookup"><span data-stu-id="3c8b7-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="3c8b7-118">Пользователь вводит текст с помощью системной клавиатуры и отправляет или отменяет</span><span class="sxs-lookup"><span data-stu-id="3c8b7-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="3c8b7-119">Unity переключается обратно в представление объемные</span><span class="sxs-lookup"><span data-stu-id="3c8b7-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="3c8b7-120">Приложение отвечает за возобновление состояния приложения после завершения *таучскринкэйбоард*</span><span class="sxs-lookup"><span data-stu-id="3c8b7-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="3c8b7-121">Отправленный текст доступен в *таучскринкэйбоард*</span><span class="sxs-lookup"><span data-stu-id="3c8b7-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="3c8b7-122">Доступные представления клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3c8b7-122">Available keyboard views</span></span>

<span data-ttu-id="3c8b7-123">Доступно шесть различных представлений клавиатуры:</span><span class="sxs-lookup"><span data-stu-id="3c8b7-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="3c8b7-124">Текстовое поле с одной строкой</span><span class="sxs-lookup"><span data-stu-id="3c8b7-124">Single-line textbox</span></span>
* <span data-ttu-id="3c8b7-125">Однострочное текстовое поле с заголовком</span><span class="sxs-lookup"><span data-stu-id="3c8b7-125">Single-line textbox with title</span></span>
* <span data-ttu-id="3c8b7-126">Многострочное текстовое поле</span><span class="sxs-lookup"><span data-stu-id="3c8b7-126">Multi-line textbox</span></span>
* <span data-ttu-id="3c8b7-127">Многострочное текстовое поле с заголовком</span><span class="sxs-lookup"><span data-stu-id="3c8b7-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="3c8b7-128">Поле пароля в одной строке</span><span class="sxs-lookup"><span data-stu-id="3c8b7-128">Single-line password box</span></span>
* <span data-ttu-id="3c8b7-129">Поле однострочного пароля с заголовком</span><span class="sxs-lookup"><span data-stu-id="3c8b7-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="3c8b7-130">Как включить системную клавиатуру в Unity</span><span class="sxs-lookup"><span data-stu-id="3c8b7-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="3c8b7-131">Системная клавиатура HoloLens доступна только для приложений Unity, которые экспортируются с параметром "тип сборки UWP", имеющим значение "XAML".</span><span class="sxs-lookup"><span data-stu-id="3c8b7-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="3c8b7-132">При выборе "XAML" в качестве типа сборки UWP по "D3D" можно использовать компромиссы.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="3c8b7-133">Если вы не знакомы с этими компромиссами, вам может потребоваться изучить альтернативное [решение ввода](#alternative-keyboard-options) для системной клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="3c8b7-134">Откройте меню **файл** и выберите **параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="3c8b7-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="3c8b7-135">Убедитесь, что для **платформы** задано значение **Магазин Windows**, для **пакета SDK** установлено значение **универсальное 10**, а для **типа сборки UWP** — значение **XAML**.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="3c8b7-136">В диалоговом окне **параметры сборки** нажмите кнопку **Параметры проигрывателя...**</span><span class="sxs-lookup"><span data-stu-id="3c8b7-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="3c8b7-137">Перейдите на вкладку **параметры для Магазина Windows** .</span><span class="sxs-lookup"><span data-stu-id="3c8b7-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="3c8b7-138">Разверните группу **другие параметры** .</span><span class="sxs-lookup"><span data-stu-id="3c8b7-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="3c8b7-139">В разделе " **Подготовка** " установите флажок " **Virtual Reality Supported** ", чтобы добавить новый список **устройств виртуальной реальности** .</span><span class="sxs-lookup"><span data-stu-id="3c8b7-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="3c8b7-140">Убедитесь, что **Windows holographic** отображается в списке пакетов SDK виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="3c8b7-141">Если вы не помечаете сборку как виртуальная реальность, поддерживаемая на устройстве HoloLens, проект будет экспортирован в виде 2D-приложения XAML.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="3c8b7-142">Использование системной клавиатуры в приложении Unity</span><span class="sxs-lookup"><span data-stu-id="3c8b7-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="3c8b7-143">Объявление клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3c8b7-143">Declare the keyboard</span></span>

<span data-ttu-id="3c8b7-144">В классе объявите переменную для хранения *таучскринкэйбоард* и переменную для хранения строки, возвращаемой клавиатурой.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="3c8b7-145">Вызов клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3c8b7-145">Invoke the keyboard</span></span>

<span data-ttu-id="3c8b7-146">Когда событие возникает при запросе ввода с клавиатуры, вызовите одну из этих функций в зависимости от требуемого типа входных данных.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="3c8b7-147">Обратите внимание, что заголовок указывается в параметре Текстплацехолдер.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="3c8b7-148">Получение типизированного содержимого</span><span class="sxs-lookup"><span data-stu-id="3c8b7-148">Retrieve typed contents</span></span>

<span data-ttu-id="3c8b7-149">В цикле обновления проверьте, получил ли клавиатура новые входные данные, и сохраните их для использования в других местах.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="3c8b7-150">Альтернативные параметры клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3c8b7-150">Alternative keyboard options</span></span>

<span data-ttu-id="3c8b7-151">Мы понимаем, что переключение объемные представления в двухмерную представление не является идеальным способом получения текстового ввода от пользователя.</span><span class="sxs-lookup"><span data-stu-id="3c8b7-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="3c8b7-152">Текущие альтернативы использованию системной клавиатуры через Unity включают:</span><span class="sxs-lookup"><span data-stu-id="3c8b7-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="3c8b7-153">Использование диктовки речи для ввода данных (<b>Примечание.</b> часто возникает ошибка для слов, не найденных в словаре и не подходящих для ввода пароля).</span><span class="sxs-lookup"><span data-stu-id="3c8b7-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="3c8b7-154">Создание клавиатуры, работающей в монопольном представлении приложений</span><span class="sxs-lookup"><span data-stu-id="3c8b7-154">Create a keyboard that works in your applications exclusive view</span></span>
