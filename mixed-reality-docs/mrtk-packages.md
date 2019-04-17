---
title: Пакеты MRTK
description: В этой статье описываются пакеты, которые составляют Toollkit Microsoft смешанной реальности.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality, MRTK, компонент, пакет
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604643"
---
# <a name="mrtk-packages"></a><span data-ttu-id="de8d5-104">Пакеты MRTK</span><span class="sxs-lookup"><span data-stu-id="de8d5-104">MRTK packages</span></span>

<span data-ttu-id="de8d5-105">Набор средств смешанной реальности (MRTK) является коллекцией из пакетов, обеспечивающих разработку приложений межплатформенные смешанной реальности, предоставляя поддержку для смешанной реальности оборудования и платформ компонентной образом.</span><span class="sxs-lookup"><span data-stu-id="de8d5-105">The Mixed Reality Toolkit (MRTK) is a collection of packages that enable cross platform Mixed Reality application development by providing support for Mixed Reality hardware and platforms in a componentized manner.</span></span>

<span data-ttu-id="de8d5-106">Существует три категории пакетов MRTK:</span><span class="sxs-lookup"><span data-stu-id="de8d5-106">There are three categories of MRTK packages:</span></span> 

* [<span data-ttu-id="de8d5-107">Foundation</span><span class="sxs-lookup"><span data-stu-id="de8d5-107">Foundation</span></span>](#foundation-packages)
* [<span data-ttu-id="de8d5-108">Расширение</span><span class="sxs-lookup"><span data-stu-id="de8d5-108">Extension</span></span>](#extension-packages)
* [<span data-ttu-id="de8d5-109">Экспериментальные</span><span class="sxs-lookup"><span data-stu-id="de8d5-109">Experimental</span></span>](#experimental-packages)

## <a name="foundation-packages"></a><span data-ttu-id="de8d5-110">Базовые пакеты</span><span class="sxs-lookup"><span data-stu-id="de8d5-110">Foundation Packages</span></span>

<span data-ttu-id="de8d5-111">В смешанной реальности Toolkit лежит набор пакетов, которые позволяют приложению использовать функциональные возможности на платформах смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="de8d5-111">The Mixed Reality Toolkit Foundation is the set of packages that enable your application to leverage common functionality across Mixed Reality Platforms.</span></span> <span data-ttu-id="de8d5-112">Эти пакеты будут выпущены и поддерживается корпорацией Майкрософт, из исходного кода в [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) ветви на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="de8d5-112">These packages are released and supported by Microsoft from source code in the [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) branch on GitHub.</span></span>

![MRTK базовые пакеты](images/mrtk-foundation.jpg)

<span data-ttu-id="de8d5-114">*Смешанной реальности Toolkit базовые пакеты*</span><span class="sxs-lookup"><span data-stu-id="de8d5-114">*Mixed Reality Toolkit Foundation packages*</span></span>

<span data-ttu-id="de8d5-115">MRTK Foundation состоит из:</span><span class="sxs-lookup"><span data-stu-id="de8d5-115">The MRTK Foundation is comprised of:</span></span>

* [<span data-ttu-id="de8d5-116">Основной пакет</span><span class="sxs-lookup"><span data-stu-id="de8d5-116">Core Package</span></span>](#core-package)
* [<span data-ttu-id="de8d5-117">Поставщики платформы</span><span class="sxs-lookup"><span data-stu-id="de8d5-117">Platform Providers</span></span>](#platform-providers)
* [<span data-ttu-id="de8d5-118">Системные службы</span><span class="sxs-lookup"><span data-stu-id="de8d5-118">System Services</span></span>](#system-services)
* [<span data-ttu-id="de8d5-119">Функция активы</span><span class="sxs-lookup"><span data-stu-id="de8d5-119">Feature Assets</span></span>](#feature-assets)

<span data-ttu-id="de8d5-120">В следующих разделах описаны типы пакетов в каждой категории.</span><span class="sxs-lookup"><span data-stu-id="de8d5-120">The following sections describe the types of packages in each category.</span></span>

### <a name="core-package"></a><span data-ttu-id="de8d5-121">Основной пакет</span><span class="sxs-lookup"><span data-stu-id="de8d5-121">Core Package</span></span>

<span data-ttu-id="de8d5-122">Основной пакет является _требуется_ компонента и выполняется как зависимость использоваться всеми пакетами MRTK foundation.</span><span class="sxs-lookup"><span data-stu-id="de8d5-122">The core package is a _required_ component and is taken as a dependency by all MRTK foundation packages.</span></span>

<span data-ttu-id="de8d5-123">MRTK основной пакет включает в себя:</span><span class="sxs-lookup"><span data-stu-id="de8d5-123">The MRTK Core package includes:</span></span>

* [<span data-ttu-id="de8d5-124">Общие интерфейсы, классы и типы данных</span><span class="sxs-lookup"><span data-stu-id="de8d5-124">Common interfaces, classes and data types</span></span>](#common-interfaces-clases-and-data-types)
* [<span data-ttu-id="de8d5-125">Компонент MixedRealityToolkit сцены</span><span class="sxs-lookup"><span data-stu-id="de8d5-125">MixedRealityToolkit scene component</span></span>](#mixedrealitytoolkit-scene-component)
* [<span data-ttu-id="de8d5-126">Стандартный шейдера MRTK</span><span class="sxs-lookup"><span data-stu-id="de8d5-126">MRTK Standard Shader</span></span>](#mrtk-standard-shader)
* [<span data-ttu-id="de8d5-127">Поставщик ввода с Unity</span><span class="sxs-lookup"><span data-stu-id="de8d5-127">Unity Input Provider</span></span>](#unity-input-provider)
* [<span data-ttu-id="de8d5-128">Управление пакетами</span><span class="sxs-lookup"><span data-stu-id="de8d5-128">Package Management</span></span>](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a><span data-ttu-id="de8d5-129">Общие интерфейсы, классы и типы данных</span><span class="sxs-lookup"><span data-stu-id="de8d5-129">Common interfaces, classes and data types</span></span>

<span data-ttu-id="de8d5-130">Основной набор средств смешанной реальности пакет содержит определения для всех общих интерфейсов, классов и типов данных, которые используются другими компонентами.</span><span class="sxs-lookup"><span data-stu-id="de8d5-130">The Mixed Reality Toolkit Core package contains the definitions for all of the common interfaces, classes and data types that are used by all other components.</span></span> <span data-ttu-id="de8d5-131">Настоятельно рекомендуется что приложений доступа к компонентам MRTK исключительно через определенные интерфейсы, позволяющие самый высокий уровень совместимости между платформами.</span><span class="sxs-lookup"><span data-stu-id="de8d5-131">It is highly recommended that applications access MRTK components exclusively through the defined interfaces to enable the highest level of compatibility across platforms.</span></span>

#### <a name="mixedrealitytoolkit-scene-component"></a><span data-ttu-id="de8d5-132">Компонент MixedRealityToolkit сцены</span><span class="sxs-lookup"><span data-stu-id="de8d5-132">MixedRealityToolkit scene component</span></span>

<span data-ttu-id="de8d5-133">Компонент сцены MixedRealityToolkit — диспетчер централизованного отдельный ресурс для смешанной реальности Toolkit.</span><span class="sxs-lookup"><span data-stu-id="de8d5-133">The MixedRealityToolkit scene component is the single, centralized resource manager for the Mixed Reality Toolkit.</span></span> <span data-ttu-id="de8d5-134">Этот компонент загружает и управляет существования модулей платформ и служб и предоставляет ресурсы для систем, для доступа к их параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="de8d5-134">This component loads and manages the lifespan of the platform and service modules and provides resources for the systems to access their configuration settings.</span></span> 

#### <a name="mrtk-standard-shader"></a><span data-ttu-id="de8d5-135">Стандартный шейдера MRTK</span><span class="sxs-lookup"><span data-stu-id="de8d5-135">MRTK Standard Shader</span></span>

<span data-ttu-id="de8d5-136">Стандартный шейдера MRTK обеспечивает основу для практически всех материалов, предоставленных MRTK.</span><span class="sxs-lookup"><span data-stu-id="de8d5-136">The MRTK Standard Shader provides the basis for virtually all of the materials provided by the MRTK.</span></span> <span data-ttu-id="de8d5-137">Этот шейдер чрезвычайно гибкого и оптимизированного для различных платформ, в которых поддерживается MRTK.</span><span class="sxs-lookup"><span data-stu-id="de8d5-137">This shader is extremely flexible and optimized for the variety of platforms on which MRTK is supported.</span></span> <span data-ttu-id="de8d5-138">Это _высокой_ рекомендуется использовать стандартный шейдера MRTK материалы приложения для обеспечения оптимальной производительности.</span><span class="sxs-lookup"><span data-stu-id="de8d5-138">It is _highly_ recommended that your application's materials use the MRTK standard shader for optimal performance.</span></span>

#### <a name="unity-input-provider"></a><span data-ttu-id="de8d5-139">Поставщик ввода с Unity</span><span class="sxs-lookup"><span data-stu-id="de8d5-139">Unity Input Provider</span></span>

<span data-ttu-id="de8d5-140">Поставщик ввода Unity предоставляет доступ к common устройства ввода, например игровых устройств управления, сенсорных экранов и 3D пространственных мыши.</span><span class="sxs-lookup"><span data-stu-id="de8d5-140">The Unity Input Provider provides access to common input devices such as game controllers, touch screens and a 3D spatial mouse.</span></span>

#### <a name="package-management"></a><span data-ttu-id="de8d5-141">Управление пакетами</span><span class="sxs-lookup"><span data-stu-id="de8d5-141">Package Management</span></span>

<span data-ttu-id="de8d5-142">_Скоро_</span><span class="sxs-lookup"><span data-stu-id="de8d5-142">_Coming soon_</span></span>

<span data-ttu-id="de8d5-143">Основной набор средств смешанной реальности пакет предоставляет поддержку обнаружения и управления необязательно foundation, расширение и экспериментальные пакеты MRTK.</span><span class="sxs-lookup"><span data-stu-id="de8d5-143">The Mixed Reality Toolkit Core package provides support for discovering and managing the optional foundation, extension and experimental MRTK packages.</span></span>

### <a name="platform-providers"></a><span data-ttu-id="de8d5-144">Поставщики платформы</span><span class="sxs-lookup"><span data-stu-id="de8d5-144">Platform Providers</span></span>

<span data-ttu-id="de8d5-145">Пакеты MRTK поставщика платформы являются компонентами, позволяющих смешанной реальности Toolkit к целевому объекту смешанной реальности оборудования и функциональных возможностей платформы.</span><span class="sxs-lookup"><span data-stu-id="de8d5-145">The MRTK Platform Provider packages are the components that enable the Mixed Reality Toolkit to target Mixed Reality hardware and platform functionality.</span></span>

<span data-ttu-id="de8d5-146">Поддерживаются следующие платформы:</span><span class="sxs-lookup"><span data-stu-id="de8d5-146">Supported platforms include:</span></span>

* [<span data-ttu-id="de8d5-147">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="de8d5-147">Windows Mixed Reality</span></span>](#windows-mixed-reality)
* [<span data-ttu-id="de8d5-148">OpenVR</span><span class="sxs-lookup"><span data-stu-id="de8d5-148">OpenVR</span></span>](#openvr)
* [<span data-ttu-id="de8d5-149">Голосовые Windows</span><span class="sxs-lookup"><span data-stu-id="de8d5-149">Windows Voice</span></span>](#windows-voice)

#### <a name="windows-mixed-reality"></a><span data-ttu-id="de8d5-150">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="de8d5-150">Windows Mixed Reality</span></span>

<span data-ttu-id="de8d5-151">Пакет Windows Mixed Reality обеспечивает поддержку для устройств Microsoft HoloLens и Иммерсивных Windows смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="de8d5-151">The Windows Mixed Reality package provides support for Microsoft HoloLens and Windows Mixed Reality Immersive devices.</span></span> <span data-ttu-id="de8d5-152">Пакет содержит полной поддержки платформы, включая:</span><span class="sxs-lookup"><span data-stu-id="de8d5-152">The package contains full platform support, including:</span></span>

* <span data-ttu-id="de8d5-153">Нацеливание взглядом</span><span class="sxs-lookup"><span data-stu-id="de8d5-153">Gaze targeting</span></span>
* <span data-ttu-id="de8d5-154">Жесты</span><span class="sxs-lookup"><span data-stu-id="de8d5-154">Gestures</span></span>
* <span data-ttu-id="de8d5-155">Контроллеры Windows смешанной реальности движения</span><span class="sxs-lookup"><span data-stu-id="de8d5-155">Windows Mixed Reality Motion controllers</span></span>
* <span data-ttu-id="de8d5-156">Пространственное сопоставление</span><span class="sxs-lookup"><span data-stu-id="de8d5-156">Spatial Mapping</span></span>

#### <a name="openvr"></a><span data-ttu-id="de8d5-157">OpenVR</span><span class="sxs-lookup"><span data-stu-id="de8d5-157">OpenVR</span></span>

<span data-ttu-id="de8d5-158">Пакет OpenVR обеспечивает поддержку оборудования и платформы для устройств с помощью платформы OpenVR.</span><span class="sxs-lookup"><span data-stu-id="de8d5-158">The OpenVR package provides hardware and platform support for devices using the OpenVR platform.</span></span>

#### <a name="windows-voice"></a><span data-ttu-id="de8d5-159">Голосовые Windows</span><span class="sxs-lookup"><span data-stu-id="de8d5-159">Windows Voice</span></span>

<span data-ttu-id="de8d5-160">Пакет Windows голосовой обеспечивает поддержку функций распознавания ключевое слово, на устройствах Microsoft Windows 10.</span><span class="sxs-lookup"><span data-stu-id="de8d5-160">The Windows Voice package provides support for keyword recognition and dictation functionality on Microsoft Windows 10 devices.</span></span>

### <a name="system-services"></a><span data-ttu-id="de8d5-161">Системные службы</span><span class="sxs-lookup"><span data-stu-id="de8d5-161">System Services</span></span>

<span data-ttu-id="de8d5-162">Базовые службы платформы, указанные в пакеты службы системы.</span><span class="sxs-lookup"><span data-stu-id="de8d5-162">Core platform services are provided in system service packages.</span></span> <span data-ttu-id="de8d5-163">Эти пакеты содержат системные службы интерфейсы, определенные в реализации по умолчанию смешанной реальности Toolkit [core](#core-package) пакета.</span><span class="sxs-lookup"><span data-stu-id="de8d5-163">These packages contain the Mixed Reality Toolkit's default implementations of the system service interfaces, defined in the [core](#core-package) package.</span></span>

<span data-ttu-id="de8d5-164">MRTK foundation включает в себя следующие системные службы:</span><span class="sxs-lookup"><span data-stu-id="de8d5-164">The MRTK foundation includes the following system services:</span></span>

* [<span data-ttu-id="de8d5-165">Границы системы</span><span class="sxs-lookup"><span data-stu-id="de8d5-165">Boundary System</span></span>](#boundary-system)
* [<span data-ttu-id="de8d5-166">Система диагностики</span><span class="sxs-lookup"><span data-stu-id="de8d5-166">Diagnostic System</span></span>](#diagnostic-system)
* [<span data-ttu-id="de8d5-167">Система ввода</span><span class="sxs-lookup"><span data-stu-id="de8d5-167">Input System</span></span>](#input-system)
* [<span data-ttu-id="de8d5-168">Поддержка пространственных системы</span><span class="sxs-lookup"><span data-stu-id="de8d5-168">Spatial Awareness System</span></span>](#spatial-awareness-system)
* [<span data-ttu-id="de8d5-169">Teleport системы</span><span class="sxs-lookup"><span data-stu-id="de8d5-169">Teleport System</span></span>](#teleport-system)

#### <a name="boundary-system"></a><span data-ttu-id="de8d5-170">Границы системы</span><span class="sxs-lookup"><span data-stu-id="de8d5-170">Boundary System</span></span>

<span data-ttu-id="de8d5-171">Система границ MRTK предоставляет данные о в виртуальный реальности playspace.</span><span class="sxs-lookup"><span data-stu-id="de8d5-171">The MRTK Boundary System provides data about the to virtual reality playspace.</span></span> <span data-ttu-id="de8d5-172">В системах, для которых пользователь настроил границу система может предоставлять плоскость floor, прямоугольная playspace, отслеживаемой области и многое другое.</span><span class="sxs-lookup"><span data-stu-id="de8d5-172">On systems for which the user has configured the boundary, the system can provide a floor plane, rectangular playspace, tracked area, and more.</span></span>

#### <a name="diagnostic-system"></a><span data-ttu-id="de8d5-173">Система диагностики</span><span class="sxs-lookup"><span data-stu-id="de8d5-173">Diagnostic System</span></span>

<span data-ttu-id="de8d5-174">Система диагностики MRTK предоставляет данные производительности в реальном времени в работу приложения.</span><span class="sxs-lookup"><span data-stu-id="de8d5-174">The MRTK Diagnostic System provides real-time performance data within your application experience.</span></span> <span data-ttu-id="de8d5-175">В краткая будет иметь возможность просматривать частоту кадров, загруженности процессора и других ключевых метрик производительности, использования приложения.</span><span class="sxs-lookup"><span data-stu-id="de8d5-175">At a glace, you will be able to view frame rate, processor time and other key performance metrics as you use your application.</span></span>

#### <a name="input-system"></a><span data-ttu-id="de8d5-176">Система ввода</span><span class="sxs-lookup"><span data-stu-id="de8d5-176">Input System</span></span>

<span data-ttu-id="de8d5-177">MRTK систем ввода позволяет приложениям получать доступ к входные данные в виде кроссплатформенный, определение действия пользователя и назначение эти действия наиболее подходящий кнопок и осей на целевых контроллеров.</span><span class="sxs-lookup"><span data-stu-id="de8d5-177">The MRTK Input Systems enables applications to access input in a cross platform manner by specifying user actions and assigning those actions to the most appropriate buttons and axes on target controllers.</span></span>

#### <a name="spatial-awareness-system"></a><span data-ttu-id="de8d5-178">Поддержка пространственных системы</span><span class="sxs-lookup"><span data-stu-id="de8d5-178">Spatial Awareness System</span></span>

<span data-ttu-id="de8d5-179">Пространственные системы Awareness MRTK обеспечивает доступ к реальной среды данных из устройств, таких как Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="de8d5-179">The MRTK Spatial Awareness System enables access to real-world environmental data from devices such as the Microsoft HoloLens.</span></span>

#### <a name="teleport-system"></a><span data-ttu-id="de8d5-180">Teleport системы</span><span class="sxs-lookup"><span data-stu-id="de8d5-180">Teleport System</span></span>

<span data-ttu-id="de8d5-181">Система Teleport MRTK поддерживает locomotion виртуальной реальности.</span><span class="sxs-lookup"><span data-stu-id="de8d5-181">The MRTK Teleport System provides virtual reality locomotion support.</span></span>

### <a name="feature-assets"></a><span data-ttu-id="de8d5-182">Функция активы</span><span class="sxs-lookup"><span data-stu-id="de8d5-182">Feature Assets</span></span>

<span data-ttu-id="de8d5-183">Функция ресурсы представляют собой коллекции связанных функций, предоставляемая как Unity средств и сценариев.</span><span class="sxs-lookup"><span data-stu-id="de8d5-183">Feature Assets are collections of related functionality delivered as Unity assets and scripts.</span></span> <span data-ttu-id="de8d5-184">Ниже перечислены некоторые из этих функций.</span><span class="sxs-lookup"><span data-stu-id="de8d5-184">Some of these features include:</span></span>

* <span data-ttu-id="de8d5-185">Элементы управления пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="de8d5-185">User Interface Controls</span></span>
* <span data-ttu-id="de8d5-186">Стандартных активов</span><span class="sxs-lookup"><span data-stu-id="de8d5-186">Standard Assets</span></span>
* <span data-ttu-id="de8d5-187">more</span><span class="sxs-lookup"><span data-stu-id="de8d5-187">more</span></span>

## <a name="extension-packages"></a><span data-ttu-id="de8d5-188">Пакеты расширений</span><span class="sxs-lookup"><span data-stu-id="de8d5-188">Extension Packages</span></span>

<span data-ttu-id="de8d5-189">Пакеты расширений MRTK представляют собой коллекцию пакеты, написанные корпорацией Майкрософт и сообщества, которые расширяют и улучшают функции набора средств смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="de8d5-189">MRTK Extension packages are a collection of packages written by Microsoft and the Community that extend and enhance the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="de8d5-190">Авторы расширение будет состояние все необходимые зависимости, пометить пакет как совместимая с набором средств смешанной реальности и предоставляют лицензирования и поддерживают инструкции.</span><span class="sxs-lookup"><span data-stu-id="de8d5-190">Extension authors will state any required dependencies, mark the package as compatible with the Mixed Reality Toolkit and provide licensing and support statements.</span></span>

<span data-ttu-id="de8d5-191">Пакеты расширений может предоставлять новые функции и поддержку новых платформ.</span><span class="sxs-lookup"><span data-stu-id="de8d5-191">Extension packages may provide new features and new platform support.</span></span> <span data-ttu-id="de8d5-192">Со временем расширения могут с помощь и утверждения авторов, быть перенесены в Foundation MRTK, после чего они будут выпущены и поддерживается корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="de8d5-192">Over time, extensions may, with the assistance and approval of the authors, be migrated into the MRTK Foundation at which time they will be released and supported by Microsoft.</span></span>

![Пакет расширения MRTK](images/mrtk-extensions.jpg)

<span data-ttu-id="de8d5-194">*Смешанной реальности набор средств расширения пакетов*</span><span class="sxs-lookup"><span data-stu-id="de8d5-194">*Mixed Reality Toolkit Extension packages*</span></span>

## <a name="experimental-packages"></a><span data-ttu-id="de8d5-195">Экспериментальные пакеты</span><span class="sxs-lookup"><span data-stu-id="de8d5-195">Experimental Packages</span></span>

<span data-ttu-id="de8d5-196">Экспериментальные пакеты предоставляют возможность рейсов прототипа функции, предварительные выпуски и интересные новые идеи.</span><span class="sxs-lookup"><span data-stu-id="de8d5-196">Experimental packages provide the ability to flight prototype features, pre-releases and exciting new ideas.</span></span> <span data-ttu-id="de8d5-197">Цель наиболее экспериментальные пакеты — попробовать что-то новое или датчика заинтересованности клиентов.</span><span class="sxs-lookup"><span data-stu-id="de8d5-197">The goal of most experimental packages is to try something new and to gauge customer interest.</span></span> <span data-ttu-id="de8d5-198">Многие, хотя и не все экспериментальные пакеты будут повторно выпущено как расширения по завершении создания прототипов и тестирования.</span><span class="sxs-lookup"><span data-stu-id="de8d5-198">Many, though not all, experimental packages will be re-released as extensions once the prototyping and testing phase completes.</span></span>

![Экспериментальные пакеты MRTK](images/mrtk-experimental.jpg)

<span data-ttu-id="de8d5-200">*Смешанной реальности Toolkit экспериментальные пакеты*</span><span class="sxs-lookup"><span data-stu-id="de8d5-200">*Mixed Reality Toolkit Experimental packages*</span></span>

## <a name="conclusion"></a><span data-ttu-id="de8d5-201">Заключение</span><span class="sxs-lookup"><span data-stu-id="de8d5-201">Conclusion</span></span>

<span data-ttu-id="de8d5-202">Пакеты смешанной реальности Toolkit и система управления пакетами предназначены для включения простой и четкий способ аддитивно создания функции в своем опыте работы, не требуя ненужные компоненты для включения в проект.</span><span class="sxs-lookup"><span data-stu-id="de8d5-202">The Mixed Reality Toolkit packages and package management system are designed to enable a clean and simple method for you to additively build features into your experiences without requiring unnecessary components to be included into the project.</span></span>

<span data-ttu-id="de8d5-203">Со временем добавляются поддержка управления пакетами и улучшены в наборе средств смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="de8d5-203">Over time, package management support will be added and enhanced within the Mixed Reality Toolkit.</span></span> <span data-ttu-id="de8d5-204">Если вы хотите оставить отзыв или хотите стать участником, посетите [проекта смешанной реальности Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="de8d5-204">If you have feedback or wish to get involved, please visit the [Mixed Reality Toolkit project](https://github.com/Microsoft/MixedRealityToolkit-Unity) on GitHub.</span></span> 

## <a name="see-also"></a><span data-ttu-id="de8d5-205">См. также</span><span class="sxs-lookup"><span data-stu-id="de8d5-205">See also</span></span>

* [<span data-ttu-id="de8d5-206">MixedRealityToolkit-Unity (GitHub)</span><span class="sxs-lookup"><span data-stu-id="de8d5-206">MixedRealityToolkit-Unity (GitHub)</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

