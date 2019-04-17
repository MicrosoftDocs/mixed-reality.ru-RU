---
title: Получить приложения для HoloLens
description: Описывает установку приложений для HoloLens, как с помощью Microsoft Store и загрузки неопубликованных приложений.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Загрузка неопубликованных, нагрузки на стороне, загрузить неопубликованными, магазин, универсальной платформы Windows, приложения, установка
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597556"
---
# <a name="get-apps-for-hololens"></a><span data-ttu-id="85c6e-104">Получить приложения для HoloLens</span><span class="sxs-lookup"><span data-stu-id="85c6e-104">Get apps for HoloLens</span></span>

<span data-ttu-id="85c6e-105">Как устройство Windows 10 HoloLens поддерживает многих существующих приложений универсальной платформы Windows из магазина приложений, а также новые приложения, созданный специально для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85c6e-105">As a Windows 10 device, HoloLens supports many existing UWP applications from the app store, as well as new apps built specifically for HoloLens.</span></span> <span data-ttu-id="85c6e-106">Поверх этих, вы даже можете [разрабатывать](development-overview.md) и установки приложений или их своим друзьям!</span><span class="sxs-lookup"><span data-stu-id="85c6e-106">On top of these, you may even want to [develop](development-overview.md) and install your own apps or those of your friends!</span></span>

## <a name="installing-apps"></a><span data-ttu-id="85c6e-107">Установка приложений</span><span class="sxs-lookup"><span data-stu-id="85c6e-107">Installing Apps</span></span>

<span data-ttu-id="85c6e-108">Для установки новых приложений на вашей HoloLens тремя способами.</span><span class="sxs-lookup"><span data-stu-id="85c6e-108">There are three ways to install new apps on your HoloLens.</span></span> <span data-ttu-id="85c6e-109">Для установки новых приложений из Windows Store будет первым методом.</span><span class="sxs-lookup"><span data-stu-id="85c6e-109">The primary method will be to install new applications from the Windows Store.</span></span> <span data-ttu-id="85c6e-110">Тем не менее, можно также установить приложения с помощью портала устройства или развернуть их из Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85c6e-110">However, you can also install your own applications using either the Device Portal or by deploying them from Visual Studio.</span></span>

