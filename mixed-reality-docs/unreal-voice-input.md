---
title: Речевой ввод
description: Объясняется, как использовать речевой ввод
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835327"
---
# <a name="voice-input"></a><span data-ttu-id="fc1da-104">Речевой ввод</span><span class="sxs-lookup"><span data-stu-id="fc1da-104">Voice Input</span></span>

<span data-ttu-id="fc1da-105">Чтобы включить распознавание речи в HoloLens, разработчику необходимо включить "микрофон" в нереальном редакторе в разделе "Параметры проекта" > "платформа > HoloLens >".</span><span class="sxs-lookup"><span data-stu-id="fc1da-105">To enable speech recognition on HoloLens, the developer needs to enable “Microphone” in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> <span data-ttu-id="fc1da-106">На устройстве также должно быть включено распознавание речи в параметрах > конфиденциальность > речи и использовать английский язык.</span><span class="sxs-lookup"><span data-stu-id="fc1da-106">The device must also have Speech recognition enabled in Settings > Privacy > Speech and use the English language.</span></span>

![Параметры распознавания речи Windows](images/unreal/speech-recognition-settings.png)

<span data-ttu-id="fc1da-108">Рекомендуется включить распознавание речи в сети для наилучшего возможного качества службы.</span><span class="sxs-lookup"><span data-stu-id="fc1da-108">It’s recommended to enable Online speech recognition too for the best possible quality of the service.</span></span> <span data-ttu-id="fc1da-109">Технические сведения о распознавании речи в HoloLens можно найти [здесь](voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="fc1da-109">Technical details for speech recognition on HoloLens can be found [here](voice-input.md)</span></span>

<span data-ttu-id="fc1da-110">Затем пользователь увидит диалоговое окно, посвященное включению микрофона при первом запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="fc1da-110">Then user will see a dialog about enabling the microphone when the application first starts.</span></span> <span data-ttu-id="fc1da-111">Если пользователь выбрал Да, приложение начнет получать речевой ввод.</span><span class="sxs-lookup"><span data-stu-id="fc1da-111">If a user selects Yes, the application will begin getting voice input.</span></span>

<span data-ttu-id="fc1da-112">Речевому вводу не требуется специальный API Windows Mixed Reality, который создается на основе существующего API-интерфейса для сопоставления входных данных из нереального модуля 4.</span><span class="sxs-lookup"><span data-stu-id="fc1da-112">Speech input doesn’t require a special Windows Mixed Reality API and is instead built upon the existing Unreal Engine 4 Input mapping API.</span></span> <span data-ttu-id="fc1da-113">Дополнительные сведения об использовании входного API см. [здесь](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html) .</span><span class="sxs-lookup"><span data-stu-id="fc1da-113">Details on how to use the Input API are [here](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span></span>

<span data-ttu-id="fc1da-114">Сопоставления речи добавлены в раздел "привязки" обработчика — входные данные ниже действий и сопоставлений осей.</span><span class="sxs-lookup"><span data-stu-id="fc1da-114">Speech Mappings have been added to the Bindings section of Engine – Input below Action and Axis Mappings.</span></span> 

![Входное настройки UE4 Engine](images/unreal/engine-input.png)
 
<span data-ttu-id="fc1da-116">Ниже приведен пример дополнительного мониторинга для «перехода на мир».</span><span class="sxs-lookup"><span data-stu-id="fc1da-116">Here is an example of added monitoring for the world “jump”.</span></span> <span data-ttu-id="fc1da-117">Можно использовать любые английские слова или короткие предложения.</span><span class="sxs-lookup"><span data-stu-id="fc1da-117">Any English word(s) or short sentences can be used.</span></span> 

<span data-ttu-id="fc1da-118">После добавления речевого сопоставления с помощью параметров проекта разработчик может использовать стандартную нереальную логику для обработки входных данных, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="fc1da-118">After a Speech Mapping is added via Project Settings, a developer can then use standard Unreal logic to handle the input, as in the following example:</span></span> 
 
![Простое действие для голоса](images/unreal/input-action-bp.png)
