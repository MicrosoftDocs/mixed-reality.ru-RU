---
title: Ввод с клавиатуры в Unity
description: Unity предоставляет класс TouchScreenKeyboard для приема ввода с клавиатуры, когда доступно не физическую клавишу клавиатуры.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: клавиатуры, ввода, unity, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604886"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="f6c8f-104">Ввод с клавиатуры в Unity</span><span class="sxs-lookup"><span data-stu-id="f6c8f-104">Keyboard input in Unity</span></span>

<span data-ttu-id="f6c8f-105">**Пространство имен:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="f6c8f-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="f6c8f-106">**Тип**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="f6c8f-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="f6c8f-107">Хотя HoloLens поддерживает множество форм ввода, включая клавиатуры Bluetooth, большинство приложений нельзя предполагать, что все пользователи будут иметь доступные физическую клавишу клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="f6c8f-108">Если приложение требует ввода текста, должны быть предоставлены определенные виды экранную клавиатуру.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="f6c8f-109">Среда Unity предоставляет *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* класс для приема ввода с клавиатуры, когда доступно не физическую клавишу клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="f6c8f-110">Поведение клавиатуры HoloLens системы в Unity</span><span class="sxs-lookup"><span data-stu-id="f6c8f-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="f6c8f-111">На HoloLens *TouchScreenKeyboard* использует экранную клавиатуру систему.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="f6c8f-112">Экранную клавиатуру компьютера не накладывает поверх объемные представления, поэтому Unity должен создать вторичное представление XAML 2D Показать клавиатуры, а затем вернуться обратно к представлению объемные, после отправки входных данных.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="f6c8f-113">Поток пользователя выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f6c8f-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="f6c8f-114">Пользователь выполняет действия, вызвавшего кода приложения для вызова *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f6c8f-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="f6c8f-115">Приложение отвечает за состояние приостановки приложения перед вызовом *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f6c8f-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="f6c8f-116">Приложение может завершиться, прежде чем когда-либо вернуться к объемные представления</span><span class="sxs-lookup"><span data-stu-id="f6c8f-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="f6c8f-117">Unity переключается в двухмерном виде XAML, который автоматически размещаемые в мире</span><span class="sxs-lookup"><span data-stu-id="f6c8f-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="f6c8f-118">Пользователь вводит текст, с помощью клавиатуры системы и отправляет или отменяет</span><span class="sxs-lookup"><span data-stu-id="f6c8f-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="f6c8f-119">Unity переключается обратно к представлению объемные</span><span class="sxs-lookup"><span data-stu-id="f6c8f-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="f6c8f-120">Приложение отвечает за возобновление приложения состояние при *TouchScreenKeyboard* выполняется</span><span class="sxs-lookup"><span data-stu-id="f6c8f-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="f6c8f-121">Отправленный текст будет доступен в *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f6c8f-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="f6c8f-122">Доступных сочетаний представления</span><span class="sxs-lookup"><span data-stu-id="f6c8f-122">Available keyboard views</span></span>

