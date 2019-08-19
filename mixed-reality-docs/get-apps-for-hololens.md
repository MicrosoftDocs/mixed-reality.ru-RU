---
title: Получение приложений для HoloLens
description: Описывает установку приложений для HoloLens как с помощью Microsoft Store, так и при загрузке с неопубликованными приложениями.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: загружать неопубликованные, Загрузка на стороне сервера, Загрузка, сохранение, UWP, приложение, установка
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522560"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="c8bcb-104">Получение приложений для HoloLens</span><span class="sxs-lookup"><span data-stu-id="c8bcb-104">Get apps for HoloLens</span></span>

<span data-ttu-id="c8bcb-105">Как устройство Windows 10, HoloLens поддерживает множество существующих приложений UWP из магазина приложений, а также новые приложения, разработанные специально для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="c8bcb-106">На самом верху вы можете даже захотеть [разрабатывать](development-overview.md) и устанавливать собственные приложения или их друзей!</span><span class="sxs-lookup"><span data-stu-id="c8bcb-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="c8bcb-107">Установка приложений</span><span class="sxs-lookup"><span data-stu-id="c8bcb-107">Installing Apps</span></span>

<span data-ttu-id="c8bcb-108">Существует три способа установки новых приложений на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="c8bcb-109">Основным методом будет установка новых приложений из Магазина Windows.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="c8bcb-110">Однако вы также можете установить собственные приложения с помощью портала устройства или путем развертывания их из Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="c8bcb-111">Из Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="c8bcb-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="c8bcb-112">Выполните жест [раскрытия](gestures.md#bloom) , чтобы открыть [меню "Пуск](navigating-the-windows-mixed-reality-home.md#start-menu)".</span><span class="sxs-lookup"><span data-stu-id="c8bcb-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="c8bcb-113">Выберите приложение магазина, а затем коснитесь, чтобы поместить плитку в свой мир.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="c8bcb-114">После открытия приложения Магазина используйте панель поиска, чтобы найти нужное приложение.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="c8bcb-115">Выберите **получить** или **установить** на странице приложения (может потребоваться покупка).</span><span class="sxs-lookup"><span data-stu-id="c8bcb-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="c8bcb-116">Установка пакета приложения с помощью портала устройств</span><span class="sxs-lookup"><span data-stu-id="c8bcb-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="c8bcb-117">Установите подключение с [портала устройства](using-the-windows-device-portal.md) к целевому HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="c8bcb-118">Перейдите на страницу **приложения** в левой области навигации.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="c8bcb-119">В разделе **пакет приложения** найдите appx файл, связанный с вашим приложением.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="c8bcb-120">Обязательно сослаться на все связанные файлы зависимостей и сертификатов.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="c8bcb-121">Нажмите кнопку **Go (начать**).</span><span class="sxs-lookup"><span data-stu-id="c8bcb-121">Click **Go**.</span></span>

<span data-ttu-id="c8bcb-122">![Установка формы приложения на портале устройств Windows в Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="c8bcb-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="c8bcb-123">Использование портала устройств Windows для установки приложения в HoloLens</span><span class="sxs-lookup"><span data-stu-id="c8bcb-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="c8bcb-124">Развертывание из Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="c8bcb-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="c8bcb-125">Откройте решение Visual Studio приложения (SLN-файл).</span><span class="sxs-lookup"><span data-stu-id="c8bcb-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="c8bcb-126">Откройте **Свойства** проекта.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="c8bcb-127">Выберите следующую конфигурацию сборки: Master/x86/удаленный компьютер.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="c8bcb-128">При выборе удаленного компьютера:</span><span class="sxs-lookup"><span data-stu-id="c8bcb-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="c8bcb-129">Убедитесь, что адрес указывает на IP-адрес WiFi.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="c8bcb-130">Задайте для параметра Проверка подлинности значение универсальный (незашифрованный протокол).</span><span class="sxs-lookup"><span data-stu-id="c8bcb-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="c8bcb-131">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-131">Build your solution.</span></span>
6. <span data-ttu-id="c8bcb-132">Нажмите кнопку **Удаленный компьютер** , чтобы развернуть приложение с компьютера разработчика на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="c8bcb-133">Если у вас уже есть сборка на HoloLens, нажмите кнопку Да для повторной установки этой новой версии.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="c8bcb-134">![Развертывание удаленного компьютера для приложений в Microsoft HoloLens в Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="c8bcb-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="c8bcb-135">Приложение будет установлено и запущено на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c8bcb-135">The application will install and auto launch on your HoloLens.</span></span>
