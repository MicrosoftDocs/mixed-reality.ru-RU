---
title: Взгляните и зафиксируйте
description: Общие сведения о входной модели "наблюдатель и фиксация" — с помощью взгляда или головного входа.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Смешанная реальность, Взгляните, определение целевой платформы, взаимодействие, проектирование, отслеживание глаз, отслеживание головок
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375851"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="2ddf5-104">Взгляните и зафиксируйте</span><span class="sxs-lookup"><span data-stu-id="2ddf5-104">Gaze and commit</span></span>

<span data-ttu-id="2ddf5-105">_Взгляд и фиксация_ — это фундаментальная модель ввода, тесно связанная с тем, как мы взаимодействуя с нашими компьютерами с помощью мыши: _Point & щелкните_.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-105">_Gaze and commit_ is a fundamental input model that is closely related with the way we're interacting with our computers using the mouse: _Point & click_.</span></span>
<span data-ttu-id="2ddf5-106">На этой странице представлены два типа входных данных взгляда ("руководитель" и "глаз-взгляд") и различные типы действий фиксации.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> 
<span data-ttu-id="2ddf5-107">_Взгляд и фиксация_ считаются дальней моделью ввода с косвенной манипуляцией.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span>
<span data-ttu-id="2ddf5-108">Это означает, что лучше использовать его для взаимодействия с holographic, которая недоступна.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-108">This means it is best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="2ddf5-109">Гарнитуры смешанной реальности могут использовать положение и ориентацию заголовка пользователя для определения вектора направления головки.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="2ddf5-110">Ее можно представить как лазер, который указывает прямо вперед из точки между глаз пользователя.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-110">You can think of this as a laser that points straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="2ddf5-111">Это довольно приблизительная оценка того, куда смотрит пользователь.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="2ddf5-112">Приложение может пересекать этот луч с виртуальными или реальными объектами и нарисовать курсор в этом расположении, чтобы сообщить пользователю о том, что в настоящее время нацелено на них.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they are currently targeting.</span></span>

<span data-ttu-id="2ddf5-113">Помимо головного взгляда, некоторые гарнитуры смешанной реальности, например HoloLens 2, включают системы отслеживания взглядов, которые создают вектор взгляда.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="2ddf5-114">Это обеспечивает высокоточное измерение направления взгляда пользователя.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="2ddf5-115">В обоих случаях взгляд представляет важный сигнал для намерения пользователя.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="2ddf5-116">Чем лучше система может интерпретировать и прогнозировать предполагаемые действия пользователя, тем выше степень удовлетворенности пользователей и повышение производительности.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-116">The better the system can interpret and predict the user's intended actions, user satisfaction increases and performance improves.</span></span>

