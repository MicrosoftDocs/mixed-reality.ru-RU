---
title: Взглядом и простоя
description: Общие сведения о модели ввода взглядом и простоя
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: Смешанной реальности, взглядом, простоя, взаимодействие, проектирование
ms.openlocfilehash: a50ae948a351f5152ebb98778da9be8c08090d72
ms.sourcegitcommit: 222cba2d622b47f75949bf8af80d5c62de4dceab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/30/2019
ms.locfileid: "64914609"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="0fa8d-104">Взглядом и простоя</span><span class="sxs-lookup"><span data-stu-id="0fa8d-104">Gaze and dwell</span></span>

<span data-ttu-id="0fa8d-105">Когда с помощью средств и частей будут заняты руки, жесты может быть утомительным или невозможным.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>  <span data-ttu-id="0fa8d-106">Голосовые команды, такие как жест, может быть situationally ненадежно, например в условиях слишком громкий.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-106">Voice commands, like gesture, can be situationally unreliable, for example under excessively loud conditions.</span></span>  <span data-ttu-id="0fa8d-107">Кроме того с помощью голоса для управления компьютерами не еще Основная фаза взаимодействия, но оно определенно Получает поток данных!</span><span class="sxs-lookup"><span data-stu-id="0fa8d-107">Additionally, using voice to control computers isn't a mainstream interaction yet, but it certainly is gaining steam!</span></span>  <span data-ttu-id="0fa8d-108">Простой взглядом предлагает наиболее знакомо и легко master механизм работы информационных индикаторов, без участия пользователя на HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-108">Gaze dwell offers the most familiar and easy-to-master mechanism for working heads-up hands-free on HoloLens.</span></span>  <span data-ttu-id="0fa8d-109">Кроме того, простоя взглядом является полностью надежные независимо от ограничения помех, ни бездействия шума в производственной среде.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-109">Additionally, gaze dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="goals"></a><span data-ttu-id="0fa8d-110">Цели</span><span class="sxs-lookup"><span data-stu-id="0fa8d-110">Goals</span></span>

<span data-ttu-id="0fa8d-111">Предоставляет механизм для взаимодействия с полной без участия пользователя, без использования голоса.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-111">Provide a mechanism for full hands-free interactions, without using Voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="0fa8d-112">Принципы проектирования</span><span class="sxs-lookup"><span data-stu-id="0fa8d-112">Design principles</span></span>

1. <span data-ttu-id="0fa8d-113">Взглядом не оружие</span><span class="sxs-lookup"><span data-stu-id="0fa8d-113">Gaze is not a weapon</span></span>
    
    <span data-ttu-id="0fa8d-114">Взглядом требует визуальную обратную связь для взаимодействия с интуитивно понятным, но слишком много отзывов можно вызвать беспокойство перед поездкой.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-114">Gaze requires visual feedback for intuitive interaction, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="0fa8d-115">Отзыв должен помочь пользователю знать, что они целевой платформой является, но не автоматический выбор от их назначение.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-115">The feedback should help a user know what they're targeting, but not auto-select against their intent.</span></span> <span data-ttu-id="0fa8d-116">Чтение текста требует дополнительных соображений для предоставления комнаты самым защищая данные перед выбором пользователя.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-116">Reading text requires extra consideration to provide a user room to absorb the info before selecting.</span></span>
    
2. <span data-ttu-id="0fa8d-117">Эта скорость поиска</span><span class="sxs-lookup"><span data-stu-id="0fa8d-117">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="0fa8d-118">Простой заливки могут иметь разные таймеры, в зависимости от влияния навигации — наиболее часто используемых функций будет обычно получают ряд преимуществ сократить время заполнения, хотя более косвенные функции могут получить преимущества от более длительное время заполнения.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-118">The dwell fill can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="0fa8d-119">Кривые анимации цвета заливки можно положительным образом скажется на чувство сократить время заполнения.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-119">Animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="0fa8d-120">Внимание следует принимать для включения пользователя решением, принятым fast: средняя/низкая переопределения скорость заполнения.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-120">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="0fa8d-121">Скажем no-no yo-yo эффекта</span><span class="sxs-lookup"><span data-stu-id="0fa8d-121">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="0fa8d-122">Эффект yo-yo (также называется «ночь в Roxbury») — это вызвать беспокойство в шаблон, который могут возникать из определенного расположения содержимого, а также элементы управления на основе взглядом.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-122">The yo-yo effect (also known as "Night at the Roxbury") is an uncomfortable pattern that can emerge from certain  placement of content and gaze-based controls.</span></span> <span data-ttu-id="0fa8d-123">Например nav списка с помощью заливки, расположенную в нижней вызывает цикл - вид вниз вдаваясь, просмотрите результаты, можно попытаться простоя и т. д. Этот результирующий шаблон доставляет неудобства и его следует избегать, разместив элементы управления для переходов в централизованное расположение, которое требует меньше туда и обратно.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-123">For example, a list nav with the fill button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="0fa8d-124">Размещение кнопки простоя по отношению к их воздействие становится важным для комфорта.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-124">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="0fa8d-125">Шаблоны пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="0fa8d-125">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="0fa8d-126">Высокая частота кнопок</span><span class="sxs-lookup"><span data-stu-id="0fa8d-126">High frequency buttons</span></span>
    
