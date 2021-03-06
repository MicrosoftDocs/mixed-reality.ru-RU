---
title: Развертывание и отладка с помощью Visual Studio
description: Узнайте, как создавать, отлаживать и развертывать приложения для HoloLens и Windows Mixed Reality с помощью Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, смешанная реальность, отладка, развертывание
ms.openlocfilehash: 8708ca39460fbd381bd41f5887e1276291f48b07
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "81484324"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Развертывание и отладка с помощью Visual Studio

Независимо от того, что вы хотите использовать для разработки приложения смешанной реальности — DirectX или Unity, для отладки и развертывания будет использоваться Visual Studio. В этом разделе вы научитесь:
* развертывать приложения на иммерсивной гарнитуре HoloLens или Windows Mixed Reality с помощью Visual Studio;
* использовать эмулятор HoloLens, встроенный в Visual Studio;
* отлаживать приложения смешанной реальности.

## <a name="prerequisites"></a>Предварительные условия
1. Инструкции по установке см. в разделе [Установка инструментов](install-the-tools.md).
2. Создайте проект универсального приложения для Windows в Visual Studio.  Для HoloLens (1-го поколения) используйте Visual Studio 2017 или более позднюю версию.  Для HoloLens 2 используйте Visual Studio 2019 16.2 или более позднюю версию. Поддерживаются языки C# и C++. (Вы можете также следовать инструкции по [созданию приложения в Unity](holograms-100.md).)

## <a name="enabling-developer-mode"></a>Включение режима разработчика

Для начала включите **режим разработчика** на устройстве, чтобы среда Visual Studio могла к нему подключиться.

### <a name="hololens"></a>HoloLens
1. Включите устройство HoloLens и наденьте его.
2. Выполните [жест "Пуск"](system-gesture.md), чтобы запустить главное меню.
3. Щелкните плитку **Параметры**, чтобы запустить приложение в среде.
4. Выберите пункт меню **Обновить**.
5. Выберите пункт меню **Для разработчиков**.
6. Включите **Режим разработчика**. Это позволит [развертывать приложения из Visual Studio](using-visual-studio.md) в HoloLens.
7. Дополнительно Прокрутите вниз и включите **Портал устройств**. Это также позволит подключиться к [порталу устройств Windows](using-the-windows-device-portal.md) на HoloLens из веб-браузера.

### <a name="windows-pc"></a>Компьютер с Windows

При работе с гарнитурой Windows Mixed Reality, подключенной к компьютеру, н нем необходимо включить **режим разработчика**.
1. Перейдите в раздел **Параметры**.
2. Выберите **Обновление и безопасность**.
3. Выберите **Для разработчиков**.
4. Включите **Режим разработчика**, прочитайте заявление об отказе от ответственности для выбранного параметра, затем щелкните "Да", чтобы принять изменения.

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>Развертывание приложения по Wi-Fi на HoloLens (1-го поколения)
1. Выберите для приложения конфигурацию сборки **x86**.</br>
![Конфигурация сборки x86 в Visual Studio](images/x86setting.png)</br>
2. Выберите **Удаленный компьютер** в раскрывающемся меню цели развертывания.</br>
![Удаленный компьютер как цель развертывания в Visual Studio](images/remotemachinesetting.png)</br>
3. Для проектов C++ и JavaScript выберите **Проект > Свойства > Свойства конфигурации > Отладка**. Для проектов C# автоматически отобразится диалоговое окно настройки подключения.
  a. Введите IP-адрес своего устройства в поле **Адрес** или **Имя компьютера**. Этот IP-адрес можно найти в HoloLens, выбрав **Settings (Параметры) > Network & Internet (Сеть и Интернет) > Advanced Options (Дополнительные параметры)** . Можно также спросить Кортану: "Какой мой IP-адрес?"
  b. Установите режим проверки подлинности **Универсальный (незашифрованный протокол)** .</br>
  ![Диалоговое окно удаленного подключения в Visual Studio](images/remotedeploy.png)</br>
4. Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</br>
![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)</br>
5. При первом развертывании приложения с компьютера на HoloLens будет предложено ввести ПИН-код. Выполните приведенные ниже инструкции по **связыванию устройства**.

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>Развертывание приложения по Wi-Fi на HoloLens 2
1. Выберите для приложения конфигурацию сборки **ARM** или **ARM64**.</br>
![Конфигурация сборки ARM64 в Visual Studio](images/arm64setting.png)</br>
2. Выберите **Удаленный компьютер** в раскрывающемся меню цели развертывания.</br>
![Удаленный компьютер как цель развертывания в Visual Studio](images/remotemachinesetting_arm64.png)</br>
3. Для проектов C++ и JavaScript выберите **Проект > Свойства > Свойства конфигурации > Отладка**. Для проектов C# автоматически отобразится диалоговое окно настройки подключения.
  a. Введите IP-адрес своего устройства в поле **Адрес** или **Имя компьютера**. Этот IP-адрес можно найти в HoloLens, выбрав **Settings (Параметры) > Network & Internet (Сеть и Интернет) > Advanced Options (Дополнительные параметры)** . Можно также спросить Кортану: "Какой мой IP-адрес?"
  b. Установите режим проверки подлинности **Универсальный (незашифрованный протокол)** .</br>
  ![Диалоговое окно удаленного подключения в Visual Studio](images/remotedeploy.png)</br>
4. Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</br>
![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)</br>
5. При первом развертывании приложения с компьютера на HoloLens будет предложено ввести ПИН-код. Выполните приведенные ниже инструкции по **связыванию устройств**.

Если IP-адрес HoloLens изменится, можно будет изменить IP-адрес целевого компьютера, выбрав **Проект > Свойства > Свойства конфигурации > Отладка**.

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>Развертывание приложения по USB на HoloLens (1-го поколения)
1. Выберите для приложения конфигурацию сборки **x86**.</br>
![Конфигурация сборки x86 в Visual Studio](images/x86setting.png)</br>
2. Выберите **Устройство** в раскрывающемся меню цели развертывания.</br>
![Развертывание устройства в Visual Studio](images/buildsettingsusbdeploy.png)</br>
3. Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</br>
![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)</br>
4. При первом развертывании приложения с компьютера на HoloLens будет предложено ввести ПИН-код. Выполните приведенные ниже инструкции по **связыванию устройства**.

## <a name="deploying-an-app-over-usb---hololens-2"></a>Развертывание приложения по USB на HoloLens 2

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. Выберите для приложения конфигурацию сборки **ARM** или **ARM64**.</br>
![Конфигурация сборки ARM64 в Visual Studio](images/arm64setting.png)</br>
2. Выберите **Устройство** в раскрывающемся меню цели развертывания.</br>
![Развертывание устройства в Visual Studio](images/buildsettingsusbdeploy_arm64.png)</br>
3. Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</br>
![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)</br>
4. При первом развертывании приложения с компьютера на HoloLens будет предложено ввести ПИН-код. Выполните приведенные ниже инструкции по **связыванию устройства**.

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>Развертывание приложения на локальном компьютере, к которому подключена иммерсивная гарнитура

Следуйте этим инструкциям, если вы используете иммерсивную гарнитуру Windows Mixed Reality, которая подключается к компьютеру, или [эмулятор смешанной реальности](using-the-windows-mixed-reality-simulator.md). В этих случаях просто разверните и запустите приложение на локальном компьютере.
1. Выберите для приложения конфигурацию сборки **x86** или **x64**.
2. Выберите **Локальный компьютер** в раскрывающемся меню цели развертывания.
3. Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.

## <a name="pairing-your-device"></a>Связывание устройства

При первом развертывании приложения из Visual Studio на HoloLens будет предложено ввести ПИН-код. На HoloLens создайте ПИН-код, запустив приложение Settings, выберите **Update (Обновление) > For Developers (Для разработчиков)** и коснитесь **Pair** (Связать). Этот ПИН-код будет показан на HoloLens. Введите его в Visual Studio. После завершения связывания коснитесь **Done** (Готово) на HoloLens, чтобы закрыть диалоговое окно. Теперь этот компьютер связан с HoloLens, и вы сможете развертывать приложения автоматически. Повторите эти действия для каждого последующего компьютера, который используется для развертывания приложений в HoloLens.

