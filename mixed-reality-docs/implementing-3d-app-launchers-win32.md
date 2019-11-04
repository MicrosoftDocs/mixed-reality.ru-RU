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
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="81594-104">Реализация запуска трехмерных приложений (приложения Win32)</span><span class="sxs-lookup"><span data-stu-id="81594-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="81594-105">Эта функция доступна только для компьютеров, на которых выполняются последние авиарейсы по [предварительной версии Windows](https://insider.windows.com) (RS5), сборка 17704 и более поздние версии.</span><span class="sxs-lookup"><span data-stu-id="81594-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="81594-106">[Главная страница Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) — это отправная точка, в которой пользователи начинают работу перед запуском приложений.</span><span class="sxs-lookup"><span data-stu-id="81594-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="81594-107">По умолчанию впечатляющие приложения и игры Win32 VR должны быть запущены за пределами гарнитуры и не будут отображаться в списке "все приложения" в меню "Пуск" Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="81594-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="81594-108">Тем не менее, следуя инструкциям, приведенным в этой статье, чтобы реализовать средство запуска для трехмерных приложений, можно запустить иммерсивное приложение Win32 VR в меню "Пуск" Windows Mixed Reality и в домашней среде.</span><span class="sxs-lookup"><span data-stu-id="81594-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="81594-109">Это справедливо только для захватывающих функций Win32 VR, дистрибутиед за пределами Steam.</span><span class="sxs-lookup"><span data-stu-id="81594-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="81594-110">Для функций VR, [распространяемых через Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), мы [обновили бета-версию Windows Mixed Reality для стеамвр Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) вместе с последними РЕЙСами Windows Insider RS5, чтобы заголовки стеамвр отображались в меню Пуск Windows Mixed Reality в списке "все приложения". автоматическое использование средства запуска по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="81594-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="81594-111">Иными словами, метод, описанный в этой статье, не нужен для заголовков Стеамвр и будет переопределен функцией бета-версии Windows Mixed Reality для Стеамвр.</span><span class="sxs-lookup"><span data-stu-id="81594-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="81594-112">процесс создания средства запуска приложений 3D</span><span class="sxs-lookup"><span data-stu-id="81594-112">3D app launcher creation process</span></span>