* <span data-ttu-id="0fa8d-127">Кнопок «Далее или назад»</span><span class="sxs-lookup"><span data-stu-id="0fa8d-127">Next/Back buttons</span></span>
  * <span data-ttu-id="0fa8d-128">Очень небольшая задержка до заполнения (всплывающие мерцание буфер)</span><span class="sxs-lookup"><span data-stu-id="0fa8d-128">Very short delay pre-fill (flyover flicker buffer)</span></span>
  * <span data-ttu-id="0fa8d-129">Чтобы упростить нажатие с взглядом большего размера кнопок</span><span class="sxs-lookup"><span data-stu-id="0fa8d-129">Larger buttons are easier to hit with gaze</span></span>
  * <span data-ttu-id="0fa8d-130">Желательно сохранить их в глаза высота нагрузку, поэтому для взаимодействия</span><span class="sxs-lookup"><span data-stu-id="0fa8d-130">Nice to keep these at eye height so no strain to interact</span></span>
  * <span data-ttu-id="0fa8d-131">Область простоя можно больше, чем неактивные значок, чтобы было проще использовать (назад)</span><span class="sxs-lookup"><span data-stu-id="0fa8d-131">Dwell region can be larger than inactive icon to make it easier to use (BACK)</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="0fa8d-132">Низкая частота кнопок</span><span class="sxs-lookup"><span data-stu-id="0fa8d-132">Low frequency buttons</span></span>
    
* <span data-ttu-id="0fa8d-133">Активация меню "Параметры"</span><span class="sxs-lookup"><span data-stu-id="0fa8d-133">Activate settings menu</span></span>
  * <span data-ttu-id="0fa8d-134">Больше задержка хорошо предварительного заполнения (всплывающие мерцание буфер)</span><span class="sxs-lookup"><span data-stu-id="0fa8d-134">Longer delay pre-fill okay (flyover flicker buffer)</span></span>
  * <span data-ttu-id="0fa8d-135">Стараются поддерживать эти кнопки мешало каналы часто курсора</span><span class="sxs-lookup"><span data-stu-id="0fa8d-135">Try to keep these buttons out of the way of frequent cursor pathways</span></span>

* <span data-ttu-id="0fa8d-136">Подтверждений (т. е. Просмотр потока, диалоговые окна)</span><span class="sxs-lookup"><span data-stu-id="0fa8d-136">Confirmations (i.e. scan flow, dialogs)</span></span>
  * <span data-ttu-id="0fa8d-137">Показать выделение выбора на главной кнопки</span><span class="sxs-lookup"><span data-stu-id="0fa8d-137">Show selection highlight on main button</span></span>
  * <span data-ttu-id="0fa8d-138">Показать целевой простоя одновременно выделение выбора</span><span class="sxs-lookup"><span data-stu-id="0fa8d-138">Reveal dwell target at same time as selection highlight</span></span>
  * <span data-ttu-id="0fa8d-139">Используйте вдаваясь целевой окружающего значок, чтобы не усложнять интерфейса</span><span class="sxs-lookup"><span data-stu-id="0fa8d-139">Use dwell target surrounding icon to keep interface simple</span></span>
  * <span data-ttu-id="0fa8d-140">Важное решение, чтобы не активировать выделения, показывает простой целевой объект для повторного рассмотрения своей судьбы времени</span><span class="sxs-lookup"><span data-stu-id="0fa8d-140">Important decision, so highlight doesn't activate, reveals dwell target for reconsideration time</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="0fa8d-141">Переключателей</span><span class="sxs-lookup"><span data-stu-id="0fa8d-141">Toggle buttons</span></span>

