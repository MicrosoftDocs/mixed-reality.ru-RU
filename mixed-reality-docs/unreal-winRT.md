---
title: WinRT в Unreal
description: Общие сведения о подключаемом модуле пространственного звука для Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, потоковая передача, удаленное взаимодействие, смешанная реальность, разработка, начало работы, функции, новый проект, эмулятор, документация, руководства, функции, голограммы, разработка игр
ms.openlocfilehash: 7a64002a5fa48bb589ab113f0a8dc1bfcb92d535
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408222"
---
# <a name="winrt-in-unreal"></a>WinRT в Unreal

## <a name="overview"></a>Обзор

В процессе разработки HoloLens может потребоваться написать функцию с помощью WinRT. Например, для открытия диалогового окна файла в приложении HoloLens потребуется Филесавепиккер в файле заголовка WinRT/Windows. Storage.. h.  Поскольку нереальность не компилирует код WinRT в машинном коде, это задание создает отдельный двоичный файл, который может использоваться в нереальной системе сборки. В этом учебнике рассматривается такой сценарий.

## <a name="objectives"></a>Цели
- Создание универсальной библиотеки DLL Windows, которая открывает Филесаведиалогуе
- Связывание библиотеки DLL с нереальным игровым проектом
- Сохранение файла на HoloLens из нереального проекта с помощью новой библиотеки DLL