<span data-ttu-id="f6c8f-123">Существует шесть различных сочетаний представления:</span><span class="sxs-lookup"><span data-stu-id="f6c8f-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="f6c8f-124">Однострочное текстовое поле</span><span class="sxs-lookup"><span data-stu-id="f6c8f-124">Single-line textbox</span></span>
* <span data-ttu-id="f6c8f-125">Однострочное текстовое поле с заголовком</span><span class="sxs-lookup"><span data-stu-id="f6c8f-125">Single-line textbox with title</span></span>
* <span data-ttu-id="f6c8f-126">Многострочного текстового поля</span><span class="sxs-lookup"><span data-stu-id="f6c8f-126">Multi-line textbox</span></span>
* <span data-ttu-id="f6c8f-127">Многострочного текстового поля с заголовком</span><span class="sxs-lookup"><span data-stu-id="f6c8f-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="f6c8f-128">Поле пароля однострочный</span><span class="sxs-lookup"><span data-stu-id="f6c8f-128">Single-line password box</span></span>
* <span data-ttu-id="f6c8f-129">Поле пароля одну строку с заголовком</span><span class="sxs-lookup"><span data-stu-id="f6c8f-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="f6c8f-130">Включение клавиатуры системы в Unity</span><span class="sxs-lookup"><span data-stu-id="f6c8f-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="f6c8f-131">Системную клавиатуру HoloLens доступна только для приложений Unity, экспортируемые вместе с «UWP построения тип» значение «XAML».</span><span class="sxs-lookup"><span data-stu-id="f6c8f-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="f6c8f-132">Не лишен недостатков, которые необходимо принять при выборе «XAML» в качестве «UWP создать тип» через «D3D».</span><span class="sxs-lookup"><span data-stu-id="f6c8f-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="f6c8f-133">Если вам неудобно решать эти компромиссы, вы можете изучить [дополнительные ввода решение](#alternative-keyboard-options) с клавиатурой системы.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="f6c8f-134">Откройте **файл** меню и выберите **параметры сборки...**</span><span class="sxs-lookup"><span data-stu-id="f6c8f-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="f6c8f-135">Убедитесь, **платформы** присваивается **Windows Store**, **SDK** имеет значение **универсальной 10**и задайте **тип построения универсальной платформы Windows**  для **XAML**.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="f6c8f-136">В **параметры построения** диалоговое окно, нажмите кнопку **параметры проигрывателя...**  кнопки</span><span class="sxs-lookup"><span data-stu-id="f6c8f-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="f6c8f-137">Выберите **параметры для Windows Store** вкладку</span><span class="sxs-lookup"><span data-stu-id="f6c8f-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="f6c8f-138">Разверните **другие параметры** группы</span><span class="sxs-lookup"><span data-stu-id="f6c8f-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="f6c8f-139">В **визуализации** установите флажок **поддерживается виртуальной реальности** флажок, чтобы добавить новый **устройств виртуальной реальности** списка</span><span class="sxs-lookup"><span data-stu-id="f6c8f-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="f6c8f-140">Убедитесь, **Windows Holographic** появится в списке пакетов SDK для виртуальной реальности</span><span class="sxs-lookup"><span data-stu-id="f6c8f-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="f6c8f-141">Если пользователь не помечает построение как виртуальной реальности поддерживается с устройством, HoloLens, проекта будут экспортированы как двухмерных приложения XAML.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="f6c8f-142">С помощью системы клавиатуры в приложении Unity</span><span class="sxs-lookup"><span data-stu-id="f6c8f-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="f6c8f-143">Объявите клавиатуры</span><span class="sxs-lookup"><span data-stu-id="f6c8f-143">Declare the keyboard</span></span>

<span data-ttu-id="f6c8f-144">В классе, объявите переменную для хранения *TouchScreenKeyboard* и возвращает переменную для хранения строки клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="f6c8f-145">Вызвать клавиатуры</span><span class="sxs-lookup"><span data-stu-id="f6c8f-145">Invoke the keyboard</span></span>

<span data-ttu-id="f6c8f-146">При возникновении события, запрашивающий ввод с клавиатуры, вызовите один из этих функций, в зависимости от типа входных данных требуемого.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="f6c8f-147">Обратите внимание, что заголовок указан в параметре textPlaceholder.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

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

### <a name="retrieve-typed-contents"></a><span data-ttu-id="f6c8f-148">Извлечь типизированное содержимое</span><span class="sxs-lookup"><span data-stu-id="f6c8f-148">Retrieve typed contents</span></span>

<span data-ttu-id="f6c8f-149">В цикле обновления проверьте, получено ли клавиатуры новые входные данные и сохранить его для использования в другом месте.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

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

## <a name="alternative-keyboard-options"></a><span data-ttu-id="f6c8f-150">Альтернативные сочетания параметров</span><span class="sxs-lookup"><span data-stu-id="f6c8f-150">Alternative keyboard options</span></span>

<span data-ttu-id="f6c8f-151">Мы понимаем, что исходящему переключению объемные представления в двухмерном виде не идеальный способ получить от пользователя ввода текста.</span><span class="sxs-lookup"><span data-stu-id="f6c8f-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="f6c8f-152">Текущий альтернативы использованию клавиатуры системы через Unity включают:</span><span class="sxs-lookup"><span data-stu-id="f6c8f-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="f6c8f-153">С помощью диктовки речи для входных данных (<b>Примечание:</b> это зачастую подвержено ошибкам для слов, не найден в словаре и не подходит для ввода пароля)</span><span class="sxs-lookup"><span data-stu-id="f6c8f-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="f6c8f-154">Создание клавиатуры, который работает в представлении эксклюзивные приложения</span><span class="sxs-lookup"><span data-stu-id="f6c8f-154">Create a keyboard that works in your applications exclusive view</span></span>
