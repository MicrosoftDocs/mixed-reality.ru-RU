---
title: 6. Упаковка и развертывание на устройстве или в эмуляторе
description: Часть 6 руководства по созданию простого приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля средств разработки пользовательского интерфейса (UX) из набора средств для смешанной реальности
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, средства разработки пользовательского интерфейса, средства UX, документация
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519974"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="36e92-104">6. Упаковка и развертывание на устройстве или в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="36e92-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="36e92-105">В этом разделе описан процесс, который подготовит приложение к запуску на устройстве или в эмуляторе HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="36e92-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="36e92-106">Если у вас есть устройство, вы можете передать потоком приложение с компьютера прямо на устройство либо упаковать приложение для запуска прямо на устройстве.</span><span class="sxs-lookup"><span data-stu-id="36e92-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="36e92-107">Если у вас нет устройства, приложение необходимо упаковать для запуска в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="36e92-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="36e92-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="36e92-108">Objectives</span></span>

* <span data-ttu-id="36e92-109">[Только для устройства] Передача приложения в HoloLens 2 через голографическое удаленное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="36e92-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="36e92-110">Упаковка и развертывание приложения на устройстве или в эмуляторе HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="36e92-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="36e92-111">[Только для устройства] Потоковая передача</span><span class="sxs-lookup"><span data-stu-id="36e92-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="36e92-112">Установите **проигрыватель голографического удаленного взаимодействия** из Microsoft Store на устройстве HoloLens 2 и запустите его.</span><span class="sxs-lookup"><span data-stu-id="36e92-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="36e92-113">Перейдите к разделу **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="36e92-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="36e92-114">В разделе "Голографическое удаленное взаимодействие" установите флажок, чтобы включить взаимодействие, и перезапустите редактор.</span><span class="sxs-lookup"><span data-stu-id="36e92-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="36e92-115">Введите IP-адрес устройства и щелкните Connect (Подключить).</span><span class="sxs-lookup"><span data-stu-id="36e92-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="36e92-116">Завершив подключение, щелкните в редакторе UE4 стрелку раскрывающегося списка справа от кнопки Play (Играть) и выберите значение VR Preview (Просмотр виртуальной реальности).</span><span class="sxs-lookup"><span data-stu-id="36e92-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="36e92-117">Упаковка и развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="36e92-117">Package and deploy your app</span></span> 

>[!NOTE]
><span data-ttu-id="36e92-118">Если вы впервые упаковываете приложение Unreal для HoloLens, потребуется скачать вспомогательные файлы из Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="36e92-118">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> <span data-ttu-id="36e92-119">Для этого перейдите на вкладку **Library** (Библиотека) в Epic Games Launcher.</span><span class="sxs-lookup"><span data-stu-id="36e92-119">To do so, go to the **Library** tab in the Epic Games Launcher.</span></span> <span data-ttu-id="36e92-120">Щелкните стрелку раскрывающегося списка рядом с полем **Launch** (Запуск) и выберите элемент **Options** (Параметры).</span><span class="sxs-lookup"><span data-stu-id="36e92-120">Select the dropdown arrow next to **Launch** and select **Options**.</span></span> <span data-ttu-id="36e92-121">В разделе **Target Platforms** (Целевые платформы) выберите элемент **HoloLens 2** и щелкните команду **Apply** (Применить).</span><span class="sxs-lookup"><span data-stu-id="36e92-121">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="36e92-122">![Вкладка Project Settings (Параметры проекта), раздел Description (Описание)](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="36e92-122">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="36e92-123">Перейдите к разделу **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="36e92-123">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="36e92-124">В разделе **Project > Description > About > Project Name** (Проект > Описание > Сведения > Имя проекта) присвойте проекту имя.</span><span class="sxs-lookup"><span data-stu-id="36e92-124">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="36e92-125">В разделе **Project > Description > Publisher > Company Distinguished Name** (Проект > Описание > Издатель > Название организации) поместите значение "CN={INSERT COMPANY NAME}".</span><span class="sxs-lookup"><span data-stu-id="36e92-125">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="36e92-126">Если любое из этих полей останется пустым, процесс завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="36e92-126">Leaving either of these fields blank will result in an error.</span></span> 

![Параметры проекта — Описание](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="36e92-128">В разделе **Platforms > HoloLens** (Платформы > HoloLens) выберите эмуляцию и (или) устройство в зависимости от того, для какой среды вы готовите приложение.</span><span class="sxs-lookup"><span data-stu-id="36e92-128">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="36e92-129">В разделе **Packaging** (Упаковка) рядом с полем **Signing Certificate** (Сертификат для подписи) щелкните **Generate new** (Создать новый), чтобы создать новый сертификат для подписи.</span><span class="sxs-lookup"><span data-stu-id="36e92-129">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="36e92-130">Вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="36e92-130">Return to the Main window.</span></span>

![Параметры проекта — Платформы — HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="36e92-132">Откройте раздел **File > Package Project** (Файл > Упаковка проекта) и выберите **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="36e92-132">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="36e92-133">Создайте новую папку для сохранения пакета и щелкните **Select Folder** (Выбрать папку).</span><span class="sxs-lookup"><span data-stu-id="36e92-133">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="36e92-134">Когда завершится создание пакета приложения, откройте **Портал устройств Windows**, перейдите к разделу **Представления > Приложения** и найдите раздел **Развертывание приложений**.</span><span class="sxs-lookup"><span data-stu-id="36e92-134">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="36e92-135">Щелкните**Обзор...** и найдите файл **ChessApp.appxbundle**.</span><span class="sxs-lookup"><span data-stu-id="36e92-135">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="36e92-136">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="36e92-136">Click **Open**.</span></span> 

    * <span data-ttu-id="36e92-137">Если приложение впервые устанавливается на этом устройстве, установите флажок **Allow me to select framework packages** (Разрешить выбор пакетов платформы).</span><span class="sxs-lookup"><span data-stu-id="36e92-137">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="36e92-138">В следующем диалоговом окне включите соответствующий APPX-файл для VCLibs (arm64 для устройства или x64 для эмулятора).</span><span class="sxs-lookup"><span data-stu-id="36e92-138">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="36e92-139">Щелкните **Установить**.</span><span class="sxs-lookup"><span data-stu-id="36e92-139">Click **Install**</span></span>

<span data-ttu-id="36e92-140">Итак, вы завершили работу с этим руководством!</span><span class="sxs-lookup"><span data-stu-id="36e92-140">Congratulations on finishing this tutorial!</span></span>  