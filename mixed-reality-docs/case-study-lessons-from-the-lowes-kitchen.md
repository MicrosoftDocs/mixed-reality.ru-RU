---
title: Пример использования - уроки из кухни Лоу
description: Команда HoloLens хочет поделиться некоторыми советы и рекомендации, которые были получены из проекта Лоу HoloLens.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, его Лоу, HoloLens, кухни, пример внедрения
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599846"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="b0e16-104">Пример использования - уроки из кухни Лоу</span><span class="sxs-lookup"><span data-stu-id="b0e16-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="b0e16-105">Команда HoloLens хочет поделиться некоторыми советы и рекомендации, которые были получены из проекта Лоу HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b0e16-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="b0e16-106">Ниже видеоролик HoloLens Лоу прогнозам демонстрируется в выступления Ignite 2016 Сатья.</span><span class="sxs-lookup"><span data-stu-id="b0e16-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="b0e16-107">В Лоу HoloLens рекомендации</span><span class="sxs-lookup"><span data-stu-id="b0e16-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="b0e16-108">Два видео рассматриваются рекомендации, которые были получены на основе HoloLens Лоу пилотный проект, который времен в хранилищах двух Лоу апреля 2016 г.</span><span class="sxs-lookup"><span data-stu-id="b0e16-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="b0e16-109">Ниже приведены ключевые темы.</span><span class="sxs-lookup"><span data-stu-id="b0e16-109">The key topics are:</span></span>
* <span data-ttu-id="b0e16-110">Добиться максимальной производительности для мобильного устройства</span><span class="sxs-lookup"><span data-stu-id="b0e16-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="b0e16-111">Создание методов UX с помощью полной holographic фрейма (2-й talk)</span><span class="sxs-lookup"><span data-stu-id="b0e16-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="b0e16-112">Precision выравнивание (2-й talk)</span><span class="sxs-lookup"><span data-stu-id="b0e16-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="b0e16-113">Общие возможности holographic (2-й talk)</span><span class="sxs-lookup"><span data-stu-id="b0e16-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="b0e16-114">Взаимодействие с клиентами (2-й talk)</span><span class="sxs-lookup"><span data-stu-id="b0e16-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="b0e16-115">Видео 1</span><span class="sxs-lookup"><span data-stu-id="b0e16-115">Video 1</span></span>

<span data-ttu-id="b0e16-116">**Добиться максимальной производительности для мобильного устройства** HoloLens работает под управлением неограниченными возможностями, которые при этом все обработка, которые предпринимаются в устройство.</span><span class="sxs-lookup"><span data-stu-id="b0e16-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="b0e16-117">Это требует мобильной платформе и чтобы образ мышления, аналогично созданию приложений для мобильных устройств.</span><span class="sxs-lookup"><span data-stu-id="b0e16-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="b0e16-118">Корпорация Майкрософт рекомендует, что приложение HoloLens Ведение 60 кадров/с для заманчивые работы для пользователей.</span><span class="sxs-lookup"><span data-stu-id="b0e16-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="b0e16-119">Наличие низкая кадров/с может привести к нестабильной работе голограммы.</span><span class="sxs-lookup"><span data-stu-id="b0e16-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="b0e16-120">Некоторые из самых важных факторов для просмотра при разработке для HoloLens оптимизации активов/decimation, с помощью пользовательскими шейдерами (бесплатно в [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="b0e16-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="b0e16-121">Другим важным аспектом является измеряет частоту кадров с самого начала проекта.</span><span class="sxs-lookup"><span data-stu-id="b0e16-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="b0e16-122">В зависимости от проекта порядок отображения ресурсов также может быть множество материалов</span><span class="sxs-lookup"><span data-stu-id="b0e16-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="b0e16-123">Видео 2</span><span class="sxs-lookup"><span data-stu-id="b0e16-123">Video 2</span></span>

<span data-ttu-id="b0e16-124">**Создание методов UX с помощью полной holographic кадр** важно понять размещение голограммы в физическом мире.</span><span class="sxs-lookup"><span data-stu-id="b0e16-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="b0e16-125">С его Лоу мы говорим о различных методов UX, которые помогают пользователям возможности голограммы вверх закрыть среду большего размера голограммы низкую.</span><span class="sxs-lookup"><span data-stu-id="b0e16-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="b0e16-126">**Выравнивание точности** сценарии для Лоу элемента было первостепенную важность для ее интерфейс в требуется точность выравнивание голограммы физических кухне.</span><span class="sxs-lookup"><span data-stu-id="b0e16-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="b0e16-127">Мы рассмотрим методы, которые гарантирует, что побуждает пользователей, которые их физической среды был изменен.</span><span class="sxs-lookup"><span data-stu-id="b0e16-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="b0e16-128">**Общие возможности holographic** связывает являются основным способом, что потрачено Лоу качества.</span><span class="sxs-lookup"><span data-stu-id="b0e16-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="b0e16-129">Один пользователь может изменить столешницы и другой пользователь будет видеть изменения.</span><span class="sxs-lookup"><span data-stu-id="b0e16-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="b0e16-130">Мы позвонили, это «общие возможности».</span><span class="sxs-lookup"><span data-stu-id="b0e16-130">We called this "shared experiences".</span></span>

<span data-ttu-id="b0e16-131">**Взаимодействие с клиентами** Лоу конструкторы не используете HoloLens, но их нужно см. в разделе клиентов, которые отображаются.</span><span class="sxs-lookup"><span data-stu-id="b0e16-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="b0e16-132">Мы покажем, как для записи, что видят клиенты в приложении универсальной платформы Windows.</span><span class="sxs-lookup"><span data-stu-id="b0e16-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
