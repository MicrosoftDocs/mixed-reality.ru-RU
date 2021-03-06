---
title: Ввод с клавиатуры в Unity
description: Unity предоставляет класс Таучскринкэйбоард для приема ввода с клавиатуры при отсутствии доступной физической клавиатуры.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: клавиатура, вход, Unity, таучскринкэйбоард
ms.openlocfilehash: f506415f9658d9723bf31b339d63fe4569100ace
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438560"
---
# <a name="keyboard-input-in-unity"></a>Ввод с клавиатуры в Unity

**Пространство имен:** *UnityEngine*<br>
 **Тип**:  *[таучскринкэйбоард](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Хотя HoloLens поддерживает многие виды входных данных, включая клавиатуры Bluetooth, большинство приложений не может предположить, что у всех пользователей есть физическая клавиатура. Если приложению требуются текстовые входные данные, следует указать некоторые формы на экранной клавиатуре.

Unity предоставляет класс *[таучскринкэйбоард](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* для приема ввода с клавиатуры при отсутствии доступной физической клавиатуры.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Поведение системной клавиатуры HoloLens в Unity

В HoloLens *таучскринкэйбоард* использует экранную клавиатуру системы. Экранная клавиатура системы не может накладываться поверх представления объемные, поэтому Unity должен создать вторичное 2D-представление XAML, чтобы Показать клавиатуру, а затем вернуться к представлению объемные после отправки ввода. Поток пользователя выглядит следующим образом:
1. Пользователь выполняет действие, вызывающее вызов *таучскринкэйбоард* кодом приложения.
    * Приложение отвечает за приостановку состояния приложения перед вызовом *таучскринкэйбоард*
    * Приложение может завершить работу, прежде чем когда-либо переключиться обратно в представление объемные
2. Unity переключается на 2D-представление XAML, которое размещается в мире
3. Пользователь вводит текст с помощью системной клавиатуры и отправляет или отменяет
4. Unity переключается обратно в представление объемные
    * Приложение отвечает за возобновление состояния приложения после завершения *таучскринкэйбоард*
5. Отправленный текст доступен в *таучскринкэйбоард*

### <a name="available-keyboard-views"></a>Доступные представления клавиатуры

Доступно шесть различных представлений клавиатуры:
* Текстовое поле с одной строкой
* Однострочное текстовое поле с заголовком
* Многострочное текстовое поле
* Многострочное текстовое поле с заголовком
* Поле пароля в одной строке
* Поле однострочного пароля с заголовком

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Как включить системную клавиатуру в Unity

Системная клавиатура HoloLens доступна только для приложений Unity, которые экспортируются с параметром "тип сборки UWP", имеющим значение "XAML". При выборе "XAML" в качестве типа сборки UWP по "D3D" можно использовать компромиссы. Если вы не знакомы с этими компромиссами, вам может потребоваться изучить [альтернативное решение ввода](#alternative-keyboard-options) для системной клавиатуры.
1. Откройте меню **файл** и выберите **параметры сборки...**
2. Убедитесь, что для **платформы** задано значение **Магазин Windows**, для **пакета SDK** установлено значение **универсальное 10**, а для **типа сборки UWP** — значение **XAML**.
3. В диалоговом окне **параметры сборки** нажмите кнопку **Параметры проигрывателя...**
4. Перейдите на вкладку **параметры для Магазина Windows** .
5. Разверните группу **другие параметры** .
6. В разделе " **Подготовка** " установите флажок " **Virtual Reality Supported** ", чтобы добавить новый список **устройств виртуальной реальности** .
7. Убедитесь, что **Windows holographic** отображается в списке пакетов SDK виртуальной реальности.

>[!NOTE]
>Если вы не помечаете сборку как виртуальная реальность, поддерживаемая на устройстве HoloLens, проект будет экспортирован в виде 2D-приложения XAML.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Использование системной клавиатуры в приложении Unity

### <a name="declare-the-keyboard"></a>Объявление клавиатуры

В классе объявите переменную для хранения *таучскринкэйбоард* и переменную для хранения строки, возвращаемой клавиатурой.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Вызов клавиатуры

Когда событие возникает при запросе ввода с клавиатуры, вызовите одну из этих функций в зависимости от требуемого типа входных данных. Обратите внимание, что заголовок указывается в параметре Текстплацехолдер.

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

### <a name="retrieve-typed-contents"></a>Получение типизированного содержимого

В цикле обновления проверьте, получил ли клавиатура новые входные данные, и сохраните их для использования в других местах.

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

## <a name="alternative-keyboard-options"></a>Альтернативные параметры клавиатуры

Мы понимаем, что переключение объемные представления в двухмерную представление не является идеальным способом получения текстового ввода от пользователя.

Текущие альтернативы использованию системной клавиатуры через Unity включают:
* Использование диктовки речи для ввода данных (<b>Примечание.</b> часто возникает ошибка для слов, не найденных в словаре и не подходящих для ввода пароля).
* Создание клавиатуры, работающей в монопольном представлении приложений