* <span data-ttu-id="0fa8d-142">Pin</span><span class="sxs-lookup"><span data-stu-id="0fa8d-142">Pin</span></span>
  * <span data-ttu-id="0fa8d-143">Очистите активных и неактивных визуальное состояние</span><span class="sxs-lookup"><span data-stu-id="0fa8d-143">Clear active/inactive visual state</span></span>
  * <span data-ttu-id="0fa8d-144">Радиальный заливки помогает фокус пользователя и предоставляет естественный ход выполнения</span><span class="sxs-lookup"><span data-stu-id="0fa8d-144">Radial fill helps focus user and provides natural progress</span></span> 

* <span data-ttu-id="0fa8d-145">Отдельные параметры</span><span class="sxs-lookup"><span data-stu-id="0fa8d-145">Individual settings</span></span>
  * <span data-ttu-id="0fa8d-146">Очистите активных и неактивных состояний</span><span class="sxs-lookup"><span data-stu-id="0fa8d-146">Clear active/inactive states</span></span>
  * <span data-ttu-id="0fa8d-147">Буду распространяться целевые объекты на левой окружающей значок</span><span class="sxs-lookup"><span data-stu-id="0fa8d-147">Dwell targets all on left surrounding icon</span></span>
  * <span data-ttu-id="0fa8d-148">Простой предназначен только отображаются при выделении активный</span><span class="sxs-lookup"><span data-stu-id="0fa8d-148">Dwell targets only show up when selection highlight active</span></span>
  * <span data-ttu-id="0fa8d-149">«Подолгу занимаются такими ползунок» в правом углу для параметров on/off</span><span class="sxs-lookup"><span data-stu-id="0fa8d-149">"Dwell on slider" on right side for on/off settings</span></span>

### <a name="list-views"></a><span data-ttu-id="0fa8d-150">Представления списка</span><span class="sxs-lookup"><span data-stu-id="0fa8d-150">List views</span></span>

* <span data-ttu-id="0fa8d-151">Просмотр списка Просмотр - файлов, чтобы открыть руководство</span><span class="sxs-lookup"><span data-stu-id="0fa8d-151">Browsing list view - guide files to open</span></span>
  * <span data-ttu-id="0fa8d-152">Основные особенности курсор в любом месте строки из в строке, но не начинается простоя</span><span class="sxs-lookup"><span data-stu-id="0fa8d-152">Cursor highlights row from anywhere on row but doesn’t begin dwell</span></span>
  * <span data-ttu-id="0fa8d-153">При выделении строк курсора, целевой простоя отображается слева</span><span class="sxs-lookup"><span data-stu-id="0fa8d-153">When row is highlighted by cursor, dwell target appears on left</span></span>
  * <span data-ttu-id="0fa8d-154">Буду распространяться целевой всегда круг слева от текста в всех представлений списков</span><span class="sxs-lookup"><span data-stu-id="0fa8d-154">Dwell target always a circle on left side of text in all list views</span></span>
  * <span data-ttu-id="0fa8d-155">Больше не показывать, что все вдаваясь целевых объектов за один раз, чтобы избежать повторяющихся пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="0fa8d-155">Don't show all dwell targets at once to avoid repetitive UI</span></span>
  * <span data-ttu-id="0fa8d-156">Повторно использовать один и тот же шаблон для установления UX Знакомство</span><span class="sxs-lookup"><span data-stu-id="0fa8d-156">Re-use the same pattern to establish UX familiarity</span></span>
        
* <span data-ttu-id="0fa8d-157">Просмотр представления списка - задачи и подзадачи в структуре иерархии</span><span class="sxs-lookup"><span data-stu-id="0fa8d-157">Browsing list view - hierarchy of tasks/steps in a guide</span></span>
  * <span data-ttu-id="0fa8d-158">Буду распространяться целевой всегда круг слева от текста</span><span class="sxs-lookup"><span data-stu-id="0fa8d-158">Dwell target always a circle on left side of text</span></span>
  * <span data-ttu-id="0fa8d-159">Развертывание или свертывание affordance простоя</span><span class="sxs-lookup"><span data-stu-id="0fa8d-159">Collapse/expand dwell affordance</span></span>
        
