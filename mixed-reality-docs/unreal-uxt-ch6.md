---
title: 6. Упаковка и развертывание на устройстве или в эмуляторе
description: Часть 6 руководства по созданию простого приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля средств разработки пользовательского интерфейса (UX) из набора средств для смешанной реальности
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, средства разработки пользовательского интерфейса, средства UX, документация
ms.openlocfilehash: 35b18e4bb289438f94433827846e94d1014385db
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840383"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="5c2c3-104">6. Упаковка и развертывание на устройстве или в эмуляторе</span><span class="sxs-lookup"><span data-stu-id="5c2c3-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="5c2c3-105">В этом разделе описан процесс, который подготовит приложение к запуску на устройстве или в эмуляторе HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="5c2c3-106">Если у вас есть устройство, вы можете передать потоком приложение с компьютера прямо на устройство либо упаковать приложение для запуска прямо на устройстве.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="5c2c3-107">Если у вас нет устройства, приложение необходимо упаковать для запуска в эмуляторе.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="5c2c3-108">Задачи</span><span class="sxs-lookup"><span data-stu-id="5c2c3-108">Objectives</span></span>

* <span data-ttu-id="5c2c3-109">[Только для устройства] Передача приложения в HoloLens 2 через голографическое удаленное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="5c2c3-110">Упаковка и развертывание приложения на устройстве или в эмуляторе HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="5c2c3-111">[Только для устройства] Потоковая передача</span><span class="sxs-lookup"><span data-stu-id="5c2c3-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="5c2c3-112">Установите **проигрыватель голографического удаленного взаимодействия** из Microsoft Store на устройстве HoloLens 2 и запустите его.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="5c2c3-113">Перейдите к разделу **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="5c2c3-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="5c2c3-114">В разделе "Голографическое удаленное взаимодействие" установите флажок, чтобы включить взаимодействие, и перезапустите редактор.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="5c2c3-115">Введите IP-адрес устройства и щелкните Connect (Подключить).</span><span class="sxs-lookup"><span data-stu-id="5c2c3-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="5c2c3-116">Завершив подключение, щелкните в редакторе UE4 стрелку раскрывающегося списка справа от кнопки Play (Играть) и выберите значение VR Preview (Просмотр виртуальной реальности).</span><span class="sxs-lookup"><span data-stu-id="5c2c3-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="5c2c3-117">Упаковка и развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="5c2c3-117">Package and deploy your app</span></span> 

1.  <span data-ttu-id="5c2c3-118">Перейдите к разделу **Edit > Project Settings** (Правка > Параметры проекта).</span><span class="sxs-lookup"><span data-stu-id="5c2c3-118">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="5c2c3-119">В разделе **Project > Description > About > Project Name** (Проект > Описание > Сведения > Имя проекта) присвойте проекту имя.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-119">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="5c2c3-120">В разделе **Project > Description > Publisher > Company Distinguished Name** (Проект > Описание > Издатель > Название организации) поместите значение "CN={INSERT COMPANY NAME}".</span><span class="sxs-lookup"><span data-stu-id="5c2c3-120">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="5c2c3-121">Если любое из этих полей останется пустым, процесс завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-121">Leaving either of these fields blank will result in an error.</span></span> 

![Параметры проекта — Описание](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="5c2c3-123">В разделе **Platforms > HoloLens** (Платформы > HoloLens) выберите эмуляцию и (или) устройство в зависимости от того, для какой среды вы готовите приложение.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-123">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="5c2c3-124">В разделе **Packaging** (Упаковка) рядом с полем **Signing Certificate** (Сертификат для подписи) щелкните **Generate new** (Создать новый), чтобы создать новый сертификат для подписи.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-124">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="5c2c3-125">Вернитесь в главное окно.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-125">Return to the Main window.</span></span>

![Параметры проекта — Платформы — HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="5c2c3-127">Откройте раздел **File > Package Project** (Файл > Упаковка проекта) и выберите **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-127">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="5c2c3-128">Создайте новую папку для сохранения пакета и щелкните **Select Folder** (Выбрать папку).</span><span class="sxs-lookup"><span data-stu-id="5c2c3-128">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="5c2c3-129">Когда завершится создание пакета приложения, откройте **Портал устройств Windows**, перейдите к разделу **Представления > Приложения** и найдите раздел **Развертывание приложений**.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-129">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="5c2c3-130">Щелкните**Обзор...** и найдите файл **ChessApp.appxbundle**.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-130">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="5c2c3-131">Нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-131">Click **Open**.</span></span> 

    * <span data-ttu-id="5c2c3-132">Если приложение впервые устанавливается на этом устройстве, установите флажок **Allow me to select framework packages** (Разрешить выбор пакетов платформы).</span><span class="sxs-lookup"><span data-stu-id="5c2c3-132">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="5c2c3-133">В следующем диалоговом окне включите соответствующий APPX-файл для VCLibs (arm64 для устройства или x64 для эмулятора).</span><span class="sxs-lookup"><span data-stu-id="5c2c3-133">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="5c2c3-134">Щелкните **Установить**.</span><span class="sxs-lookup"><span data-stu-id="5c2c3-134">Click **Install**</span></span>

<span data-ttu-id="5c2c3-135">Итак, вы завершили работу с этим руководством!</span><span class="sxs-lookup"><span data-stu-id="5c2c3-135">Congratulations on finishing this tutorial!</span></span>  