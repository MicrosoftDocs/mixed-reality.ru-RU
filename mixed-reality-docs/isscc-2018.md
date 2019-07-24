---
title: Технический документ о фотокамере — ИССКК 2018
description: Технический документ, в котором обсуждается камера с глубиной, которая будет использоваться в Project Kinect для Azure и следующей версии HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: Event, ИСКК, компьютерное зрение, исследование, Kinect, hololens, глубина, ТОФ
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516893"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="283ff-104">Технический документ о фотокамере — ИССКК 2018</span><span class="sxs-lookup"><span data-stu-id="283ff-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="283ff-105">**Титуль** 1Mpixel 65nm BSI 320MHz демодуляция с датчиком изображения ТОФ с 3,5 μм глобальные Пиксели затвора и аналоговый группирования</span><span class="sxs-lookup"><span data-stu-id="283ff-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="283ff-106">**Участники** Цирус S Бамжи, Свати Мехта, Барри Thompson, Тамер Елкхатиб, Стефан Вурстер, Онур Аккайа, Эндрю Пайне, Джон Годбаз, Mike Фентон, Виджай Ражасекаран, Ларри Прасер, Сатья Nagaraja, Vishali Mogallapu, область «данные снег, Rich McCauley, Mustansir Mukadam, ISKENDER AGI, (Shaun Мккарси, Занпинг КСУ, Travis Перри, Уильям Киан, Веи-, Прабху Адепу, Гази Ali, Муниб Ахмед, Адитя Мукхержи, Шисал Найак, Дейв Гампелл, Сунила Acharya, Lou Kordus, Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="283ff-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="283ff-107">**Представлено в ИССКК 2018 и Опубликовано в ИССКК град. Tech. Документация, Фев 2018.**</span><span class="sxs-lookup"><span data-stu-id="283ff-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="283ff-108">В.</span><span class="sxs-lookup"><span data-stu-id="283ff-108">C.</span></span> <span data-ttu-id="283ff-109">Бамжи et al., "1Mpixel 65nm BSI 320MHz демодуляциовый датчик изображения ТОФ с 3,5 μм глобальной затворной и аналоговый группирования," ИССКК град.</span><span class="sxs-lookup"><span data-stu-id="283ff-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="283ff-110">Tech.</span><span class="sxs-lookup"><span data-stu-id="283ff-110">Tech.</span></span> <span data-ttu-id="283ff-111">Документация, PP. 94-95, Фев 2018.</span><span class="sxs-lookup"><span data-stu-id="283ff-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="283ff-112">Ссылка для просмотра по стандарту IEEE: https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="283ff-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="283ff-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="283ff-113">© 2018 IEEE.</span></span> <span data-ttu-id="283ff-114">Личное использование этого материала разрешено.</span><span class="sxs-lookup"><span data-stu-id="283ff-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="283ff-115">Разрешение от IEEE должно быть получено для всех других целей, на всех текущих или будущих носителях, включая повторную печать или повторную публикацию этого материала для рекламы или рекламы, создания новых коллективных работ, для перепродажи или перераспределения на серверы или списки. повторное использование любых защищенных компонентов этой работы в других Works.</span><span class="sxs-lookup"><span data-stu-id="283ff-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="283ff-116">**Технический документ**</span><span class="sxs-lookup"><span data-stu-id="283ff-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="283ff-117">![Предварительный просмотр технического документа](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="283ff-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="283ff-118">Технический документ о камере с глубиной загрузки</span><span class="sxs-lookup"><span data-stu-id="283ff-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
