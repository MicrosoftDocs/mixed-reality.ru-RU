---
title: Реализация запуска трехмерных приложений (приложения Win32)
description: Как создать трехмерные программы запуска и логотипы для приложений и игр Win32 VR (распределенных за пределами Steam), чтобы они отображались в меню "Пуск" Windows Mixed Reality и в домашней среде.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Эмблема, значок, моделирование, средство запуска, трехмерное средство запуска, плитка, динамический куб, Win32
ms.openlocfilehash: 87eadfb5184f9fb5f8d513ab00a2a954e71df376
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438575"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Реализация запуска трехмерных приложений (приложения Win32)

> [!NOTE]
> Эта функция доступна только для компьютеров, на которых выполняются последние авиарейсы по [предварительной версии Windows](https://insider.windows.com) (RS5), сборка 17704 и более поздние версии.

[Главная страница Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) — это отправная точка, в которой пользователи начинают работу перед запуском приложений. По умолчанию впечатляющие приложения и игры Win32 VR должны быть запущены за пределами гарнитуры и не будут отображаться в списке "все приложения" в меню "Пуск" Windows Mixed Reality. Тем не менее, следуя инструкциям, приведенным в этой статье, чтобы реализовать средство запуска для трехмерных приложений, можно запустить иммерсивное приложение Win32 VR в меню "Пуск" Windows Mixed Reality и в домашней среде.

Это справедливо только для захватывающих функций Win32 VR, дистрибутиед за пределами Steam. Для функций VR, [распространяемых через Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), мы [обновили бета-версию Windows Mixed Reality для стеамвр Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) вместе с последними РЕЙСами Windows Insider RS5, чтобы заголовки стеамвр отображались в меню Пуск Windows Mixed Reality в списке "все приложения". автоматическое использование средства запуска по умолчанию. Иными словами, метод, описанный в этой статье, не нужен для заголовков Стеамвр и будет переопределен функцией бета-версии Windows Mixed Reality для Стеамвр.

## <a name="3d-app-launcher-creation-process"></a>процесс создания средства запуска приложений 3D

Создание средства запуска 3D-приложений состоит из трех этапов.
1. [Проектирование и концепция](3d-app-launcher-design-guidance.md)
2. [Моделирование и экспорт](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Интеграция этого приложения в приложение (в этой статье)

Трехмерные ресурсы, которые будут использоваться в качестве запуска для приложения, должны быть созданы с использованием [руководств по разработке Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) для обеспечения совместимости. Активы, которые не соответствуют этой спецификации разработки, не будут подготавливаться к просмотру на домашней странице Windows Mixed Reality.

## <a name="configuring-the-3d-launcher"></a>Настройка средства запуска 3D

Приложения Win32 будут отображаться в списке "все приложения" в меню "Пуск" Windows Mixed Reality, если для них создается средство запуска для 3D-приложений. Для этого создайте XML-файл [манифеста визуальных элементов](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) , ссылающийся на средство запуска 3D-приложений, выполнив следующие действия.

1. Создайте **файл GLBA ресурсов средства запуска 3D-приложения** (см. раздел [моделирование и экспорт](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Создайте **[Манифест визуальных элементов](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** для приложения.
    1. Вы можете начать с [примера ниже](#sample-visual-elements-manifest).  Дополнительные сведения см. в документации по полному [манифесту визуальных элементов](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) .
    2. Обновите **Square150x150Logo** и **SQUARE70X70LOGO** с помощью PNG/JPG/GIF для своего приложения.
        * Они будут использоваться для 2D-логотипа приложения в списке все приложения Windows Mixed Reality и в меню Пуск на рабочем столе.
        * Путь к файлу задается относительно папки, содержащей манифест визуальных элементов.
        * Вам по-прежнему нужно указать значок меню "Пуск" для приложения с помощью стандартных механизмов. Это может быть либо непосредственно в исполняемом файле, либо в созданном вами ярлыке (например, через Ишелллинк:: Сетиконлокатион).
        * *Необязательно:* Файл Resources. PRI можно использовать, если вы хотите, чтобы MRT предоставил несколько размеров ресурсов для различных масштабов разрешения и высококонтрастных тем.
    3. Обновите **путь микседреалитимодел** , чтобы он УКАЗЫВАЛ на GLBA для средства запуска 3D-приложений.
    4. Сохраните файл с тем же именем, что и у исполняемого файла, с расширением. Висуалелементсманифест. XML "и сохраните его в том же каталоге. Например, для исполняемого файла "contoso. exe" сопутствующий XML-файл называется contoso. висуалелементсманифест. XML.
3. **Добавьте ярлык** для своего приложения в меню "Пуск" в Windows Desktop. Пример C++ реализации см. в [примере ниже](#sample-app-launcher-shortcut-creation) . 
    * Создание в%Аллусерспрофиле%\микрософт\виндовс\старт Мену\програмс (Machine) или%Аппдата%\микрософт\виндовс\старт Menu\Programs (User)
    * Если обновление изменяет манифест визуальных элементов или ресурсы, на которые ссылается этот элемент, средство обновления или установщик должно обновить ярлык, чтобы манифест был повторно проанализирован, а кэшированные ресурсы были обновлены.
4. *Необязательно:* Если ярлык на рабочем столе не указывает на ИСПОЛНЯЕМый файл приложения (например, при вызове пользовательского обработчика протокола, например "myapp://"), в меню "Пуск" не будет автоматически найдено приложение Висуалелементсманифест. XML приложения. Чтобы устранить эту проблему, ярлык должен указать путь к файлу манифеста визуальных элементов с помощью System. Аппусермодел. Висуалелементсманифессинтпас (). Это можно задать в ярлыке, используя те же методы, что и System.AppUserModel.ID. Вы не обязаны использовать System.AppUserModel.ID, но вы можете сделать это, если хотите, чтобы сочетание клавиш соответствовало явному ИДЕНТИФИКАТОРу пользовательской модели приложения, если оно используется.  Пример см. в разделе [Создание ярлыка для примера запуска приложения](#sample-app-launcher-shortcut-creation) ниже. C++

### <a name="sample-visual-elements-manifest"></a>Пример манифеста визуальных элементов

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>Создание ярлыка для примера запуска приложения

В примере кода ниже показано, как можно создать ярлык в C++, включая переопределение пути в XML-файл манифеста визуальных элементов. Обратите внимание, что переопределение требуется только в случаях, когда ярлык не указывает на исполняемый файл, связанный с манифестом (например, в ярлыке используется пользовательский обработчик протокола, например "myapp://".

#### <a name="sample-lnk-shortcut-creation-c"></a>Следующий. Создание ярлыка LNKC++()

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>Следующий. Ярлык средства запуска URL-адреса 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>См. также

* [Образец модели Mixed Reality](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) , содержащий средство запуска 3D-приложения.
* [Руководство по проектированию средств запуска трехмерных приложений](3d-app-launcher-design-guidance.md)
* [Создание трехмерных моделей для использования на домашней странице Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Реализация запуска трехмерных приложений (приложения UWP)](implementing-3d-app-launchers.md)
* [Навигация по дому с технологией Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