## <a name="getting-started"></a>Начало работы
1. Убедитесь, что установлены все [необходимые средства](unreal-uxt-ch1.md) .
2. [Создайте новый проект с нереальным](unreal-uxt-ch2.md#creating-a-new-unreal-project) именем и назовите его **консумевинрт**
3. Включение [необходимых подключаемых модулей](unreal-uxt-ch2.md#enabling-required-plugins) для разработки HoloLens
4. [Установка для развертывания](unreal-uxt-ch6.md) на устройстве или в эмуляторе

## <a name="creating-a-winrt-dll"></a>Создание библиотеки DLL WinRT 
1. Откройте новый проект Visual Studio и создайте проект **DLL (универсальные приложения Windows)** в том же каталоге, в котором находится файл **упрожект** нереального игры. 

![Создание библиотеки DLL](images/unreal-winrt-img-01.png)

2. Присвойте проекту имя **хололенсвинртдлл** и задайте расположение в качестве подкаталога **сторонних** для файла упрожект нереальной игры. 
    * Выберите **разместить решение и проект в том же каталоге** , чтобы упростить поиск путей в дальнейшем. 

![Настройка библиотеки DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> После компиляции нового проекта необходимо обратить особое внимание на пустые файлы cpp и Header с именами **хололенсвинртдлл. cpp** и **хололенсвинртдлл. h** соответственно. Заголовок — это включаемый файл, использующий библиотеку DLL в нереальном режиме, в то время как в cpp содержится текст всех экспортируемых функций, а также код WinRT, который в противном случае не может быть скомпилирован. 

3. Перед добавлением кода необходимо обновить свойства проекта, чтобы убедиться, что необходимый код WinRT можно скомпилировать: 
    * Щелкните правой кнопкой мыши проект Хололенсвинртдлл и выберите пункт **Свойства** .  
    * В раскрывающемся списке **Конфигурация** укажите **все конфигурации** и раскрывающийся список **платформа** для **всех платформ** .  
    * В разделе **Свойства конфигурации> C/C++> все параметры**:
        * Добавьте параметр **await** в **Дополнительные параметры** , чтобы убедиться, что мы можем ожидать асинхронные задачи.  
        * Изменение **стандарта языка C++** на **ISO C++ 17 Standard (/std: C++ 17)** для включения любого кода WinRT

![Настройка библиотеки DLL](images/unreal-winrt-img-03.png)

Проект готов к обновлению источника библиотеки DLL с помощью кода WinRT, который открывает диалоговое окно файла и сохраняет файл на диск HoloLens.  

## <a name="adding-the-dll-code"></a>Добавление кода DLL
1. Откройте **хололенсвинртдлл. h** и добавьте экспортированную функцию DLL для использования в нереальном виде: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Откройте **хололенсвинртдлл. cpp** и добавьте все заголовки, которые будет использовать класс:  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> Весь код WinRT хранится в **хололенсвинртдлл. cpp** , поэтому нереально не пытается включить какой-либо код WinRT при ссылке на заголовок. 

3. По-прежнему в **хололенсвинртдлл. cpp**добавьте тело функции для опенфиледиалогуе () и весь поддерживаемый код: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Добавьте класс Савегамеманажер в файл **хололенсвинртдлл. cpp** , чтобы обрабатывал диалоговое окно файла и сохранить файл: 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullprt);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. Постройте решение для **выпуска > ARM64** , чтобы создать библиотеку DLL в дочернем каталоге ARM64/Release/хололенсвинртдлл из решения DLL. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Добавление двоичного файла WinRT в нереалию 
Для связывания и использования библиотеки DLL в нереальном случае требуется проект C++. Если вы используете проект схемы, его можно легко преобразовать в проект C++, добавив класс C++:  

1. В нереальном редакторе откройте **файл > новый класс C++...** и создайте новый **субъект** с именем **винртактор** для запуска кода в библиотеке DLL: 

![Настройка библиотеки DLL](images/unreal-winrt-img-04.png)

> [!NOTE]
> Теперь решение создано в том же каталоге, что и файл упрожект, а также новый скрипт сборки с именем Source/Консумевинрт/Консумервинрт. Build. cs.

2. Откройте решение, найдите папку **Games/консумевинрт/Source/консумевинрт** и откройте **ConsumeWinRT.Build.CS**:

![Настройка библиотеки DLL](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Связывание библиотеки DLL
1. В **ConsumeWinRT.Build.CS**добавьте свойство, чтобы найти путь включения для библиотеки DLL (каталог, содержащий хололенсвинртдлл. h). Библиотека DLL находится в дочернем каталоге с путем include, поэтому это свойство будет использоваться в качестве двоичного корневого каталога:

```cs
public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirddParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. В конструкторе класса добавьте следующий код, чтобы обновить путь включаемых файлов, связать новую библиотеку lib и загрузить отложенную загрузку и скопировать DLL в расположение пакета Appx:

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. Откройте **винртактор. h** и добавьте два определения функций, одну из которых может использовать схема, и другую, которая использует код DLL: 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. Откройте **винртактор. cpp** и загрузите DLL-файл в бегинплай: 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> Библиотека DLL должна быть загружена перед вызовом любой из ее функций.

### <a name="building-the-game"></a>Создание игры
1. Выполните сборку решения игры, чтобы запустить нереальный редактор, Открытый для игрового проекта: 
    * На вкладке **Размещение субъектов** найдите новый **винртактор** и перетащите его в сцену. 
    * Откройте проект уровня, чтобы выполнить вызываемую функцию схемы в **винртактор** . 

![Настройка библиотеки DLL](images/unreal-winrt-img-06.png)

2. В **мировом мире**найдите **виндртактор** , ранее вставленный в сцену, и перетащите его в проект уровня: 

![Настройка библиотеки DLL](images/unreal-winrt-img-07.png)

3. В схеме уровня перетащите выходной узел из Винртактор, найдите **диалоговое окно Открыть файл**, а затем направьте узел от любого пользовательского ввода.  В этом случае диалоговое окно открытия файла вызывается из события речи: 

![Настройка библиотеки DLL](images/unreal-winrt-img-08.png)

4. [Упакуйте эту игру для HoloLens](unreal-uxt-ch6.md), разверните ее и запустите.  

Когда недействительные вызовы Опенфиледиалогуе, открывается диалоговое окно файла на странице HoloLens, в которой запрашивается имя файла. txt.  После сохранения файла перейдите на вкладку " **проводник** " на портале устройств, чтобы просмотреть содержимое "Hello WinRT". 

## <a name="summary"></a>Итоги 

Мы рекомендуем использовать код из этого руководства в качестве отправной точки для использования кода WinRT в нереальном виде.  Он позволяет пользователям сохранять файлы на диск HoloLens, используя тот же диалог, что и Windows.  Выполните те же действия, чтобы экспортировать дополнительные функции из заголовка Хололенсвинртдлл и использовать их в нереальном виде.  Обратите внимание на код DLL, который ожидает любой асинхронный код WinRT в фоновом потоке агента передачи сообщений, что позволяет избежать взаимоблокировки нереального игрового потока. 

## <a name="see-also"></a>См. также раздел
* [API-интерфейсы/WinRT C++](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [Класс Филесавепиккер](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Нереал. сторонние библиотеки](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