Чтобы отменить связь HoloLens со всеми компьютерами, с которыми это устройство связано, запустите приложение **Settings**, выберите **Update (Обновление) > For Developers (Для разработчиков)** и коснитесь **Clear** (Очистить).

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>Развертывание приложения в эмуляторе HoloLens (1-го поколения)
1. Убедитесь, что у вас **[установлен эмулятор HoloLens](install-the-tools.md)** .
2. Выберите для приложения конфигурацию сборки **x86**.</br>
![Конфигурация сборки x86 в Visual Studio](images/x86setting.png)</br>
3. Выберите **HoloLens Emulator** (Эмулятор HoloLens) в раскрывающемся меню цели развертывания.</br>
![Эмулятор в качестве цели развертывания в Visual Studio](images/deployemulator.png)</br>
4. Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</br>
![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)</br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>Развертывание приложения в эмуляторе HoloLens 2
1. Убедитесь, что у вас **[установлен эмулятор HoloLens](install-the-tools.md)** .
2. Выберите для приложения конфигурацию сборки **x86** или **x64**.</br>
![Конфигурация сборки x86 в Visual Studio](images/x86setting.png)</br>
3. Выберите **HoloLens 2 Emulator** (Эмулятор HoloLens 2) в раскрывающемся меню цели развертывания.</br>
![Эмулятор в качестве цели развертывания в Visual Studio](images/deployemulator2.png)</br>
4. Выберите **Отладка > Начать отладку**, чтобы развернуть приложение и начать отладку.</br>
![Запуск без отладки в Visual Studio](images/deploywithdebugging.png)</br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Отладчик графики для HoloLens (1-го поколения)

Инструменты диагностики графики Visual Studio очень полезны при создании и оптимизации голографического приложения. Подробные сведения см. в разделе [Диагностика графики в Visual Studio](https://msdn.microsoft.com/library/hh315751.aspx) на сайте MSDN.

**Запуск отладчика графики**
1. Выполните приведенные выше инструкции, чтобы выбрать устройство или эмулятор в качестве цели.
2. Выберите **Отладка > Графика > Начать диагностику**.
3. При первом выполнении этого действия для HoloLens может появиться сообщение об ошибке "Отказано в доступе". Перезагрузите HoloLens, чтобы обновленные разрешения вступили в действие, и повторите попытку.

## <a name="profiling"></a>Профилирование

Инструменты профилирования Visual Studio позволяют анализировать производительность и использование ресурсов приложения. Сюда входят инструменты для оптимизации использования ЦП, памяти, графического процессора и сети. Подробные сведения см. в разделе [Запуск средств диагностики без отладки](https://msdn.microsoft.com/library/dn957936.aspx) на сайте MSDN.

**Запуск инструментов профилирования для HoloLens**
1. Выполните приведенные выше инструкции, чтобы выбрать устройство или эмулятор в качестве цели.
2. Выберите **Отладка > Запустить средства диагностики без отладки**.
3. Выберите инструменты, которые вы хотите использовать.
4. Щелкните **Запустить**.
5. При первом выполнении этого действия для HoloLens может появиться сообщение об ошибке "Отказано в доступе". Перезагрузите HoloLens, чтобы обновленные разрешения вступили в действие, и повторите попытку.

## <a name="debugging-an-installed-or-running-app"></a>Отладка установленного или работающего приложения

Visual Studio можно использовать для отладки универсального приложения для Windows, установленного без развертывания из проекта Visual Studio. Это удобно, если требуется выполнить отладку установленного пакета приложения или уже запущенного приложения.
1. Выберите **Отладка > Другие целевые объекты отладки > Отладка установленного пакета приложения**.
2. Выберите цель **Удаленный компьютер**, если используется HoloLens, или **Локальный компьютер**, если используются иммерсивные гарнитуры.
3. Введите **IP-адрес** устройства.
4. Выберите режим аутентификации **Universal** (Универсальная).
5. В окне отображаются как работающие, так и неактивные приложения. Выберите приложение, которое хотите отладить.
6. Выберите тип отлаживаемого кода (управляемый, собственный, смешанный).
7. Щелкните **Присоединить** или **Запустить**.

## <a name="see-also"></a>См. также статью
* [Установка средств](install-the-tools.md)
* [Использование эмулятора HoloLens](using-the-hololens-emulator.md)
* [Развертывание и отладка приложений универсальной платформы Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [Включение устройства для разработки](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
