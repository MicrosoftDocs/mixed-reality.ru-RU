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
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="0273a-104">Реализовать средствах запуска трехмерных приложений (приложения Win32)</span><span class="sxs-lookup"><span data-stu-id="0273a-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="0273a-105">Эта функция доступна только на компьютерах под управлением последней версии [Windows Insider](https://insider.windows.com) рейсов (RS5), сборка 17704 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="0273a-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="0273a-106">[Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md) является отправной точкой, где пользователи будут располагаться перед запуском приложения.</span><span class="sxs-lookup"><span data-stu-id="0273a-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="0273a-107">По умолчанию иммерсивных игр и приложений виртуальной Реальности Win32 нужно запускать из за пределами гарнитуры и не будет отображаться в списке «Все приложения» в меню Пуск смешанной реальностью Windows.</span><span class="sxs-lookup"><span data-stu-id="0273a-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="0273a-108">Тем не менее, следуя инструкциям в этой статье для реализации запуска трехмерного приложения, вашего присутствия Win32 VR можно запустить из меню Windows Пуск смешанной реальности и домашней вычислительной среде.</span><span class="sxs-lookup"><span data-stu-id="0273a-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="0273a-109">Это верно только для иммерсивных distributied интерфейсы Win32 VR за пределами поток данных.</span><span class="sxs-lookup"><span data-stu-id="0273a-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="0273a-110">Для работы в виртуальной Реальности [распространяться с помощью пар](updating-your-steamvr-application-for-windows-mixed-reality.md), мы улучшили [обновлены смешанной реальности Windows для бета-версии SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) вместе с последней RS5 предварительной оценки Windows рейсов, таким образом, чтобы SteamVR названия show копии в Windows Смешанной реальности меню "Пуск" в списке «Все приложения», автоматически с помощью средства запуска по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0273a-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="0273a-111">Другими словами метод, описанный в этой статье не нужен для наименований SteamVR и будут переопределены Windows Mixed Reality для функциональных возможностей SteamVR бета-версии.</span><span class="sxs-lookup"><span data-stu-id="0273a-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="0273a-112">Процесс создания приложения трехмерной запуска</span><span class="sxs-lookup"><span data-stu-id="0273a-112">3D app launcher creation process</span></span>