<span data-ttu-id="2ddf5-117">Ниже приведено несколько примеров того, как разработчику смешанной реальности можно воспользоваться преимуществами от головного взгляда или глаза.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="2ddf5-118">Ваше приложение может быть пересекается с голограммами в сцене, чтобы определить, где именно внимание пользователь (точнее, с глазом).</span><span class="sxs-lookup"><span data-stu-id="2ddf5-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="2ddf5-119">Приложение может переключаться между жестами и нажатиями контроллеров на основе взгляда пользователя, позволяя пользователю легко выбирать, активировать, захватить, прокручивать или иным образом взаимодействовать с их голограммами.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-119">Your app can channel gestures and controller presses based on the user's gaze, letting the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="2ddf5-120">Приложение может позволить пользователю размещать голограммы на реальных поверхностях, пересекать их лучом с помощью сетки пространственных сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="2ddf5-121">Приложение может быть уверенным в том, что пользователь *не* смотрит в направлении важного объекта, что может привести к тому, что ваше приложение предоставит визуальные и звуковые подсказки для включения этого объекта.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-121">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="2ddf5-122">Поддержка устройств</span><span class="sxs-lookup"><span data-stu-id="2ddf5-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2ddf5-123"><strong>Модель ввода</strong></span><span class="sxs-lookup"><span data-stu-id="2ddf5-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="2ddf5-124"><a href="hololens-hardware-details.md"><strong>HoloLens (1-го поколения)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2ddf5-124"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2ddf5-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2ddf5-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2ddf5-126"><a href="immersive-headset-hardware-details.md"><strong>Иммерсивные гарнитуры</strong></a></span><span class="sxs-lookup"><span data-stu-id="2ddf5-126"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2ddf5-127">Направление головы и фиксация</span><span class="sxs-lookup"><span data-stu-id="2ddf5-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="2ddf5-128">✔ Рекомендуется</span><span class="sxs-lookup"><span data-stu-id="2ddf5-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="2ddf5-129">✔ Рекомендуется (третий вариант <a href="interaction-fundamentals.md">см. в разделе других возможностей</a>)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="2ddf5-130">➕ Альтернативный вариант</span><span class="sxs-lookup"><span data-stu-id="2ddf5-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="2ddf5-131">Определение направления взгляда и фиксация</span><span class="sxs-lookup"><span data-stu-id="2ddf5-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="2ddf5-132">❌ недоступна</span><span class="sxs-lookup"><span data-stu-id="2ddf5-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="2ddf5-133">✔ Рекомендуется (третий вариант <a href="interaction-fundamentals.md">см. в разделе других возможностей</a>)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="2ddf5-134">❌ недоступна</span><span class="sxs-lookup"><span data-stu-id="2ddf5-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="2ddf5-135">Взгляд</span><span class="sxs-lookup"><span data-stu-id="2ddf5-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="2ddf5-136">Взгляните на глаза или голову?</span><span class="sxs-lookup"><span data-stu-id="2ddf5-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="2ddf5-137">При возникновении вопроса о том, следует ли использовать входную модель "глаз-взгляд и фиксация" или "Head-взгляд и фиксация", необходимо учитывать несколько моментов.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-137">There are several considerations to take into account when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="2ddf5-138">Если вы разрабатываете для создания впечатляющих головных телефонов или для HoloLens (1-го поколения), то по своему выбору просто: Head-взгляд и Commit.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-138">If you're developing for an immersive headset or for HoloLens (1st gen) then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="2ddf5-139">Если вы разрабатываете для HoloLens 2, выбор будет немного сложнее, поэтому важно понимать преимущества и проблемы, которые поставляются с каждым из них.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-139">If you're developing for HoloLens 2, the choice becomes a little harder which is why it's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="2ddf5-140">Мы откомпилированы некоторые широкие возможности Pro и Con, приведенные в таблице ниже, чтобы отличить нацеливание от заголовков и глаз.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-140">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="2ddf5-141">Это далеко не все, и мы рекомендуем изучить дополнительные сведения о нацеливании на глаза в смешанной реальности здесь:</span><span class="sxs-lookup"><span data-stu-id="2ddf5-141">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="2ddf5-142">[Отслеживание взгляда на hololens 2](eye-tracking.md): общее введение нашей новой возможности отслеживания взгляда на hololens 2, включая некоторые руководства для разработчиков.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-142">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="2ddf5-143">[Взаимодействие с глазом взгляда](eye-gaze-interaction.md): рекомендации по проектированию и рекомендации при планировании использования отслеживания взгляда в качестве входных данных.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-143">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="2ddf5-144"><strong>Глаз — нацеленность на взгляд</strong></span><span class="sxs-lookup"><span data-stu-id="2ddf5-144"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="2ddf5-145"><strong>Нацеленность на головной взгляд</strong></span><span class="sxs-lookup"><span data-stu-id="2ddf5-145"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2ddf5-146">Ускоряет!</span><span class="sxs-lookup"><span data-stu-id="2ddf5-146">Fast!</span></span></td>
        <td><span data-ttu-id="2ddf5-147">Сравнен</span><span class="sxs-lookup"><span data-stu-id="2ddf5-147">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2ddf5-148">Низкие усилия (что очень мало, чем требуется перемещение текста)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-148">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="2ddf5-149">Может быть фатигуинг-возможно дискомфорт (например, с ограничением горловины)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-149">Can be fatiguing - Possible discomfort (e.g., neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2ddf5-150">Не требует курсора, но рекомендуется оставить слабый отзыв</span><span class="sxs-lookup"><span data-stu-id="2ddf5-150">Does not require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="2ddf5-151">Требуется для отображения курсора</span><span class="sxs-lookup"><span data-stu-id="2ddf5-151">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2ddf5-152">Нет движений плавного взгляда, например, не подходит для рисования</span><span class="sxs-lookup"><span data-stu-id="2ddf5-152">No smooth eye movements – e.g., not good for drawing</span></span></td>
        <td><span data-ttu-id="2ddf5-153">Более контролируемые и явные</span><span class="sxs-lookup"><span data-stu-id="2ddf5-153">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2ddf5-154">Сложная задача для очень маленьких целей (например, маленьких кнопок или ссылок)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-154">Difficult for very small targets (e.g., tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="2ddf5-155">Против!</span><span class="sxs-lookup"><span data-stu-id="2ddf5-155">Reliable!</span></span> <span data-ttu-id="2ddf5-156">Отличная резервная стратегия!</span><span class="sxs-lookup"><span data-stu-id="2ddf5-156">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2ddf5-157">...</span><span class="sxs-lookup"><span data-stu-id="2ddf5-157">...</span></span></td>
        <td><span data-ttu-id="2ddf5-158">...</span><span class="sxs-lookup"><span data-stu-id="2ddf5-158">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="2ddf5-159">Независимо от того, используется ли для вашей входной модели «выборка» или «глаз-взгляд» с разными наборами ограничений конструктора, которые будут рассматриваться отдельно в статьях « [взгляд-взгляд](gaze-and-commit-eyes.md) » и «фиксация», «Head» и « [фиксация](gaze-and-commit-head.md) ».</span><span class="sxs-lookup"><span data-stu-id="2ddf5-159">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model comes with different sets of design constraints, which will be covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="2ddf5-160">Cursor</span><span class="sxs-lookup"><span data-stu-id="2ddf5-160">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2ddf5-161">Для головного взгляда в большинстве приложений следует использовать [курсор](cursors.md) (или другой индикатор аудита или визуального отображения), чтобы дать пользователю уверенность в том, с чем они взаимодействуют.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-161">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="2ddf5-162">Как правило, этот курсор размещается в мире, где первый из них сначала пересекает объект, что может быть голограммой или реальной поверхностью.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-162">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="2ddf5-163">Для глаза, как правило, рекомендуется *не* отображать курсор, так как это может быстро стать нежелательным и непонятным для пользователя.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-163">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="2ddf5-164">Вместо этого можно выделить визуальные целевые объекты или использовать очень бледный курсор, чтобы предоставить уверенность о том, с чем будет взаимодействовать пользователь.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-164">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="2ddf5-165">Дополнительные сведения см. в нашем руководстве по [проектированию для получения данных на основе глаз](eye-tracking.md) в HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-165">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="2ddf5-166">![пример визуального курсора для отображения взгляда](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-166">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="2ddf5-167">*Изображение: пример визуального курсора для отображения взгляда*</span><span class="sxs-lookup"><span data-stu-id="2ddf5-167">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="2ddf5-168">Фиксация</span><span class="sxs-lookup"><span data-stu-id="2ddf5-168">Commit</span></span>
<span data-ttu-id="2ddf5-169">После того как вы говорите о _различных способах взглянуть на_ целевой объект, давайте поговорим немного подробнее о части _фиксации_ в _взгляде и фиксации_.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-169">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="2ddf5-170">После нацеливания на объект или элемент пользовательского интерфейса пользователь может взаимодействовать с ним или щелкать его, используя Вторичный вход.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-170">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="2ddf5-171">Это называется этапом фиксации входной модели.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-171">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="2ddf5-172">Поддерживаются следующие методы фиксации:</span><span class="sxs-lookup"><span data-stu-id="2ddf5-172">The following commit methods are supported:</span></span>
- <span data-ttu-id="2ddf5-173">Жест касания воздуха (т. е. создать руку перед вами и объединить указатель и палец)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-173">Air tap hand gesture (i.e., raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="2ddf5-174">Скажите _"выбрать"_ или одну из целевых голосовых команд</span><span class="sxs-lookup"><span data-stu-id="2ddf5-174">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="2ddf5-175">Нажатие одной кнопки на кнопке [HoloLens](hardware-accessories.md#hololens-clicker)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-175">Press a single button on a [HoloLens Clicker](hardware-accessories.md#hololens-clicker)</span></span>
- <span data-ttu-id="2ddf5-176">Нажмите кнопку "A" на игровом планшете Xbox</span><span class="sxs-lookup"><span data-stu-id="2ddf5-176">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="2ddf5-177">Нажмите кнопку "A" на адаптивном контроллере Xbox</span><span class="sxs-lookup"><span data-stu-id="2ddf5-177">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="2ddf5-178">Жест взгляда и касания воздуха</span><span class="sxs-lookup"><span data-stu-id="2ddf5-178">Gaze and air tap gesture</span></span>
<span data-ttu-id="2ddf5-179">Касание — это жест касания с положением руки вертикально.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-179">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="2ddf5-180">Чтобы выполнить касание, поднимите указатель пальца до позиции готовности, затем проведите сжатие с помощью бегунка, а затем поднимите палец пальца до выпуска.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-180">To perform an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="2ddf5-181">В HoloLens (1-й общий) поток касания является наиболее распространенным вторичным входом.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-181">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="2ddf5-182">![палец в положении готовности](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-182">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="2ddf5-183">**Палец в месте готовности**</span><span class="sxs-lookup"><span data-stu-id="2ddf5-183">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2ddf5-184">![нажмите палец вниз, чтобы коснуться или щелкнуть](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-184">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="2ddf5-185">**Нажмите палец вниз, чтобы коснуться или щелкнуть**</span><span class="sxs-lookup"><span data-stu-id="2ddf5-185">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="2ddf5-186">В HoloLens 2 также доступен воздушный нажим.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-186">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="2ddf5-187">Она была ослаблена от исходной версии.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-187">It has been relaxed from the original version.</span></span> <span data-ttu-id="2ddf5-188">Теперь поддерживаются почти все типы сжатий, если рука по-прежнему находится в вертикальном и удерживаемом виде.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-188">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="2ddf5-189">Это значительно упрощает для пользователей знакомство с жестом и его использование.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-189">This makes it much easier for users to learn and perform the gesture.</span></span> <span data-ttu-id="2ddf5-190">Новое касание Air заменяет старое, используя тот же API, поэтому существующие приложения будут автоматически создавать новое поведение после повторной компиляции для HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-190">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="2ddf5-191">Посмотрите и выберем команду "Select"</span><span class="sxs-lookup"><span data-stu-id="2ddf5-191">Gaze and "Select" voice command</span></span>
<span data-ttu-id="2ddf5-192">Речевая команда — один из основных методов взаимодействия в смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-192">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="2ddf5-193">Он предоставляет мощный механизм для управления системой.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-193">It provides a very powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="2ddf5-194">Существуют различные типы моделей речевого взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-194">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="2ddf5-195">Универсальная команда "Select", которая выполняет нажатие или фиксацию в качестве вторичного входа.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-195">The generic "Select" command that performs a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="2ddf5-196">Команды объекта (например, "Close" или "make" больше ") выполняют и фиксируют действие в качестве вторичного входа.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-196">Object commands (e.g., "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="2ddf5-197">Для глобальных команд (например, "перейти к началу") целевой объект не требуется.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-197">Global commands (e.g., "Go to start") don't require a target.</span></span>
- <span data-ttu-id="2ddf5-198">Пользовательские интерфейсы или сущности диалога, такие как Кортана, имеют естественный язык AI.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-198">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="2ddf5-199">Пользовательские команды Voice</span><span class="sxs-lookup"><span data-stu-id="2ddf5-199">Custom voice commands</span></span>

<span data-ttu-id="2ddf5-200">Чтобы получить дополнительные сведения, а также полный список доступных голосов и способов их использования, ознакомьтесь с нашим руководством по [голосовым командам](voice-design.md) .</span><span class="sxs-lookup"><span data-stu-id="2ddf5-200">To find out more details as well as a comprehensive list of available voice commands and how to use them, check out our [voice commanding](voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="2ddf5-201">Элемент "взгляд" и "HoloLens"</span><span class="sxs-lookup"><span data-stu-id="2ddf5-201">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2ddf5-202">Щелчок HoloLens — это первое периферийное устройство, созданное специально для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-202">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="2ddf5-203">Он входит в состав выпуска HoloLens (1-го поколения) разработки.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-203">It is included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="2ddf5-204">Щелчок HoloLens позволяет пользователю щелкнуть с минимальным движением руки и зафиксировать его как Вторичный вход.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-204">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="2ddf5-205">Щелчок HoloLens подключается к HoloLens (1-го поколения) или HoloLens 2 с помощью Bluetooth низкого энергопотребления (БТЛЕ).</span><span class="sxs-lookup"><span data-stu-id="2ddf5-205">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="2ddf5-206">Дополнительные сведения и инструкции по связыванию устройства</span><span class="sxs-lookup"><span data-stu-id="2ddf5-206">More information and instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="2ddf5-207">*Изображение: щелчок HoloLens*</span><span class="sxs-lookup"><span data-stu-id="2ddf5-207">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![Щелчок HoloLens](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="2ddf5-209">Взгляд и контроллер беспроводной связи Xbox</span><span class="sxs-lookup"><span data-stu-id="2ddf5-209">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2ddf5-210">Контроллер беспроводной связи Xbox выполняет нажатие кнопки как Вторичный вход, используя кнопку "A".</span><span class="sxs-lookup"><span data-stu-id="2ddf5-210">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="2ddf5-211">Устройство сопоставляется с набором действий по умолчанию, которые помогают перемещаться по системе и управлять ей.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-211">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="2ddf5-212">Если вы хотите настроить контроллер, используйте приложение Xbox "стандартные" для настройки контроллера беспроводной сети Xbox.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-212">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="2ddf5-213">Как связать контроллер Xbox с компьютером</span><span class="sxs-lookup"><span data-stu-id="2ddf5-213">How to pair an Xbox controller with your PC</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="2ddf5-214">*Образ: Беспроводной контроллер Xbox*</span><span class="sxs-lookup"><span data-stu-id="2ddf5-214">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Контроллер беспроводной связи Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="2ddf5-216">Взгляд и адаптивный контроллер Xbox</span><span class="sxs-lookup"><span data-stu-id="2ddf5-216">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="2ddf5-217">Адаптивный контроллер Xbox, разработанный в основном для удовлетворения потребностей игр с ограниченным мобильным доступом, является единым концентратором для устройств, которые помогают сделать смешанную реальность более доступной.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-217">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="2ddf5-218">Адаптивный контроллер Xbox выполняет нажатие кнопки как Вторичный вход, используя кнопку "A".</span><span class="sxs-lookup"><span data-stu-id="2ddf5-218">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="2ddf5-219">Устройство сопоставляется с набором действий по умолчанию, которые помогают перемещаться по системе и управлять ей.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-219">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="2ddf5-220">Если вы хотите настроить контроллер, используйте приложение Xbox для настройки адаптивного контроллера Xbox.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-220">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="2ddf5-221">![Адаптивный контроллер Xbox](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="2ddf5-222">*Адаптивный контроллер Xbox*</span><span class="sxs-lookup"><span data-stu-id="2ddf5-222">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="2ddf5-223">Подключите внешние устройства, такие как коммутаторы, кнопки, подключения и джойстики, чтобы создать пользовательский интерфейс контроллера, который является уникальным.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-223">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="2ddf5-224">Входные данные кнопки, аналогового стика и триггера контролируются с помощью вспомогательных устройств, подключенных через разъемы 3,5 мм и порты USB.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-224">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5mm jacks and USB ports.</span></span>

<span data-ttu-id="2ddf5-225">![Порты адаптивного контроллера Xbox](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="2ddf5-225">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="2ddf5-226">*Порты адаптивного контроллера Xbox*</span><span class="sxs-lookup"><span data-stu-id="2ddf5-226">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="2ddf5-227">Инструкции по связыванию устройства</span><span class="sxs-lookup"><span data-stu-id="2ddf5-227">Instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="2ddf5-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Дополнительные сведения доступны на сайте Xbox</a></span><span class="sxs-lookup"><span data-stu-id="2ddf5-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="2ddf5-229">Составные жесты</span><span class="sxs-lookup"><span data-stu-id="2ddf5-229">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="2ddf5-230">Жест касания</span><span class="sxs-lookup"><span data-stu-id="2ddf5-230">Air tap</span></span>
<span data-ttu-id="2ddf5-231">Жест касания воздуха (а также другие жесты ниже) реагирует только на определенное касание.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-231">The air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="2ddf5-232">Для обнаружения других касаний, таких как меню или распознавать, приложение должно напрямую использовать взаимодействия нижнего уровня, описанные в разделе «жесты двух ключевых компонентов» выше.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-232">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="2ddf5-233">Коснуться и удерживать</span><span class="sxs-lookup"><span data-stu-id="2ddf5-233">Tap and hold</span></span>
<span data-ttu-id="2ddf5-234">Удерживание — это просто удержание пальца в опущенном положении после касания.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-234">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="2ddf5-235">Сочетание воздушного касания и удержания позволяет использовать множество более сложных взаимодействий "щелчок и перетаскивание" при сочетании с движением ARM, например выборка объекта вместо активации или MouseDown вторичных взаимодействий, таких как отображение контекстного меню.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-235">The combination of air tap and hold allows for a variety of more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="2ddf5-236">Однако при разработке этого жеста следует соблюдать осторожность, поскольку пользователи могут быть склонны к расслаблению позы рук во время любого расширенного жеста.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-236">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="2ddf5-237">Манипуляции</span><span class="sxs-lookup"><span data-stu-id="2ddf5-237">Manipulation</span></span>
<span data-ttu-id="2ddf5-238">Жесты манипуляции можно использовать для перемещения, изменения размера или поворота голограммы, когда нужно, чтобы голограмма реагировала на 1:1 в руки пользователя.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-238">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="2ddf5-239">Одно из применений таких движений 1:1 позволяет пользователю только рисовать или вписывать красками.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-239">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="2ddf5-240">Первоначальное нацеливание для жеста управления должно быть исполнено взглядом или указанием.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-240">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="2ddf5-241">После того как касание и удержание начинается, любая манипуляция объекта обрабатывается перемещениями вручную, освобождая пользователя на то время, когда они манипулируют.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-241">Once the tap and hold starts, any manipulation of the object is handled by hand movements, freeing the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="2ddf5-242">Навигация</span><span class="sxs-lookup"><span data-stu-id="2ddf5-242">Navigation</span></span>
<span data-ttu-id="2ddf5-243">Жесты навигации работают как виртуальный джойстик и могут использоваться для навигации по мини-приложениям пользовательского интерфейса, таким как радиальные меню.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-243">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="2ddf5-244">Вы касаетесь и удерживаете, чтобы начать жест, а затем двигаете рукой в нормализованном трехмерном кубе, центрированном вокруг начального нажатия.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-244">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="2ddf5-245">Вы можете перемещать руку вдоль оси X, Y или Z от значения –1 до 1, где 0 является начальной точкой.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-245">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="2ddf5-246">Навигация может использоваться для создания жестов непрерывной прокрутки или масштабирования на основе скорости, аналогично прокрутке 2D-интерфейса путем нажатия средней кнопки мыши и последующего перемещения мыши вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-246">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="2ddf5-247">Переход с границами означает возможность распознавания движений на определенной оси до тех пор, пока на этой оси не будет достигнуто определенное пороговое значение.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-247">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="2ddf5-248">Это полезно только в том случае, если в приложении разработчику разрешено перемещение нескольких осей, например, если приложение настроено на распознавание жестов навигации по оси X, Y, но также задается по оси X с границами.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-248">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="2ddf5-249">В этом случае система распознает перемещения руки по оси X, пока они остаются в мнимых шинах (направляющие) на оси X, если движение руки также выполняется на оси Y.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-249">In this case the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="2ddf5-250">В 2D-приложениях пользователи могут использовать жесты вертикальной навигации для прокрутки, масштабирования или перетаскивания внутри приложения.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-250">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="2ddf5-251">Это вводит в приложение виртуальные касания пальцем, чтобы имитировать сенсорные жесты того же типа.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-251">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="2ddf5-252">Пользователи могут выбирать, какие из этих действий выполняются, переключаясь между инструментами на панели над приложением, нажимая кнопку или произнося «< Scroll/rezoom > Tool».</span><span class="sxs-lookup"><span data-stu-id="2ddf5-252">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="2ddf5-253">Дополнительные сведения о составных жестах</span><span class="sxs-lookup"><span data-stu-id="2ddf5-253">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="2ddf5-254">Распознаватели жестов</span><span class="sxs-lookup"><span data-stu-id="2ddf5-254">Gesture recognizers</span></span>

<span data-ttu-id="2ddf5-255">Одно из преимуществ использования распознавания жестов заключается в том, что вы можете настроить распознаватель жестов только для жестов, которые может принимать текущая Целевая голограмма.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-255">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="2ddf5-256">Платформа делает только неоднозначность по мере необходимости для различения определенных поддерживаемых жестов.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-256">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="2ddf5-257">Таким образом, голограмма, которая просто поддерживает воздушный нажим, может принимать любое время между нажатием и выпуском, а голограмма, поддерживающая нажатие и удержание, может повысить уровень касания до удержания после порогового значения времени удержания.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-257">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="2ddf5-258">Распознавание рук</span><span class="sxs-lookup"><span data-stu-id="2ddf5-258">Hand recognition</span></span>
<span data-ttu-id="2ddf5-259">HoloLens распознает жесты рук, отслеживая положение одной или обеих рук, которые видимые устройству.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-259">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="2ddf5-260">Руки видны для HoloLens, когда они находятся в состоянии готовности (задняя часть руки обращена к вам указательным пальцем вверх) или в нажатом состоянии (задняя часть руки обращена к вам указательным пальцем вниз).</span><span class="sxs-lookup"><span data-stu-id="2ddf5-260">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="2ddf5-261">Когда руки находятся в других случаях, HoloLens игнорирует их.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-261">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="2ddf5-262">Для каждой руки, которую обнаруживает HoloLens, можно получить доступ к его положению без ориентации и нажатого состояния.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-262">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="2ddf5-263">Когда рука приближается к краю рамки жеста, вам также предоставляется вектор направления, который вы можете показать пользователю. Так он узнает, как переместить руку, чтобы вернуть ее туда, где она будет видна для HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-263">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="2ddf5-264">Рамка жестов</span><span class="sxs-lookup"><span data-stu-id="2ddf5-264">Gesture frame</span></span>
<span data-ttu-id="2ddf5-265">Для жестов в HoloLens необходимо находиться в пределах рамки жеста, в диапазоне, в котором камеры с сенсорным входом могут видеть соответствующим образом, от нос до уши и между плечи.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-265">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="2ddf5-266">Пользователи должны быть обучены в этой области распознавания как для успеха, так и для собственной работы.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-266">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="2ddf5-267">Многие пользователи изначально предполагают, что рамка жеста должна находиться в пределах своего представления через HoloLens и держать свои руки некомфортными для взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-267">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact.</span></span> <span data-ttu-id="2ddf5-268">При использовании щелчка HoloLens необязательно, чтобы руки находящихся внутри рамки жеста.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-268">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="2ddf5-269">В частности, в случае с непрерывными жестами пользователь может переместить свои руки за пределы рамки жеста при перемещении holographic-объекта, например, и потерять предполагаемый результат.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-269">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="2ddf5-270">Есть три вещи, которые необходимо рассмотреть:</span><span class="sxs-lookup"><span data-stu-id="2ddf5-270">There are three things that you should consider:</span></span>

- <span data-ttu-id="2ddf5-271">Обучение пользователей на существовании и приблизительных границах рамки жеста.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-271">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="2ddf5-272">Это научилось во время установки HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-272">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="2ddf5-273">Уведомление пользователей о том, что их жесты близки или нарушают границы кадра жестов в пределах приложения до степени, в которой потерянный жест ведет к нежелательным результатам.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-273">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="2ddf5-274">Исследование показало Ключевые качества такой системы уведомлений.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-274">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="2ddf5-275">Оболочка HoloLens предоставляет хороший пример такого типа уведомления — визуальный элемент, расположенный в центральном курсоре, указывающий направление пересечения границ.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-275">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="2ddf5-276">Последствия нарушения границ рамки жеста должны быть сведены к минимуму.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-276">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="2ddf5-277">В общем случае это означает, что результат жеста должен быть остановлен на границе, а не на противоположный.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-277">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="2ddf5-278">Например, если пользователь перемещает несколько holographic объектов в комнате, перемещение должно прерываться при нарушении рамки жеста и не возвращаться к начальной точке.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-278">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="2ddf5-279">Пользователь может столкнуться с неудовлетворенностью, но может более быстро понять границы и не должен каждый раз перезапускать все запланированные действия.</span><span class="sxs-lookup"><span data-stu-id="2ddf5-279">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="2ddf5-280">См. также:</span><span class="sxs-lookup"><span data-stu-id="2ddf5-280">See also</span></span>
* [<span data-ttu-id="2ddf5-281">Взаимодействие на основе глаз</span><span class="sxs-lookup"><span data-stu-id="2ddf5-281">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="2ddf5-282">Отслеживание глаз в HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2ddf5-282">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="2ddf5-283">Взгляд и остановка</span><span class="sxs-lookup"><span data-stu-id="2ddf5-283">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="2ddf5-284">Руки: непосредственное манипулирование</span><span class="sxs-lookup"><span data-stu-id="2ddf5-284">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2ddf5-285">Руки: жесты</span><span class="sxs-lookup"><span data-stu-id="2ddf5-285">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="2ddf5-286">Руки: наведение и фиксация</span><span class="sxs-lookup"><span data-stu-id="2ddf5-286">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="2ddf5-287">Инстинктивное взаимодействие</span><span class="sxs-lookup"><span data-stu-id="2ddf5-287">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="2ddf5-288">Голосовой ввод</span><span class="sxs-lookup"><span data-stu-id="2ddf5-288">Voice input</span></span>](voice-input.md)

