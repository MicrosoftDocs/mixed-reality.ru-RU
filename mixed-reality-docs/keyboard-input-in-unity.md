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
# <a name="keyboard-input-in-unity"></a>Ввод с клавиатуры в Unity

**Пространство имен:** *UnityEngine*<br>
 **Тип**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Хотя HoloLens поддерживает множество форм ввода, включая клавиатуры Bluetooth, большинство приложений нельзя предполагать, что все пользователи будут иметь доступные физическую клавишу клавиатуры. Если приложение требует ввода текста, должны быть предоставлены определенные виды экранную клавиатуру.

Среда Unity предоставляет *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* класс для приема ввода с клавиатуры, когда доступно не физическую клавишу клавиатуры.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Поведение клавиатуры HoloLens системы в Unity

На HoloLens *TouchScreenKeyboard* использует экранную клавиатуру систему. Экранную клавиатуру компьютера не накладывает поверх объемные представления, поэтому Unity должен создать вторичное представление XAML 2D Показать клавиатуры, а затем вернуться обратно к представлению объемные, после отправки входных данных. Поток пользователя выглядит следующим образом:
1. Пользователь выполняет действия, вызвавшего кода приложения для вызова *TouchScreenKeyboard*
    * Приложение отвечает за состояние приостановки приложения перед вызовом *TouchScreenKeyboard*
    * Приложение может завершиться, прежде чем когда-либо вернуться к объемные представления
2. Unity переключается в двухмерном виде XAML, который автоматически размещаемые в мире
3. Пользователь вводит текст, с помощью клавиатуры системы и отправляет или отменяет
4. Unity переключается обратно к представлению объемные
    * Приложение отвечает за возобновление приложения состояние при *TouchScreenKeyboard* выполняется
5. Отправленный текст будет доступен в *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>Доступных сочетаний представления

Существует шесть различных сочетаний представления:
* Однострочное текстовое поле
* Однострочное текстовое поле с заголовком
* Многострочного текстового поля
* Многострочного текстового поля с заголовком
* Поле пароля однострочный
* Поле пароля одну строку с заголовком

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Включение клавиатуры системы в Unity

Системную клавиатуру HoloLens доступна только для приложений Unity, экспортируемые вместе с «UWP построения тип» значение «XAML». Не лишен недостатков, которые необходимо принять при выборе «XAML» в качестве «UWP создать тип» через «D3D». Если вам неудобно решать эти компромиссы, вы можете изучить [дополнительные ввода решение](#alternative-keyboard-options) с клавиатурой системы.
1. Откройте **файл** меню и выберите **параметры сборки...**
2. Убедитесь, **платформы** присваивается **Windows Store**, **SDK** имеет значение **универсальной 10**и задайте **тип построения универсальной платформы Windows**  для **XAML**.
3. В **параметры построения** диалоговое окно, нажмите кнопку **параметры проигрывателя...**  кнопки
4. Выберите **параметры для Windows Store** вкладку
5. Разверните **другие параметры** группы
6. В **визуализации** установите флажок **поддерживается виртуальной реальности** флажок, чтобы добавить новый **устройств виртуальной реальности** списка
7. Убедитесь, **Windows Holographic** появится в списке пакетов SDK для виртуальной реальности

>[!NOTE]
>Если пользователь не помечает построение как виртуальной реальности поддерживается с устройством, HoloLens, проекта будут экспортированы как двухмерных приложения XAML.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>С помощью системы клавиатуры в приложении Unity

### <a name="declare-the-keyboard"></a>Объявите клавиатуры

В классе, объявите переменную для хранения *TouchScreenKeyboard* и возвращает переменную для хранения строки клавиатуры.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Вызвать клавиатуры

При возникновении события, запрашивающий ввод с клавиатуры, вызовите один из этих функций, в зависимости от типа входных данных требуемого. Обратите внимание, что заголовок указан в параметре textPlaceholder.

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

### <a name="retrieve-typed-contents"></a>Извлечь типизированное содержимое

В цикле обновления проверьте, получено ли клавиатуры новые входные данные и сохранить его для использования в другом месте.

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

## <a name="alternative-keyboard-options"></a>Альтернативные сочетания параметров

Мы понимаем, что исходящему переключению объемные представления в двухмерном виде не идеальный способ получить от пользователя ввода текста.

Текущий альтернативы использованию клавиатуры системы через Unity включают:
* С помощью диктовки речи для входных данных (<b>Примечание:</b> это зачастую подвержено ошибкам для слов, не найден в словаре и не подходит для ввода пароля)
* Создание клавиатуры, который работает в представлении эксклюзивные приложения