* <span data-ttu-id="0fa8d-160">Представление для просмотра списка - Выбор режима</span><span class="sxs-lookup"><span data-stu-id="0fa8d-160">Browsing list view - mode select</span></span>
  * <span data-ttu-id="0fa8d-161">Следовать шаблонам, установить выше</span><span class="sxs-lookup"><span data-stu-id="0fa8d-161">Follow patterns established above</span></span>

### <a name="contextual-buttons"></a><span data-ttu-id="0fa8d-162">Контекстные кнопок</span><span class="sxs-lookup"><span data-stu-id="0fa8d-162">Contextual buttons</span></span>

* <span data-ttu-id="0fa8d-163">Показать/скрыть 3D - показано вверх в трехмерном пространстве вдоль крепления практически голограммы</span><span class="sxs-lookup"><span data-stu-id="0fa8d-163">Show/Hide 3D - shows up in 3D along tether near holograms</span></span> 
  * <span data-ttu-id="0fa8d-164">Очистите активных и неактивных визуальное состояние</span><span class="sxs-lookup"><span data-stu-id="0fa8d-164">Clear active/inactive visual state</span></span>

### <a name="pivots"></a><span data-ttu-id="0fa8d-165">Сводки</span><span class="sxs-lookup"><span data-stu-id="0fa8d-165">Pivots</span></span>

* <span data-ttu-id="0fa8d-166">Список руководств последние/All</span><span class="sxs-lookup"><span data-stu-id="0fa8d-166">Recent/All guides list</span></span>
  * <span data-ttu-id="0fa8d-167">Заливка affordance пользовательского интерфейса, который остается, чтобы указать, какие вкладки активен</span><span class="sxs-lookup"><span data-stu-id="0fa8d-167">Fill the UI affordance that remains to indicate which tab is active</span></span>
  * <span data-ttu-id="0fa8d-168">Для преобразования короткого одно слово мы выбрали без простоя шаблону целевого объекта</span><span class="sxs-lookup"><span data-stu-id="0fa8d-168">For short single word pivots, we elected to forego the dwell target pattern</span></span>
  * <span data-ttu-id="0fa8d-169">Мы нетразакционным упрощенный интерфейс другой 2 круг целевых объектов и шире пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="0fa8d-169">We favored the simplified interface over another 2 circle targets and a wider UI</span></span>
  * <span data-ttu-id="0fa8d-170">В нашем случае слова, достаточно короткий, что задержка может обеспечить достаточно комфорта до заполнения</span><span class="sxs-lookup"><span data-stu-id="0fa8d-170">In our case, the words are short enough that a delay provides enough comfort before filling</span></span>


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="0fa8d-171">UX правила и рекомендации</span><span class="sxs-lookup"><span data-stu-id="0fa8d-171">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="0fa8d-172">Размеры цели</span><span class="sxs-lookup"><span data-stu-id="0fa8d-172">Target sizes</span></span>

  * <span data-ttu-id="0fa8d-173">Минимальный размер значка ПИН-код: 6cm в абсолютном пространстве в Unity, 30 единиц (30cm @ 2 МБ)</span><span class="sxs-lookup"><span data-stu-id="0fa8d-173">Pin icon minimum size: 6cm in world space in Unity, 30 MRUs ( 30cm @ 2m)</span></span>
  * <span data-ttu-id="0fa8d-174">Вообще-целевые объекты «намагничены» или «прикрепленные»?</span><span class="sxs-lookup"><span data-stu-id="0fa8d-174">Are the targets "magnetized" or "sticky" at all?</span></span> <span data-ttu-id="0fa8d-175">(т. е. помощи сглаживания курсора)</span><span class="sxs-lookup"><span data-stu-id="0fa8d-175">(i.e. gaze cursor smoothing)</span></span>

### <a name="animation"></a><span data-ttu-id="0fa8d-176">Анимация</span><span class="sxs-lookup"><span data-stu-id="0fa8d-176">Animation</span></span>

  * <span data-ttu-id="0fa8d-177">Задержка перед .5sec visual триггеры простоя</span><span class="sxs-lookup"><span data-stu-id="0fa8d-177">Delay before dwell visual triggers .5sec</span></span>
  * <span data-ttu-id="0fa8d-178">Продолжительность простоя visual 1,2 сек</span><span class="sxs-lookup"><span data-stu-id="0fa8d-178">Duration of dwell visual 1.2sec</span></span>
  * <span data-ttu-id="0fa8d-179">Кривой на анимации?</span><span class="sxs-lookup"><span data-stu-id="0fa8d-179">Curve on animation?</span></span>

