---
title: Развлечения на основе расположения с использованием Windows Mixed Reality
description: Получить доступ к базовым объектам holographic в Unity.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: Смешанная реальность, VR, лбе, расположение
ms.openlocfilehash: e23d17ff2b07c636c98a9f19a5dd20f4dc558bf7
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2019
ms.locfileid: "69983402"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a><span data-ttu-id="2a28f-104">Развлечения на основе расположения с использованием Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="2a28f-104">Location Based Entertainment with Windows Mixed Reality</span></span>

<span data-ttu-id="2a28f-105">В последние несколько лет мы выделили невероятный объем роста и инноваций в категории "развлечения на основе местоположения".</span><span class="sxs-lookup"><span data-stu-id="2a28f-105">In the last couple of years, we have witnessed an incredible amount of growth and innovation in the Location Based Entertainment category.</span></span> <span data-ttu-id="2a28f-106">Традиционные места проведения, такие как theme парки и сеатрес, начали предлагать впечатляющие, многопользовательские возможности в качестве бесплатных решений для существующих установок.</span><span class="sxs-lookup"><span data-stu-id="2a28f-106">Traditional venues like theme parks and theatres have started offering immersive, multi-player experiences as complimentary experiences to existing rides and installations.</span></span> <span data-ttu-id="2a28f-107">Новые операторы и места проведения используют уникальные возможности работы с несколькими игроками по привлекательной цене на языке.</span><span class="sxs-lookup"><span data-stu-id="2a28f-107">New operators and venues are bringing unique multi-sensorial, multi-player experiences at an attractive price to the masses.</span></span> <span data-ttu-id="2a28f-108">Все эти возможности помещаются на конверте для того, что возможно в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2a28f-108">All of these experiences are pushing the envelope for what’s possible with mixed reality.</span></span>

<span data-ttu-id="2a28f-109">Этот документ представляет собой руководство по началу работы с Windows Mixed Reality в категории "развлечения на месте".</span><span class="sxs-lookup"><span data-stu-id="2a28f-109">This document is a guide to get started with Windows Mixed Reality in the Location Based Entertainment category.</span></span> <span data-ttu-id="2a28f-110">Приведенные ниже инструкции также могут быть применимы к работе на основе местоположения, помимо развлекательных средств, таких как обучение, проектирование продукта или другие варианты использования.</span><span class="sxs-lookup"><span data-stu-id="2a28f-110">The guidance below may additionally be applicable to location-based experiences beyond entertainment such as training, product design or other use cases.</span></span>

## <a name="engineering-faq"></a><span data-ttu-id="2a28f-111">Вопросы и ответы по проектированию</span><span class="sxs-lookup"><span data-stu-id="2a28f-111">Engineering FAQ</span></span>

### <a name="hardware"></a><span data-ttu-id="2a28f-112">Оборудование</span><span class="sxs-lookup"><span data-stu-id="2a28f-112">Hardware</span></span>

<span data-ttu-id="2a28f-113">**ФОРМАТЕ Какое оборудование доступно корпорации Майкрософт и ее партнерам, которые я могу использовать в программе установки?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-113">**Q: What hardware is available from Microsoft and its partners that I can use in my setup?**</span></span>

<span data-ttu-id="2a28f-114">Ответ. Корпорация Майкрософт и ее партнеры OEM предлагают привлекательный портфель устройств для выбора в зависимости от ваших потребностей.</span><span class="sxs-lookup"><span data-stu-id="2a28f-114">A: Microsoft and its OEM partners offer a compelling portfolio of devices to choose from depending on your needs.</span></span>  

<span data-ttu-id="2a28f-115">Если вы предоставляете своим клиентам возможности, которым требуются головные гарнитуры, следующие Настольные гарнитуры от HP, Samsung и стоек прекрасно подходят.</span><span class="sxs-lookup"><span data-stu-id="2a28f-115">If the experiences you’re providing to your customers require virtual reality headsets, the following in-market headsets from HP, Samsung and Acer are a great fit.</span></span> <span data-ttu-id="2a28f-116">У каждой гарнитуры есть свои отличительные атрибуты.</span><span class="sxs-lookup"><span data-stu-id="2a28f-116">Each headset has their own differentiated attributes.</span></span> <span data-ttu-id="2a28f-117">Дополнительные сведения см. здесь.</span><span class="sxs-lookup"><span data-stu-id="2a28f-117">More details on each below.</span></span>