<span data-ttu-id="0273a-113">Существует 3 шага к созданию запуска трехмерных приложений:</span><span class="sxs-lookup"><span data-stu-id="0273a-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="0273a-114">Проектирование и concepting</span><span class="sxs-lookup"><span data-stu-id="0273a-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="0273a-115">Моделирование и экспорт</span><span class="sxs-lookup"><span data-stu-id="0273a-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="0273a-116">Интеграции его в приложении (Эта статья)</span><span class="sxs-lookup"><span data-stu-id="0273a-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="0273a-117">Трехмерных ресурсов, который будет служить средствах запуска для вашего приложения должен быть создан с использованием [Windows Mixed Reality, руководство по созданию](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) для обеспечения совместимости.</span><span class="sxs-lookup"><span data-stu-id="0273a-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="0273a-118">Ресурсы, которые не соответствуют этой разработки спецификации, не будет отображаться в Windows Mixed Reality home.</span><span class="sxs-lookup"><span data-stu-id="0273a-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="0273a-119">Настройка запуска 3D</span><span class="sxs-lookup"><span data-stu-id="0273a-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="0273a-120">Приложения Win32 будут отображаться в списке «Все приложения» в меню Windows Пуск смешанной реальности, при создании средства запуска трехмерных приложений для них.</span><span class="sxs-lookup"><span data-stu-id="0273a-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="0273a-121">Чтобы сделать это, создайте [манифеста Visual элементы](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML-файл, ссылающиеся на трехмерной средства запуска приложений, сделав следующее:</span><span class="sxs-lookup"><span data-stu-id="0273a-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="0273a-122">Создание **3D Командной-файла средства запуска приложений** (см. в разделе [моделирования и экспорт](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="0273a-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="0273a-123">Создание **[манифеста Visual элементы](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="0273a-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="0273a-124">Вы можете начать с [в следующем примере](#sample-visual-elements-manifest).</span><span class="sxs-lookup"><span data-stu-id="0273a-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="0273a-125">Ознакомившись с полным [манифеста Visual элементы](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) документации для получения дополнительных сведений.</span><span class="sxs-lookup"><span data-stu-id="0273a-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="0273a-126">Обновление **Square150x150Logo** и **Square70x70Logo** с PNG и JPG или GIF для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="0273a-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="0273a-127">Они будут использоваться для 2D логотип приложения в списке Windows смешанной реальности все приложения, а также для меню "Пуск" на рабочем столе.</span><span class="sxs-lookup"><span data-stu-id="0273a-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="0273a-128">Путь к файлу задается относительно папки, содержащей Visual элементы манифеста.</span><span class="sxs-lookup"><span data-stu-id="0273a-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="0273a-129">По-прежнему необходимо предоставить на рабочем столе значок меню "Пуск" для вашего приложения через стандартные механизмы.</span><span class="sxs-lookup"><span data-stu-id="0273a-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="0273a-130">Это может быть непосредственно в исполняемый файл или ярлык, который создан (например, с помощью IShellLink::SetIconLocation).</span><span class="sxs-lookup"><span data-stu-id="0273a-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="0273a-131">*Необязательно:* Можно воспользоваться файлом resources.pri, при желании для MRT предоставить несколько размеров активов для шкал другое разрешение и темах высокой контрастности.</span><span class="sxs-lookup"><span data-stu-id="0273a-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="0273a-132">Обновление **MixedRealityModel путь** указывал на Командной вашей 3D средства запуска приложений</span><span class="sxs-lookup"><span data-stu-id="0273a-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="0273a-133">Сохраните файл с именем исполняемого файла, с расширением «. VisualElementsManifest.xml» и сохраните его в том же каталоге.</span><span class="sxs-lookup"><span data-stu-id="0273a-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="0273a-134">Например для исполняемого файла «contoso.exe», сопутствующий файл XML называется «contoso.visualelementsmanifest.xml».</span><span class="sxs-lookup"><span data-stu-id="0273a-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="0273a-135">**Добавить ярлык** в приложение для настольных систем Windows меню "Пуск".</span><span class="sxs-lookup"><span data-stu-id="0273a-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="0273a-136">См. в разделе [в следующем примере](#sample-app-launcher-shortcut-creation) пример C++ реализации.</span><span class="sxs-lookup"><span data-stu-id="0273a-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="0273a-137">Создать его в %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (по умолчанию) или %APPDATA%\Microsoft\Windows\Start Menu\Programs (пользователь)</span><span class="sxs-lookup"><span data-stu-id="0273a-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="0273a-138">Если обновление изменяет манифест визуальные элементы или активы, которые она ссылается, обновления или установки необходимо обновить сочетание таким образом, что манифест является повторный синтаксический анализ и обновляются кэшированных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0273a-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="0273a-139">*Необязательно:* Если ярлык на рабочем столе указывает непосредственно на exe-ФАЙЛ приложения (например, в том случае, если он вызывает обработчик пользовательский протокол, например «myapp: / /»), в меню «Пуск» не будет автоматически найти VisualElementsManifest.xml файла приложения.</span><span class="sxs-lookup"><span data-stu-id="0273a-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="0273a-140">Для решения этой проблемы, сочетание следует указать путь к файлу Visual элементы манифест с помощью System.AppUserModel.VisualElementsManifestHintPath ().</span><span class="sxs-lookup"><span data-stu-id="0273a-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="0273a-141">Это можно задать в ярлыке, используя те же методы в качестве System.AppUserModel.ID.</span><span class="sxs-lookup"><span data-stu-id="0273a-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="0273a-142">Вам не обязательно использовать System.AppUserModel.ID, но вы можете при желании для ярлыка для сопоставления явный идентификатор модели пользователя приложения приложения, если он используется.</span><span class="sxs-lookup"><span data-stu-id="0273a-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="0273a-143">См. в разделе [пример Создание ярлыка для запуска приложения](#sample-app-launcher-shortcut-creation) приведенном ниже разделе C++ образца.</span><span class="sxs-lookup"><span data-stu-id="0273a-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="0273a-144">Пример манифеста визуальных элементов</span><span class="sxs-lookup"><span data-stu-id="0273a-144">Sample Visual Elements Manifest</span></span>

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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="0273a-145">Создание ярлыков запуска примера приложения</span><span class="sxs-lookup"><span data-stu-id="0273a-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="0273a-146">Пример кода ниже показано, как можно создать ярлык в C++, включая переопределение путь к файлу манифеста XML Visual элементы.</span><span class="sxs-lookup"><span data-stu-id="0273a-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="0273a-147">Обратите внимание, что переопределение требуется только в случаях, где ярлык не указывает непосредственно на EXE-файла, связанное с манифестом, (например)</span><span class="sxs-lookup"><span data-stu-id="0273a-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="0273a-148">ярлык использует обработчик пользовательский протокол, например «myapp: / /»).</span><span class="sxs-lookup"><span data-stu-id="0273a-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="0273a-149">Пример. Создание ярлыков LNK (C++)</span><span class="sxs-lookup"><span data-stu-id="0273a-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="0273a-150">Пример. Средство запуска URL-ярлык</span><span class="sxs-lookup"><span data-stu-id="0273a-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="0273a-151">См. также</span><span class="sxs-lookup"><span data-stu-id="0273a-151">See also</span></span>

* <span data-ttu-id="0273a-152">[Образец модели смешанной реальности](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) содержащий запуска трехмерных приложений.</span><span class="sxs-lookup"><span data-stu-id="0273a-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="0273a-153">Руководство по проектированию приложения трехмерной запуска</span><span class="sxs-lookup"><span data-stu-id="0273a-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="0273a-154">Создании трехмерных моделей для использования в домашних Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="0273a-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="0273a-155">Реализация средствах запуска трехмерных приложений (приложения UWP)</span><span class="sxs-lookup"><span data-stu-id="0273a-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="0273a-156">Перемещение Windows Mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="0273a-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
