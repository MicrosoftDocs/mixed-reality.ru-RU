---
title: Surfaces
description: Surfaces — это пример приложения с открытым исходным кодом от лабораторных занятий корпорации Майкрософт по проектированию смешанной реальности. Он изучает, как можно создать тактиле неожиданностью с визуальным, звуковым и полноценным отслеживанием вручную.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, мртк, проектирование, пример приложения, элементы управления
ms.openlocfilehash: fb6948ceda2a059323d23d72d6d3245a3a9896ee
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240465"
---
# <a name="surfaces"></a><span data-ttu-id="74e5a-105">Surfaces</span><span class="sxs-lookup"><span data-stu-id="74e5a-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="74e5a-106">В этой статье рассматривается исследовательская выборка, созданная в [лабораторных занятиях по смешанной реальности](https://github.com/Microsoft/MRDesignLabs_Unity), где мы предоставляем наши знания и предложения по разработке приложений для смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="74e5a-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="74e5a-107">Наши статьи и код, относящиеся к проектированию, будут развиваться по мере внесения новых обнаружений.</span><span class="sxs-lookup"><span data-stu-id="74e5a-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="74e5a-108">[Surfaces — это](https://github.com/microsoft/MRDL_Unity_Surfaces) пример приложения с открытым исходным кодом от лабораторных занятий корпорации Майкрософт по проектированию смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="74e5a-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="74e5a-109">Он изучает, как можно создать тактиле неожиданностью с визуальным, звуковым и полноценным отслеживанием вручную.</span><span class="sxs-lookup"><span data-stu-id="74e5a-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Surfaces](images/MRDL_Surfaces_1.jpg)

## <a name="about-the-app"></a><span data-ttu-id="74e5a-111">Сведения о приложении</span><span class="sxs-lookup"><span data-stu-id="74e5a-111">About the app</span></span>
<span data-ttu-id="74e5a-112">На поверхностях показано, как использовать систему ввода и стандартные блоки набора средств Mixed Reality Toolkit (МРТК) для создания приложений для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="74e5a-112">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="74e5a-113">В этом проекте можно найти примеры:</span><span class="sxs-lookup"><span data-stu-id="74e5a-113">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="74e5a-114">Используйте [входную систему](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)мртк, в частности отслеживание вручную или совместно.</span><span class="sxs-lookup"><span data-stu-id="74e5a-114">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="74e5a-115">Используйте [стандартный ШЕЙДЕР](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) мртк для работы с графикой.</span><span class="sxs-lookup"><span data-stu-id="74e5a-115">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="74e5a-116">Вы можете использовать компоненты этого проекта для создания собственных приложений смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="74e5a-116">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="74e5a-117">Дни разработки MR 2020 — сведения из приложения MR Surfaces</span><span class="sxs-lookup"><span data-stu-id="74e5a-117">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="74e5a-118">Сведения из приложения MR Surfaces</span><span class="sxs-lookup"><span data-stu-id="74e5a-118">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="74e5a-119">С Симкинс, старший дизайнер, лежащий в основе приложения МРДЛ Surfaces, рассказывает о статье о проектировании и технических возможностях приложения.</span><span class="sxs-lookup"><span data-stu-id="74e5a-119">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="74e5a-120">Репозиторий проекта в GitHub</span><span class="sxs-lookup"><span data-stu-id="74e5a-120">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="74e5a-121">Скачать приложение из Microsoft Store в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="74e5a-121">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="74e5a-122">(Приложение доступно только в HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="74e5a-122">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="74e5a-123">Об авторе</span><span class="sxs-lookup"><span data-stu-id="74e5a-123">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="74e5a-124"><b>Донг Йоон</b></span><span class="sxs-lookup"><span data-stu-id="74e5a-124"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="74e5a-125">Конструктор UX@Microsoft</span><span class="sxs-lookup"><span data-stu-id="74e5a-125">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="74e5a-126">См. также</span><span class="sxs-lookup"><span data-stu-id="74e5a-126">See also</span></span>

* [<span data-ttu-id="74e5a-127">Активный объект</span><span class="sxs-lookup"><span data-stu-id="74e5a-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="74e5a-128">Коллекция объектов</span><span class="sxs-lookup"><span data-stu-id="74e5a-128">Object collection</span></span>](object-collection.md)