### <a name="visual-feedback"></a><span data-ttu-id="0fa8d-180">Визуальная обратная связь</span><span class="sxs-lookup"><span data-stu-id="0fa8d-180">Visual feedback</span></span>

  * <span data-ttu-id="0fa8d-181">Радиальный заливки из взглядом курсора начальное расположение</span><span class="sxs-lookup"><span data-stu-id="0fa8d-181">Radial fill from gaze cursor start location</span></span>
  * <span data-ttu-id="0fa8d-182">Всегда радиальной заливки из центра кнопки.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-182">Always radial fill from center of button.</span></span> <span data-ttu-id="0fa8d-183">Согласованное ответ проще, чем все разных направлениях на разные кнопки.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-183">A consistent response is less confusing than all different directions on different buttons.</span></span> 
    * <span data-ttu-id="0fa8d-184">Это правило можно разбить на то, что и для направления взаимодействия (например, панель навигации вверх/вниз/вправо и влево, т. д.).</span><span class="sxs-lookup"><span data-stu-id="0fa8d-184">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="0fa8d-185">Например направляющие делает исключение на согласившись Далее и назад по правой кнопкой мыши заливки.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-185">For example, Guides makes an exception on NEXT/BACK being left right fills.</span></span>
    * <span data-ttu-id="0fa8d-186">Рассмотрим обращение радиальной заливки из за пределами (если переключением отключение).</span><span class="sxs-lookup"><span data-stu-id="0fa8d-186">Consider inverting radial fill from outside (if toggling off).</span></span> <span data-ttu-id="0fa8d-187">Обратный чувство нажать кнопку — это хороший шаблон visual для поддержания.</span><span class="sxs-lookup"><span data-stu-id="0fa8d-187">THe inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="0fa8d-188">Возможность постепенного развертывания</span><span class="sxs-lookup"><span data-stu-id="0fa8d-188">Progressive Disclosure</span></span>

 * <span data-ttu-id="0fa8d-189">Возможность постепенного развертывания означает, что целевой объект простоя будет раскрыт на выделение (например, в элементе управления списком)</span><span class="sxs-lookup"><span data-stu-id="0fa8d-189">Progressive disclosure means that the dwell target is revealed on highlight (e.g., in a list control)</span></span>
 * <span data-ttu-id="0fa8d-190">Показать текст панели светлых spotlight на взглядом в любом месте текста</span><span class="sxs-lookup"><span data-stu-id="0fa8d-190">Text bar highlights with spotlight reveal on gaze anywhere on text</span></span>
 * <span data-ttu-id="0fa8d-191">Целевой заливки взглядом всегда отображается слева, но только для элемента списка, который будет выделен</span><span class="sxs-lookup"><span data-stu-id="0fa8d-191">Gaze fill target appears always on left, but only for the list item which is highlighted</span></span>
 * <span data-ttu-id="0fa8d-192">Размещайте все целевые объекты простоя на в любое время из-за повторяющихся внешний вид кругов с накоплением</span><span class="sxs-lookup"><span data-stu-id="0fa8d-192">Try to avoid having all dwell targets on at all times due to repetitive look of stacked circles</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="0fa8d-193">См. также</span><span class="sxs-lookup"><span data-stu-id="0fa8d-193">See also</span></span>
* [<span data-ttu-id="0fa8d-194">Прямые манипуляции</span><span class="sxs-lookup"><span data-stu-id="0fa8d-194">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0fa8d-195">Точки и фиксации</span><span class="sxs-lookup"><span data-stu-id="0fa8d-195">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="0fa8d-196">Основы взаимодействия</span><span class="sxs-lookup"><span data-stu-id="0fa8d-196">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="0fa8d-197">HEAD взглядом и фиксации</span><span class="sxs-lookup"><span data-stu-id="0fa8d-197">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0fa8d-198">Взглядом и речи</span><span class="sxs-lookup"><span data-stu-id="0fa8d-198">Gaze and voice</span></span>](voice-design.md)