<span data-ttu-id="2a28f-118">Команда HP: [Сведения](https://hp.com/go/Reverbpro)</span><span class="sxs-lookup"><span data-stu-id="2a28f-118">HP Reverb: [Details](https://hp.com/go/Reverbpro)</span></span>

<span data-ttu-id="2a28f-119">Samsung Одиссэй +: [Сведения](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span><span class="sxs-lookup"><span data-stu-id="2a28f-119">Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span></span>

<span data-ttu-id="2a28f-120">Асер [Сведения](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span><span class="sxs-lookup"><span data-stu-id="2a28f-120">Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span></span>

<span data-ttu-id="2a28f-121">Если ваше расположение специализируется на смешанных или расширенных возможностях, для которых требуется использование общедоступной гарнитуры, вы можете приобрести Microsoft HoloLens 2 (теперь он открыт для предварительного заказа).</span><span class="sxs-lookup"><span data-stu-id="2a28f-121">If your location specializes in mixed or augmented reality experiences requiring the use of a see-through headset, you can procure the Microsoft HoloLens 2 (now open for pre-order interest).</span></span>  

<span data-ttu-id="2a28f-122">HoloLens 2: [Интерес по предварительным заказам](https://www.microsoft.com/en-us/hololens/buy)</span><span class="sxs-lookup"><span data-stu-id="2a28f-122">HoloLens 2: [Pre-order interest](https://www.microsoft.com/en-us/hololens/buy)</span></span>

<span data-ttu-id="2a28f-123">Если вы проводите эксперименты с возможностями, требующими расширенного представления компьютерных концепций, речи и текста, вы можете найти Azure Kinect DK в соответствии с вашими потребностями.</span><span class="sxs-lookup"><span data-stu-id="2a28f-123">If you’re experimenting with experiences that require advanced computer vision, speech and body tracking, you may find the Azure Kinect DK a fit for your needs.</span></span>  

<span data-ttu-id="2a28f-124">Kinect Azure: [Сведения](https://azure.microsoft.com/en-us/services/kinect-dk/)</span><span class="sxs-lookup"><span data-stu-id="2a28f-124">Azure Kinect: [Details](https://azure.microsoft.com/en-us/services/kinect-dk/)</span></span>

<span data-ttu-id="2a28f-125">**ФОРМАТЕ В чем состоит портфель ранец компьютеров, которые я могу использовать для запуска моего PC-модема VR?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-125">**Q: What is the portfolio of backpack PCs I can use to run my PC-tethered VR experiences?**</span></span>

<span data-ttu-id="2a28f-126">Для компьютерных систем, исставляющих микрооборудование, поставщики вычислительной техники предлагают невероятный выбор ранец ПК, созданных в соответствии с этими нуждами.</span><span class="sxs-lookup"><span data-stu-id="2a28f-126">For PC-tethered VR experiences, our OEMs offer an incredible selection of backpack PCs built exactly for that need.</span></span>

<span data-ttu-id="2a28f-127">HP только что запустила свой HP VR ранец G2, самый мощный носимого пользователем ПК, оптимизированный для произвольного роуминга, теперь с 30-процентной мощностью и с помощью графического процессора RTX 2080.</span><span class="sxs-lookup"><span data-stu-id="2a28f-127">HP just launched their HP VR backpack G2, the world’s most powerful wearable PC – optimized for free-roam experiences, now with 30% more power with an RTX 2080 GPU inside.</span></span> [<span data-ttu-id="2a28f-128">Сведения</span><span class="sxs-lookup"><span data-stu-id="2a28f-128">Details</span></span>](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a><span data-ttu-id="2a28f-129">Установка</span><span class="sxs-lookup"><span data-stu-id="2a28f-129">Setup</span></span>

<span data-ttu-id="2a28f-130">**ФОРМАТЕ Как легко настроить установку и настроить портал смешанной реальности для ЛБЕ?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-130">**Q: How can I more easily configure setup and customize the Mixed Reality Portal for LBE?**</span></span>

>[!NOTE]
><span data-ttu-id="2a28f-131">Для этой функции требуется версия 2000.19061.1011.0 или более поздняя.</span><span class="sxs-lookup"><span data-stu-id="2a28f-131">This feature requires version 2000.19061.1011.0 or greater.</span></span>  

<span data-ttu-id="2a28f-132">Может оказаться, что требуется больше настроек портала смешанной реальности, чем обычно доступно в приложении для развертывания приложений в киосках или настраиваемых интерфейсах.</span><span class="sxs-lookup"><span data-stu-id="2a28f-132">You may find that you need more customization of Mixed Reality Portal than is normally available through the app for deploying apps to kiosks or customized experiences.</span></span> <span data-ttu-id="2a28f-133">Последнее обновление портала Mixed Reality в июле поддерживает несколько дополнительных параметров, которые можно выполнить с помощью файла конфигурации, чтобы сделать следующее:</span><span class="sxs-lookup"><span data-stu-id="2a28f-133">The latest July update of Mixed Reality Portal supports several advanced settings that can be via a configuration file to do the following:</span></span>  

<span data-ttu-id="2a28f-134">Разрешить неудачные проверки системы — обычно процесс установки проверяет компьютер на совместимость с Windows Mixed Reality перед завершением установки.</span><span class="sxs-lookup"><span data-stu-id="2a28f-134">Allow failed system checks – normally the setup process checks the PC for compatibility with Windows Mixed Reality before completing setup.</span></span> <span data-ttu-id="2a28f-135">Обойти это может вызвать проблемы при попытке запуска Windows Mixed Reality при наличии проблем совместимости.</span><span class="sxs-lookup"><span data-stu-id="2a28f-135">Bypassing this may cause issues when trying to run Windows Mixed Reality if there are compatibility issues.</span></span>  

<span data-ttu-id="2a28f-136">Пропуск приложения-компаньона устройства — DCA предоставляет действия по настройке гарнитуры, предоставленные производителем, и позволяет обновлять встроенное по гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="2a28f-136">Skip Device Companion App – the DCA provides headset-specific setup steps provided by the manufacturer and allows for updating the headset’s firmware.</span></span>  

<span data-ttu-id="2a28f-137">Пропустить настройку комнаты. вместо того, чтобы получать запрос на создание границы комнаты, можно перейти непосредственно к гарнитуре в режиме «в помещении/в помещении».</span><span class="sxs-lookup"><span data-stu-id="2a28f-137">Skip room setup – instead of being prompted to create a room boundary, you can proceed directly into the headset in Seated/Standing mode.</span></span>  

<span data-ttu-id="2a28f-138">Пропустить установку приложений из магазина — обычная установка устанавливает несколько приложений Магазина, включая 3D Viewer и надстройку средства просмотра граничных 360.</span><span class="sxs-lookup"><span data-stu-id="2a28f-138">Skip installing apps from the Store - normal setup installs several Store apps including 3D Viewer and the Edge 360 Viewer add-on.</span></span> <span data-ttu-id="2a28f-139">Это приведет к пропуску установки этих приложений, но может отсутствовать функциональность устройства.</span><span class="sxs-lookup"><span data-stu-id="2a28f-139">This will skip the install of these apps, but you may be missing device functionality.</span></span>  

<span data-ttu-id="2a28f-140">Предварительный просмотр в полноэкранном режиме. на портале Mixed Reality по умолчанию будет отображаться предварительный просмотр гарнитуры в полноэкранном режиме на настольном компьютере во время использования гарнитуры.</span><span class="sxs-lookup"><span data-stu-id="2a28f-140">Show preview in full screen – Mixed Reality Portal will default to showing the headset preview in full-screen on the desktop PC while the headset is in use.</span></span>  

<span data-ttu-id="2a28f-141">Скрыть новый для боковой панели — это предотвратит расширение новой панели при запуске портала смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2a28f-141">Hide New for you side panel – this prevent the New for you panel from being expanded on launch of Mixed Reality Portal.</span></span>  

#### <a name="how-to-configure"></a><span data-ttu-id="2a28f-142">Настройка:</span><span class="sxs-lookup"><span data-stu-id="2a28f-142">How to configure:</span></span>  

<span data-ttu-id="2a28f-143">Чтобы задать любую из этих конфигураций, необходимо создать файл с именем _UserConfig. JSON_ в этом каталоге: _\\ $env: LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState_</span><span class="sxs-lookup"><span data-stu-id="2a28f-143">To set any of these configurations, you need to create a file called _UserConfig.json_ under this directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="2a28f-144">Для большинства пользователей это будет выглядеть как _C:\Users\<username > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span><span class="sxs-lookup"><span data-stu-id="2a28f-144">For most users this will look like _C:\Users\<username>\AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="2a28f-145">Файл JSON должен иметь следующее содержимое со значением "true", установленным для любого из перечисленных выше параметров, которые должны быть включены:</span><span class="sxs-lookup"><span data-stu-id="2a28f-145">The JSON file should have the below contents with “true” set for any of the above settings you want enabled:</span></span>  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
<span data-ttu-id="2a28f-146">**ФОРМАТЕ Есть ли какие-либо рекомендации по настройке плайспаце?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-146">**Q: Is there any guidance on configuring the playspace?**</span></span>

<span data-ttu-id="2a28f-147">Ответ. Настройка плайспаце должна выполняться так же, как и при настройке потребителя.</span><span class="sxs-lookup"><span data-stu-id="2a28f-147">A: Configuring a playspace should be done as you would with a consumer setup experience.</span></span> <span data-ttu-id="2a28f-148">Процесс установки комнаты также позволит определить границы комнаты.</span><span class="sxs-lookup"><span data-stu-id="2a28f-148">The Room Setup process will also let you define your room boundaries.</span></span> <span data-ttu-id="2a28f-149">Дополнительные сведения о настройке границ комнаты можно прочитать [здесь](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span><span class="sxs-lookup"><span data-stu-id="2a28f-149">More details on configuring room boundaries can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="2a28f-150">Как обсуждалось в приведенном выше документе, максимально разумная однокоординатная плайспаце обходится вокруг 5mx5m.</span><span class="sxs-lookup"><span data-stu-id="2a28f-150">As discussed in the above document the maximum reasonable single coordinate playspace is around 5mx5m.</span></span> <span data-ttu-id="2a28f-151">Если вы хотите увеличить область, можно использовать возможность использования пространственных привязок в стеке API Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="2a28f-151">If you want to have a larger area you can make use of the Spatial Anchors capability in the Windows Holographic API stack.</span></span> <span data-ttu-id="2a28f-152">Использование этого API потребует пользовательского проектирования в создаваемых вами возможностях.</span><span class="sxs-lookup"><span data-stu-id="2a28f-152">Using this API will require custom engineering in the experiences you are producing.</span></span>  

<span data-ttu-id="2a28f-153">Дополнительные сведения о том, как оптимизировать содержимое для различных размеров пространства, можно прочитать [здесь](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="2a28f-153">More details on how to optimize your content for different space sizes can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems).</span></span>
 

<span data-ttu-id="2a28f-154">**ФОРМАТЕ Мой объем памяти слишком велик и при попытке настроить работу с границами возникают ошибки. Что делать, чтобы настроить работу с большим объемом свободного роуминга?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-154">**Q: My space is too large and I’m running into errors when I try to set up a Standing experience with boundaries. What should I do to setup my large free-roam experience work?**</span></span>

<span data-ttu-id="2a28f-155">Ответ. Чтобы настроить больший объем пространства, чем ~ 18x18ft, вы не сможете использовать границы, предоставляемые системой.</span><span class="sxs-lookup"><span data-stu-id="2a28f-155">A: To setup a larger space than ~18x18ft you won’t be able to use the boundary experience provided by the system.</span></span>  <span data-ttu-id="2a28f-156">Граничные системы полагаются на использование одной фиксированной координатной точки привязки, которая может стать нестабильной, когда пользователь находится слишком далеко от привязки центрального этапа.</span><span class="sxs-lookup"><span data-stu-id="2a28f-156">The boundary systems relies on leveraging a single fixed coordinate “anchor”, which can become unstable when a user is too far from the center stage anchor.</span></span> 

<span data-ttu-id="2a28f-157">Вместо этого можно настроить режим «под», при котором не будет отображаться граница или настроены границы или плайспаце этапа.</span><span class="sxs-lookup"><span data-stu-id="2a28f-157">Instead, you can setup “seated” mode, which will not display the boundary or configure a stage bounds or playspace.</span></span>  <span data-ttu-id="2a28f-158">Затем необходимо настроить несколько пространственных привязок в приложении, чтобы они ссылались на физические области границ.</span><span class="sxs-lookup"><span data-stu-id="2a28f-158">Then, you’ll need to configure multiple spatial anchors within the app to reference physical boundary areas.</span></span> 

<span data-ttu-id="2a28f-159">Разработчик приложения несет ответственность за отображение необходимых мер защиты, чтобы пользователи не могли конфликтовать с физической окружающей обработкой.</span><span class="sxs-lookup"><span data-stu-id="2a28f-159">The application developer is responsible to display necessary safeguards so that users don’t collide with physical surroundings.</span></span>  <span data-ttu-id="2a28f-160">Это могут быть цифровые стены в рамках опыта или настраиваемый визуальный элемент "граница игры".</span><span class="sxs-lookup"><span data-stu-id="2a28f-160">These could be digital walls within the experience or a customized game boundary visual.</span></span> 

<span data-ttu-id="2a28f-161">Руководство по настройке границы комнаты для ВМР можно найти [здесь](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span><span class="sxs-lookup"><span data-stu-id="2a28f-161">Guidance on setting up the room boundary with WMR can be found [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="2a28f-162">**ФОРМАТЕ Где находится источник плайспаце?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-162">**Q: Where is the origin of the playspace?**</span></span>

<span data-ttu-id="2a28f-163">Ответ. Источник плайспаце определяется возможностями настройки комнаты, точнее, в частности, при нажатии центральной кнопки во время установки.</span><span class="sxs-lookup"><span data-stu-id="2a28f-163">A: The origin of the playspace is determined by the Room Setup experience, more specifically the HMD position when the Center button is pressed during setup.</span></span> 

### <a name="multi-player-setup"></a><span data-ttu-id="2a28f-164">УСТАНОВКА С НЕСКОЛЬКИМИ ИГРОКАМИ</span><span class="sxs-lookup"><span data-stu-id="2a28f-164">MULTI-PLAYER SETUP</span></span>

<span data-ttu-id="2a28f-165">**ФОРМАТЕ Я развертываю несколько игроков в моем месте. Поддерживается ли в Windows Mixed Reality?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-165">**Q: I’m deploying a multi-player experience in at my venue. Is that supported on Windows Mixed Reality?**</span></span>

<span data-ttu-id="2a28f-166">Ответ. Инструмент "соединитель пространственных данных" в смешанной реальности — это бета-функция, которая позволяет локализовать несколько игроков в одном пространстве, позволяя перенести пространственные данные с одного компьютера на другой.</span><span class="sxs-lookup"><span data-stu-id="2a28f-166">A: The Mixed Reality Spatial Data Packager tool is a beta feature that allows localizing multiple players in the same space by enabling porting of the spatial data from one PC to another.</span></span> <span data-ttu-id="2a28f-167">Вы можете получить доступ к этому средству и узнать больше о нем [здесь](mixedrealityspatialdatapackager.md).</span><span class="sxs-lookup"><span data-stu-id="2a28f-167">You can access the tool and learn more about it [here](mixedrealityspatialdatapackager.md).</span></span>

### <a name="tracking"></a><span data-ttu-id="2a28f-168">ОТСЛЕЖИВАЮЩ</span><span class="sxs-lookup"><span data-stu-id="2a28f-168">TRACKING</span></span>

<span data-ttu-id="2a28f-169">Вопрос. Как работает технология отслеживания на гарнитурах Windows Mixed Reality?</span><span class="sxs-lookup"><span data-stu-id="2a28f-169">Q: How does the tracking technology in the Windows Mixed Reality headsets work?</span></span>  

<span data-ttu-id="2a28f-170">Смешанная реальность использует ту же технологию отслеживания, что и HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2a28f-170">Mixed Reality shares the same tracking technology as the HoloLens.</span></span> <span data-ttu-id="2a28f-171">Чтобы узнать больше о внутренней системе отслеживания, ознакомьтесь с документацией [здесь](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system).</span><span class="sxs-lookup"><span data-stu-id="2a28f-171">To learn more about the inside-out tracking system, check out the documentation [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system).</span></span>

<span data-ttu-id="2a28f-172">Описание того, как работает система пространственного сопоставления более высокого уровня, можно прочитать [здесь](spatial-mapping-design.md).</span><span class="sxs-lookup"><span data-stu-id="2a28f-172">For a description of how the higher-level spatial mapping system works you can read our description [here](spatial-mapping-design.md).</span></span>

<span data-ttu-id="2a28f-173">**ФОРМАТЕ Существуют ли рекомендации по получению надежного тома отслеживания?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-173">**Q: Are there any best practices for getting a reliable tracking volume?**</span></span>

<span data-ttu-id="2a28f-174">Чтобы лучше настроить среду для отслеживания успеха, можно ознакомиться с рекомендациями, приведенными в этой [записи](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="2a28f-174">To best configure the environment for tracking success, you can read best practices in this [post](environment-considerations-for-hololens.md).</span></span>

<span data-ttu-id="2a28f-175">**ФОРМАТЕ Существуют ли какие-либо особенности, связанные с отслеживанием дисковых пространств или оптимизацией, которые следует учитывать?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-175">**Q: Are there any specific nuances with tracking in warehouse-scale spaces or optimizations to consider?**</span></span>

<span data-ttu-id="2a28f-176">Ответ. Следующие рекомендации помогут получить более надежный том отслеживания.</span><span class="sxs-lookup"><span data-stu-id="2a28f-176">A: The following practices can help with getting a more reliable tracking volume:</span></span>  

<span data-ttu-id="2a28f-177">Предоставление разнообразных функций в комнате, которые перекрываются в нескольких позициях, поможет системе отслеживания получить твердую блокировку.</span><span class="sxs-lookup"><span data-stu-id="2a28f-177">Providing a variety of features in the room that overlap at multiple positions will help the tracking system get a solid lock.</span></span> <span data-ttu-id="2a28f-178">Представьте себе случайные цвета и штриховки, а не сплошные линии стиля контура.</span><span class="sxs-lookup"><span data-stu-id="2a28f-178">Think of random paint splatters and hatching rather than using solid contour style lines.</span></span> 

<span data-ttu-id="2a28f-179">Сократите динамический диапазон освещения в своей области, где это возможно.</span><span class="sxs-lookup"><span data-stu-id="2a28f-179">Minimize the dynamic range of lighting in your area where possible.</span></span> <span data-ttu-id="2a28f-180">Камеры отслеживания в нашей смешанной реальности ХМДС не HDR и имеют АГК (автоматическое усиление) и AEC (автовыдержка), чтобы работать с различным освещением.</span><span class="sxs-lookup"><span data-stu-id="2a28f-180">The tracking cameras on our Mixed Reality HMDs are not HDR and have AGC (auto gain) and AEC (auto exposure) going in order to deal with different lighting.</span></span> <span data-ttu-id="2a28f-181">В зависимости от распределения поверхности, шаблонов и контрастов, АГК или AEC могут задержать вас в любом белом или черном помещении, позволяющем размыть функции, которые могут находиться в противоположном «цвете».</span><span class="sxs-lookup"><span data-stu-id="2a28f-181">Depending on the distribution of surface light, patterns and contrast, either AGC or AEC may conclude you’re in a pretty much all white or black room which can wash out your features that may be in the opposite “color”.</span></span> <span data-ttu-id="2a28f-182">Если вы пытаетесь получить внутреннюю картинку перед внешним окном с ярко-летним периодом, и вы настроите экспозицию так, чтобы вы могли видеть подробные сведения, то все во внутренней части будут подходящими и черними.</span><span class="sxs-lookup"><span data-stu-id="2a28f-182">If you are trying to take an interior picture in front of an exterior window with bright daylight behind and you adjust exposure so you can see detail outside, then everything on the interior is underexposed and black.</span></span> <span data-ttu-id="2a28f-183">Или если задано значение для внутри, то все, что находится за пределами, теперь является недоступным и все белым.</span><span class="sxs-lookup"><span data-stu-id="2a28f-183">Or if set for inside, then everything outside is now overexposed and all white.</span></span>  

<span data-ttu-id="2a28f-184">Прожекторы в комнате (даже накладные расходы), которые находятся в представлении, если отслеживание камер иногда может быть прекращено, что приводит к путанице в контексте AEC/АГК для камер отслеживания.</span><span class="sxs-lookup"><span data-stu-id="2a28f-184">Spotlights in a room (even overhead) that are in view if tracking cameras can sometimes be culprits which confuse the AEC/AGC of the tracking cameras.</span></span> <span data-ttu-id="2a28f-185">Неструктурированное и рассеянное освещение.</span><span class="sxs-lookup"><span data-stu-id="2a28f-185">Flat/diffused lighting helps.</span></span>  

### <a name="mixed-reality-cloud-services-and-azure"></a><span data-ttu-id="2a28f-186">ОБЛАЧНЫЕ СЛУЖБЫ И AZURE СМЕШАННОЙ РЕАЛЬНОСТИ</span><span class="sxs-lookup"><span data-stu-id="2a28f-186">MIXED REALITY CLOUD SERVICES AND AZURE</span></span> 

<span data-ttu-id="2a28f-187">**ФОРМАТЕ Как можно Microsoft Azure помочь в масштабе бизнеса?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-187">**Q: How can Microsoft Azure help my business scale?**</span></span>

<span data-ttu-id="2a28f-188">Ответ. На основе Azure, а также удаленное управление может помочь бизнес-управляемым данным, снизить эксплуатационные расходы и масштабировать развертывание в существующих и новых местах.</span><span class="sxs-lookup"><span data-stu-id="2a28f-188">A: Azure based onsite and remote management can help your business be data-driven, reduce operational costs and scale deployment across existing and new locations.</span></span> <span data-ttu-id="2a28f-189">Облачные службы Azure, такие как хранилище Azure, функции Azure, служба приложений, сеть Azure и центр Интернета вещей, могут помочь в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="2a28f-189">Azure cloud services such as Azure Storage, Azure Functions, App Service, Azure Networking and IOT Hub can help with the following use cases:</span></span>  

<span data-ttu-id="2a28f-190">Удаленное развертывание устройств & Управление</span><span class="sxs-lookup"><span data-stu-id="2a28f-190">Remote Device Deployment & Management</span></span> 

<span data-ttu-id="2a28f-191">Аналитика на сайте в режиме реального времени</span><span class="sxs-lookup"><span data-stu-id="2a28f-191">Real Time Onsite Analytics</span></span> 

<span data-ttu-id="2a28f-192">Интеллектуальные адаптируемые ЛБЕ игрового процесса</span><span class="sxs-lookup"><span data-stu-id="2a28f-192">Intelligent Adaptable LBE Gameplay</span></span> 

<span data-ttu-id="2a28f-193">Потоковая передача и развертывание содержимого ЛБЕ</span><span class="sxs-lookup"><span data-stu-id="2a28f-193">LBE Content Streaming and Deployment</span></span> 

<span data-ttu-id="2a28f-194">Тепловой карты предпочтений ЛБЕ Player</span><span class="sxs-lookup"><span data-stu-id="2a28f-194">LBE Player Preference Heatmap</span></span> 

<span data-ttu-id="2a28f-195">Система резервирования и резервирования ЛБЕ</span><span class="sxs-lookup"><span data-stu-id="2a28f-195">LBE Reservation and Booking System</span></span> 

<span data-ttu-id="2a28f-196">**ФОРМАТЕ Я разрабатывает пространственный ММОГ для развертывания в огромном объеме. Какие службы помогают управлять содержимым и сохраняемостью объектов?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-196">**Q: I’m developing a spatial MMOG to deploy over a massive footprint. Any services that help me manage my content and object persistence?**</span></span>

<span data-ttu-id="2a28f-197">Ответ. Пространственные привязки Azure — это новая служба смешанной реальности, которая позволяет выполнять многопользовательские и пространственные возможности смешанной реальности на устройствах HoloLens, iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="2a28f-197">A: Azure Spatial Anchors is a new Mixed Reality service that enables multi-user, spatially aware mixed reality experiences across HoloLens, iOS and Android devices.</span></span> <span data-ttu-id="2a28f-198">Дополнительные сведения об использовании пространственных привязок Azure см. [здесь](https://azure.microsoft.com/en-us/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="2a28f-198">You can learn more about Azure Spatial Anchors [here](https://azure.microsoft.com/en-us/services/spatial-anchors/).</span></span>

<span data-ttu-id="2a28f-199">**ФОРМАТЕ. Наша работа специализируется на работе с несколькими игроками и мне хотелось бы сосредоточиться на разработке содержимого и интерфейсной разработки. Существуют ли предложения, которые могут помочь в начальной загрузке или разгрузке серверной разработки?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-199">**Q. Our venue specializes in multi-player experiences and I’d like to focus our development time on content and front-end development. Are there offerings that can help me bootstrap or offload backend development?**</span></span>

<span data-ttu-id="2a28f-200">Ответ. Azure PlayFab — это полнофункциональная серверная платформа для игр в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="2a28f-200">A: Azure PlayFab is a complete backend platform for live games.</span></span> <span data-ttu-id="2a28f-201">Дополнительные сведения см. [здесь](https://playfab.com/).</span><span class="sxs-lookup"><span data-stu-id="2a28f-201">You can learn more about it [here](https://playfab.com/).</span></span>

### <a name="misc"></a><span data-ttu-id="2a28f-202">Информации</span><span class="sxs-lookup"><span data-stu-id="2a28f-202">Misc</span></span>

<span data-ttu-id="2a28f-203">**ФОРМАТЕ Я использую Стеамвр для развертывания моего опыта. Работает ли Windows Mixed Reality с Стеамвр?**</span><span class="sxs-lookup"><span data-stu-id="2a28f-203">**Q: I use SteamVR to deploy my experiences. Does Windows Mixed Reality work with SteamVR?**</span></span>

<span data-ttu-id="2a28f-204">Ответ. Windows Mixed Reality для Стеамвр позволяет пользователям запускать Стеамврные возможности на впечатляющих наушниках Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="2a28f-204">A: Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="2a28f-205">Дополнительные сведения о Стеамвр с ВМР см. [здесь](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="2a28f-205">Learn more about SteamVR with WMR [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span></span>

### <a name="support-and-community"></a><span data-ttu-id="2a28f-206">Поддержка и сообщество</span><span class="sxs-lookup"><span data-stu-id="2a28f-206">Support and community</span></span>  

<span data-ttu-id="2a28f-207">Ниже приведено несколько полезных ресурсов, которые помогут привлечь экспертов к нашей группе, получить поддержку по устранению неполадок и принять участие в широком сообществе разработчиков смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2a28f-207">Below are a few helpful resources to engage with subject matter experts on our team, get troubleshooting support, and contribute to the broader mixed reality dev community.</span></span>  

<span data-ttu-id="2a28f-208">При возникновении проблем с общедоступными компонентами обратитесь к разделу об ошибке с помощью центра отзывов. инструкции см. на этой [странице](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback).</span><span class="sxs-lookup"><span data-stu-id="2a28f-208">If you run into issues with any publicly released features, please file a bug using Feedback Hub.For guidance, please refer to this [page](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span>

<span data-ttu-id="2a28f-209">Дополнительные сведения об устранении неполадок с ВМР см. в статье [запрос в службу](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782)поддержки клиентов.</span><span class="sxs-lookup"><span data-stu-id="2a28f-209">For additional troubleshooting help with WMR please get in touch with our customer support team by filing a [support request](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).</span></span>

<span data-ttu-id="2a28f-210">Присоединяйтесь к нашему каналу резервного времени Холодевелоперс для привлечения разработчиков, работающих над смешанной реальности и экспертами из группы: [AKA.MS/holodevelopers](https://aka.ms/holodevelopers)</span><span class="sxs-lookup"><span data-stu-id="2a28f-210">Join our HoloDevelopers Slack channel to engage with the developers working on mixed reality and subject matter experts from the team: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span></span>

<span data-ttu-id="2a28f-211">Сайте Новости, события и обновления см. в группе "связи разработчиков смешанной реальности".@MxdRealityDev</span><span class="sxs-lookup"><span data-stu-id="2a28f-211">Twitter: Follow our Mixed Reality Developer Relations team for news, events and updates @MxdRealityDev</span></span> 

<span data-ttu-id="2a28f-212">Если вы пойдете в Сан-Франциско или около него, в Microsoft реактора всегда есть нечто другое.</span><span class="sxs-lookup"><span data-stu-id="2a28f-212">If you happen to be in or around San Francisco, there’s always something going on at the Microsoft Reactor.</span></span> <span data-ttu-id="2a28f-213">Наш календарь событий можно просмотреть [здесь](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco).</span><span class="sxs-lookup"><span data-stu-id="2a28f-213">You can see our calendar of events [here](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco).</span></span>