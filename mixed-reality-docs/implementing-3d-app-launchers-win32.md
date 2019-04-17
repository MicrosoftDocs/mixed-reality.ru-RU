---
title: Реализовать средствах запуска трехмерных приложений (приложения Win32)
description: Как создать средствах запуска приложений 3D и логотипы для Win32 VR-приложений и игр, (распространяемые вне рамок пара) таким образом они отображаются в смешанной реальности Пуск меню и домашней среде.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: Объемные эффекты, логотип, значок, моделирования, средства запуска, 3D запуска, плитки, динамической куба, win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600996"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Реализовать средствах запуска трехмерных приложений (приложения Win32)

> [!NOTE]
> Эта функция доступна только на компьютерах под управлением последней версии [Windows Insider](https://insider.windows.com) рейсов (RS5), сборка 17704 и более поздних версиях.

[Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) является отправной точкой, где пользователи будут располагаться перед запуском приложения. По умолчанию иммерсивных игр и приложений виртуальной Реальности Win32 нужно запускать из за пределами гарнитуры и не будет отображаться в списке «Все приложения» в меню Пуск смешанной реальностью Windows. Тем не менее, следуя инструкциям в этой статье для реализации запуска трехмерного приложения, вашего присутствия Win32 VR можно запустить из меню Windows Пуск смешанной реальности и домашней вычислительной среде.

Это верно только для иммерсивных distributied интерфейсы Win32 VR за пределами поток данных. Для работы в виртуальной Реальности [распространяться с помощью пар](updating-your-steamvr-application-for-windows-mixed-reality.md), мы улучшили [обновлены смешанной реальности Windows для бета-версии SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) вместе с последней RS5 предварительной оценки Windows рейсов, таким образом, чтобы SteamVR названия show копии в Windows Смешанной реальности меню "Пуск" в списке «Все приложения», автоматически с помощью средства запуска по умолчанию. Другими словами метод, описанный в этой статье не нужен для наименований SteamVR и будут переопределены Windows Mixed Reality для функциональных возможностей SteamVR бета-версии.

## <a name="3d-app-launcher-creation-process"></a>Процесс создания приложения трехмерной запуска

Существует 3 шага к созданию запуска трехмерных приложений:
1. [Проектирование и concepting](3d-app-launcher-design-guidance.md)
2. [Моделирование и экспорт](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Интеграции его в приложении (Эта статья)

Трехмерных ресурсов, который будет служить средствах запуска для вашего приложения должен быть создан с использованием [Windows Mixed Reality, руководство по созданию](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) для обеспечения совместимости. Ресурсы, которые не соответствуют этой разработки спецификации, не будет отображаться в Windows Mixed Reality home.

## <a name="configuring-the-3d-launcher"></a>Настройка запуска 3D

Приложения Win32 будут отображаться в списке «Все приложения» в меню Windows Пуск смешанной реальности, при создании средства запуска трехмерных приложений для них. Чтобы сделать это, создайте [манифеста Visual элементы](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML-файл, ссылающиеся на трехмерной средства запуска приложений, сделав следующее:

1. Создание **3D Командной-файла средства запуска приложений** (см. в разделе [моделирования и экспорт](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Создание **[манифеста Visual элементы](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** для вашего приложения.
    1. Вы можете начать с [в следующем примере](#sample-visual-elements-manifest).  Ознакомившись с полным [манифеста Visual элементы](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) документации для получения дополнительных сведений.
    2. Обновление **Square150x150Logo** и **Square70x70Logo** с PNG и JPG или GIF для вашего приложения.
        * Они будут использоваться для 2D логотип приложения в списке Windows смешанной реальности все приложения, а также для меню "Пуск" на рабочем столе.
        * Путь к файлу задается относительно папки, содержащей Visual элементы манифеста.
        * По-прежнему необходимо предоставить на рабочем столе значок меню "Пуск" для вашего приложения через стандартные механизмы. Это может быть непосредственно в исполняемый файл или ярлык, который создан (например, с помощью IShellLink::SetIconLocation).
        * *Необязательно:* Можно воспользоваться файлом resources.pri, при желании для MRT предоставить несколько размеров активов для шкал другое разрешение и темах высокой контрастности.
    3. Обновление **MixedRealityModel путь** указывал на Командной вашей 3D средства запуска приложений
    4. Сохраните файл с именем исполняемого файла, с расширением «. VisualElementsManifest.xml» и сохраните его в том же каталоге. Например для исполняемого файла «contoso.exe», сопутствующий файл XML называется «contoso.visualelementsmanifest.xml».
3. **Добавить ярлык** в приложение для настольных систем Windows меню "Пуск". См. в разделе [в следующем примере](#sample-app-launcher-shortcut-creation) пример C++ реализации. 
    * Создать его в %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (по умолчанию) или %APPDATA%\Microsoft\Windows\Start Menu\Programs (пользователь)
    * Если обновление изменяет манифест визуальные элементы или активы, которые она ссылается, обновления или установки необходимо обновить сочетание таким образом, что манифест является повторный синтаксический анализ и обновляются кэшированных ресурсов.
4. *Необязательно:* Если ярлык на рабочем столе указывает непосредственно на exe-ФАЙЛ приложения (например, в том случае, если он вызывает обработчик пользовательский протокол, например «myapp: / /»), в меню «Пуск» не будет автоматически найти VisualElementsManifest.xml файла приложения. Для решения этой проблемы, сочетание следует указать путь к файлу Visual элементы манифест с помощью System.AppUserModel.VisualElementsManifestHintPath (). Это можно задать в ярлыке, используя те же методы в качестве System.AppUserModel.ID. Вам не обязательно использовать System.AppUserModel.ID, но вы можете при желании для ярлыка для сопоставления явный идентификатор модели пользователя приложения приложения, если он используется.  См. в разделе [пример Создание ярлыка для запуска приложения](#sample-app-launcher-shortcut-creation) приведенном ниже разделе C++ образца.

### <a name="sample-visual-elements-manifest"></a>Пример манифеста визуальных элементов

```xml
<Application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
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

### <a name="sample-app-launcher-shortcut-creation"></a>Создание ярлыков запуска примера приложения

Пример кода ниже показано, как можно создать ярлык в C++, включая переопределение путь к файлу манифеста XML Visual элементы. Обратите внимание, что переопределение требуется только в случаях, где ярлык не указывает непосредственно на EXE-файла, связанное с манифестом, (например) ярлык использует обработчик пользовательский протокол, например «myapp: / /»).

#### <a name="sample-lnk-shortcut-creation-c"></a>Пример. Создание ярлыков LNK (C++)

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

#### <a name="sample-url-launcher-shortcut"></a>Пример. Средство запуска URL-ярлык 

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

* [Образец модели смешанной реальности](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) содержащий запуска трехмерных приложений.
* [Руководство по проектированию приложения трехмерной запуска](3d-app-launcher-design-guidance.md)
* [Создании трехмерных моделей для использования в домашних Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Реализация средствах запуска трехмерных приложений (приложения UWP)](implementing-3d-app-launchers.md)
* [Перемещение Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)
