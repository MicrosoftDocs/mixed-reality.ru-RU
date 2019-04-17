---
title: Технический документ камеры глубина - ISSCC 2018 г.
description: Технический документ, посвященные камеры глубины для использования в проекте Kinect для Azure и следующей версии HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: событие, iscc, компьютерного зрения, исследований, kinect, hololens, глубина, списка иллюстраций
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601086"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="a02ed-104">Технический документ камеры глубина - ISSCC 2018 г.</span><span class="sxs-lookup"><span data-stu-id="a02ed-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="a02ed-105">**Заголовок:** Демодулированный BSI 65-нм 1Mpixel 320 МГц списка Иллюстраций изображение датчика с 3.5μm глобального затвора пикселей и аналогового группирования</span><span class="sxs-lookup"><span data-stu-id="a02ed-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="a02ed-106">**Соавторы:** Cyrus S Bamji, Swati Mehta, Барри Томпсон, Тамер Elkhatib, Стефан Wurster, Akkaya Онур, Эндрю Payne, Джон Godbaz, Майк Fenton, Rajasekaran Виджай, Ларри Prather, Nagaraja Сатья, Vishali Mogallapu, Dane снег, McCauley широкие возможности, Mukadam Mustansir, Iskender Agi Shaun McCarthy, Zhanping Xu, Перри Travis, Уильям Qian, Chan Vei Хан, Prabhu Adepu, Gazi али, Muneeb Ахмед, Aditya Mukherjee, Наяка Sheethal, Дейв Gampell, Acharya Сунил, Lou Kordus Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="a02ed-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="a02ed-107">**Представленные на ISSCC 2018 и публикуются в ISSCC градусов. Технический. Документы, февраля 2018 г.**</span><span class="sxs-lookup"><span data-stu-id="a02ed-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="a02ed-108">В.</span><span class="sxs-lookup"><span data-stu-id="a02ed-108">C.</span></span> <span data-ttu-id="a02ed-109">Bamji т. д., «Демодулированный BSI 65-нм 1Mpixel 320 МГц списка Иллюстраций изображение датчика с 3.5μm глобального затвора пикселей и аналогового группирования» ISSCC градусов.</span><span class="sxs-lookup"><span data-stu-id="a02ed-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="a02ed-110">Технический.</span><span class="sxs-lookup"><span data-stu-id="a02ed-110">Tech.</span></span> <span data-ttu-id="a02ed-111">Документы, стр. 94-95 февраля 2018 г.</span><span class="sxs-lookup"><span data-stu-id="a02ed-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="a02ed-112">IEEE изучите ссылку: https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="a02ed-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="a02ed-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="a02ed-113">© 2018 IEEE.</span></span> <span data-ttu-id="a02ed-114">Допускается личного использования этого материала.</span><span class="sxs-lookup"><span data-stu-id="a02ed-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="a02ed-115">Разрешение из стандарта IEEE, которые должны быть получены для всех других целей, в любой текущий или будущий мультимедиа, включая повторная печать/повторная публикация этого материала для рекламы или в рекламных целях, создание общий принцип работы оператора new, для перепродажи или повторное распространение к серверам или списки, или повторное использование компонента защищены авторским правом часть этой работы в другие работы.</span><span class="sxs-lookup"><span data-stu-id="a02ed-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="a02ed-116">**Технический документ.**</span><span class="sxs-lookup"><span data-stu-id="a02ed-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="a02ed-117">![Предварительная версия технического документа](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="a02ed-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="a02ed-118">Скачайте Технический документ с камеры глубины</span><span class="sxs-lookup"><span data-stu-id="a02ed-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