<span data-ttu-id="81594-113">Создание средства запуска 3D-приложений состоит из трех этапов.</span><span class="sxs-lookup"><span data-stu-id="81594-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="81594-114">Проектирование и концепция</span><span class="sxs-lookup"><span data-stu-id="81594-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="81594-115">Моделирование и экспорт</span><span class="sxs-lookup"><span data-stu-id="81594-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="81594-116">Интеграция этого приложения в приложение (в этой статье)</span><span class="sxs-lookup"><span data-stu-id="81594-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="81594-117">Трехмерные ресурсы, которые будут использоваться в качестве запуска для приложения, должны быть созданы с использованием [руководств по разработке Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) для обеспечения совместимости.</span><span class="sxs-lookup"><span data-stu-id="81594-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="81594-118">Активы, которые не соответствуют этой спецификации разработки, не будут подготавливаться к просмотру на домашней странице Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="81594-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="81594-119">Настройка средства запуска 3D</span><span class="sxs-lookup"><span data-stu-id="81594-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="81594-120">Приложения Win32 будут отображаться в списке "все приложения" в меню "Пуск" Windows Mixed Reality, если для них создается средство запуска для 3D-приложений.</span><span class="sxs-lookup"><span data-stu-id="81594-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="81594-121">Для этого создайте XML-файл [манифеста визуальных элементов](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) , ссылающийся на средство запуска 3D-приложений, выполнив следующие действия.</span><span class="sxs-lookup"><span data-stu-id="81594-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="81594-122">Создайте **файл GLBA ресурсов средства запуска 3D-приложения** (см. раздел [моделирование и экспорт](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="81594-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="81594-123">Создайте **[Манифест визуальных элементов](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** для приложения.</span><span class="sxs-lookup"><span data-stu-id="81594-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="81594-124">Вы можете начать с [примера ниже](#sample-visual-elements-manifest).</span><span class="sxs-lookup"><span data-stu-id="81594-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="81594-125">Дополнительные сведения см. в документации по полному [манифесту визуальных элементов](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) .</span><span class="sxs-lookup"><span data-stu-id="81594-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="81594-126">Обновите **Square150x150Logo** и **SQUARE70X70LOGO** с помощью PNG/JPG/GIF для своего приложения.</span><span class="sxs-lookup"><span data-stu-id="81594-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="81594-127">Они будут использоваться для 2D-логотипа приложения в списке все приложения Windows Mixed Reality и в меню Пуск на рабочем столе.</span><span class="sxs-lookup"><span data-stu-id="81594-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="81594-128">Путь к файлу задается относительно папки, содержащей манифест визуальных элементов.</span><span class="sxs-lookup"><span data-stu-id="81594-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="81594-129">Вам по-прежнему нужно указать значок меню "Пуск" для приложения с помощью стандартных механизмов.</span><span class="sxs-lookup"><span data-stu-id="81594-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="81594-130">Это может быть либо непосредственно в исполняемом файле, либо в созданном вами ярлыке (например, через Ишелллинк:: Сетиконлокатион).</span><span class="sxs-lookup"><span data-stu-id="81594-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="81594-131">*Необязательно:* Файл Resources. PRI можно использовать, если вы хотите, чтобы MRT предоставил несколько размеров ресурсов для различных масштабов разрешения и высококонтрастных тем.</span><span class="sxs-lookup"><span data-stu-id="81594-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="81594-132">Обновите **путь микседреалитимодел** , чтобы он УКАЗЫВАЛ на GLBA для средства запуска 3D-приложений.</span><span class="sxs-lookup"><span data-stu-id="81594-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="81594-133">Сохраните файл с тем же именем, что и у исполняемого файла, с расширением. Висуалелементсманифест. XML "и сохраните его в том же каталоге.</span><span class="sxs-lookup"><span data-stu-id="81594-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="81594-134">Например, для исполняемого файла "contoso. exe" сопутствующий XML-файл называется contoso. висуалелементсманифест. XML.</span><span class="sxs-lookup"><span data-stu-id="81594-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="81594-135">**Добавьте ярлык** для своего приложения в меню "Пуск" в Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="81594-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="81594-136">Пример C++ реализации см. в [примере ниже](#sample-app-launcher-shortcut-creation) .</span><span class="sxs-lookup"><span data-stu-id="81594-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="81594-137">Создание в%Аллусерспрофиле%\микрософт\виндовс\старт Мену\програмс (Machine) или%Аппдата%\микрософт\виндовс\старт Menu\Programs (User)</span><span class="sxs-lookup"><span data-stu-id="81594-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="81594-138">Если обновление изменяет манифест визуальных элементов или ресурсы, на которые ссылается этот элемент, средство обновления или установщик должно обновить ярлык, чтобы манифест был повторно проанализирован, а кэшированные ресурсы были обновлены.</span><span class="sxs-lookup"><span data-stu-id="81594-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="81594-139">*Необязательно:* Если ярлык на рабочем столе не указывает на ИСПОЛНЯЕМый файл приложения (например, при вызове пользовательского обработчика протокола, например "myapp://"), в меню "Пуск" не будет автоматически найдено приложение Висуалелементсманифест. XML приложения.</span><span class="sxs-lookup"><span data-stu-id="81594-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="81594-140">Чтобы устранить эту проблему, ярлык должен указать путь к файлу манифеста визуальных элементов с помощью System. Аппусермодел. Висуалелементсманифессинтпас ().</span><span class="sxs-lookup"><span data-stu-id="81594-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="81594-141">Это можно задать в ярлыке, используя те же методы, что и System.AppUserModel.ID.</span><span class="sxs-lookup"><span data-stu-id="81594-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="81594-142">Вы не обязаны использовать System.AppUserModel.ID, но вы можете сделать это, если хотите, чтобы сочетание клавиш соответствовало явному ИДЕНТИФИКАТОРу пользовательской модели приложения, если оно используется.</span><span class="sxs-lookup"><span data-stu-id="81594-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="81594-143">Пример см. в разделе [Создание ярлыка для примера запуска приложения](#sample-app-launcher-shortcut-creation) ниже. C++</span><span class="sxs-lookup"><span data-stu-id="81594-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="81594-144">Пример манифеста визуальных элементов</span><span class="sxs-lookup"><span data-stu-id="81594-144">Sample Visual Elements Manifest</span></span>

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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="81594-145">Создание ярлыка для примера запуска приложения</span><span class="sxs-lookup"><span data-stu-id="81594-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="81594-146">В примере кода ниже показано, как можно создать ярлык в C++, включая переопределение пути в XML-файл манифеста визуальных элементов.</span><span class="sxs-lookup"><span data-stu-id="81594-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="81594-147">Обратите внимание, что переопределение требуется только в случаях, когда ярлык не указывает на исполняемый файл, связанный с манифестом (например,</span><span class="sxs-lookup"><span data-stu-id="81594-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="81594-148">в ярлыке используется пользовательский обработчик протокола, например "myapp://".</span><span class="sxs-lookup"><span data-stu-id="81594-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="81594-149">Следующий. Создание ярлыка LNKC++()</span><span class="sxs-lookup"><span data-stu-id="81594-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="81594-150">Следующий. Ярлык средства запуска URL-адреса</span><span class="sxs-lookup"><span data-stu-id="81594-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="81594-151">См. также</span><span class="sxs-lookup"><span data-stu-id="81594-151">See also</span></span>

* <span data-ttu-id="81594-152">[Образец модели Mixed Reality](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) , содержащий средство запуска 3D-приложения.</span><span class="sxs-lookup"><span data-stu-id="81594-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="81594-153">Руководство по проектированию средств запуска трехмерных приложений</span><span class="sxs-lookup"><span data-stu-id="81594-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="81594-154">Создание трехмерных моделей для использования на домашней странице Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="81594-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="81594-155">Реализация запуска трехмерных приложений (приложения UWP)</span><span class="sxs-lookup"><span data-stu-id="81594-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="81594-156">Навигация по дому с технологией Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="81594-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