### <a name="from-the-microsoft-store"></a><span data-ttu-id="85c6e-111">Из Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="85c6e-111">From the Microsoft Store</span></span>
1. <span data-ttu-id="85c6e-112">Выполните [Блума](gestures.md#bloom) жестов, чтобы открыть [меню "Пуск"](navigating-the-windows-mixed-reality-home.md#start-menu).</span><span class="sxs-lookup"><span data-stu-id="85c6e-112">Perform a [bloom](gestures.md#bloom) gesture to open the [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="85c6e-113">Выберите приложение Store, а затем нажмите на размещение этой плитки в ваш мир.</span><span class="sxs-lookup"><span data-stu-id="85c6e-113">Select the Store app and then tap to place this tile into your world.</span></span>
3. <span data-ttu-id="85c6e-114">После открытия приложения Store используйте панель поиска для поиска любой нужное приложение.</span><span class="sxs-lookup"><span data-stu-id="85c6e-114">Once the Store app opens, use the search bar to look for any desired application.</span></span>
4. <span data-ttu-id="85c6e-115">Выберите **получить** или **установить** на странице приложения (покупки может потребоваться).</span><span class="sxs-lookup"><span data-stu-id="85c6e-115">Select **Get** or **Install** on the application's page (a purchase may be required).</span></span>

### <a name="installing-an-application-package-with-the-device-portal"></a><span data-ttu-id="85c6e-116">Установка пакета приложения с помощью портала устройства</span><span class="sxs-lookup"><span data-stu-id="85c6e-116">Installing an application package with the Device Portal</span></span>
1. <span data-ttu-id="85c6e-117">Установление подключения от [портал устройств](using-the-windows-device-portal.md) к целевому объекту HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85c6e-117">Establish a connection from [Device Portal](using-the-windows-device-portal.md) to the target HoloLens.</span></span>
2. <span data-ttu-id="85c6e-118">Перейдите к **приложений** страницы в области навигации слева.</span><span class="sxs-lookup"><span data-stu-id="85c6e-118">Navigate to the **Apps** page in the left navigation.</span></span>
3. <span data-ttu-id="85c6e-119">В разделе **пакет приложения** перейдите к AppX-файл, связанный с приложением.</span><span class="sxs-lookup"><span data-stu-id="85c6e-119">Under **App Package** Browse to the .appx file associated with your application.</span></span>
  >[!IMPORTANT]
  ><span data-ttu-id="85c6e-120">Убедитесь в том, что ссылки на все связанные файлы зависимостей и сертификат.</span><span class="sxs-lookup"><span data-stu-id="85c6e-120">Make sure to reference any associated dependency and certificate files.</span></span>

4. <span data-ttu-id="85c6e-121">Нажмите кнопку **Go**.</span><span class="sxs-lookup"><span data-stu-id="85c6e-121">Click **Go**.</span></span>

<span data-ttu-id="85c6e-122">![Установка форма приложения в Windows Device Portal на Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span><span class="sxs-lookup"><span data-stu-id="85c6e-122">![Install app form in Windows Device Portal on Microsoft HoloLens](images/deviceportal-appmanager.jpg)</span></span><br>
<span data-ttu-id="85c6e-123">С помощью Windows Device Portal для установки приложения на HoloLens</span><span class="sxs-lookup"><span data-stu-id="85c6e-123">Using Windows Device Portal to install an app on HoloLens</span></span>

### <a name="deploying-from-microsoft-visual-studio-2015"></a><span data-ttu-id="85c6e-124">Развертывание из Microsoft Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="85c6e-124">Deploying from Microsoft Visual Studio 2015</span></span>
1. <span data-ttu-id="85c6e-125">Откройте решение приложения Visual Studio (SLN-файл).</span><span class="sxs-lookup"><span data-stu-id="85c6e-125">Open your app's Visual Studio solution (.sln file).</span></span>
2. <span data-ttu-id="85c6e-126">Откройте проект **свойства** .</span><span class="sxs-lookup"><span data-stu-id="85c6e-126">Open the project's **Properties** .</span></span>
3. <span data-ttu-id="85c6e-127">Выберите следующую конфигурацию сборки: Master/x86/удаленный компьютер.</span><span class="sxs-lookup"><span data-stu-id="85c6e-127">Select the following build configuration: Master/x86/Remote Machine.</span></span>
4. <span data-ttu-id="85c6e-128">При выборе удаленного компьютера:</span><span class="sxs-lookup"><span data-stu-id="85c6e-128">When you select Remote Machine:</span></span>
   * <span data-ttu-id="85c6e-129">Убедитесь, что адресные точки HoloLens Wi-Fi IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="85c6e-129">Make sure the address points to the HoloLens' WiFi IP address.</span></span>
   * <span data-ttu-id="85c6e-130">Настройка проверки подлинности для универсальный (незашифрованный протокол).</span><span class="sxs-lookup"><span data-stu-id="85c6e-130">Set authentication to Universal (Unencrypted Protocol).</span></span>
5. <span data-ttu-id="85c6e-131">Построение решения.</span><span class="sxs-lookup"><span data-stu-id="85c6e-131">Build your solution.</span></span>
6. <span data-ttu-id="85c6e-132">Нажмите кнопку **удаленный компьютер** кнопку, чтобы развернуть приложение из Компьютере разработки для вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85c6e-132">Click the **Remote Machine** button to deploy the app from your development PC to your HoloLens.</span></span> <span data-ttu-id="85c6e-133">Если уже существующую сборку на HoloLens, выберите "Да", чтобы повторно установить более новую версию.</span><span class="sxs-lookup"><span data-stu-id="85c6e-133">If you already have an existing build on the HoloLens, select yes to re-install this newer version.</span></span><br>
  <span data-ttu-id="85c6e-134">![Удаленное развертывание машины для приложений для Microsoft HoloLens в Visual Studio](images/vs2015-remotedeployment.jpg)</span><span class="sxs-lookup"><span data-stu-id="85c6e-134">![Remote Machine deployment for apps to Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)</span></span><br>
7. <span data-ttu-id="85c6e-135">Приложение установит и автоматического запуска на вашей HoloLens.</span><span class="sxs-lookup"><span data-stu-id="85c6e-135">The application will install and auto launch on your HoloLens.</span></span>
