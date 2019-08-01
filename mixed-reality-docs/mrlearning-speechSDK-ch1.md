---
title: Учебники по службам речи Azure — 1. Интеграция и использование распознавания речи и транскрипции
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 501e8bc2e70248a4ca8a79f90d74d30129830701
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701961"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="d0bc3-105">1. Интеграция и использование распознавания речи и транскрипции</span><span class="sxs-lookup"><span data-stu-id="d0bc3-105">1. Integrating and using speech recognition and transcription</span></span>

<span data-ttu-id="d0bc3-106">В этом руководстве создается приложение смешанной реальности, в котором рассматривается использование пакета Azure Cognitive Services Speech SDK с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-106">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="d0bc3-107">По завершении работы с этой серией руководств вы сможете использовать микрофон устройства для транскрипция речи в текст в режиме реального времени, перевода речи на другие языки и использования функции речевого пакета SDK для понимания голосовых команд с помощью искусственный интеллект.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-107">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="d0bc3-108">Цели</span><span class="sxs-lookup"><span data-stu-id="d0bc3-108">Objectives</span></span>

- <span data-ttu-id="d0bc3-109">Узнайте, как интегрировать пакет SDK для Azure для распознавания речи в приложение HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-109">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="d0bc3-110">Узнайте, как использовать команды Voice</span><span class="sxs-lookup"><span data-stu-id="d0bc3-110">Learn how to use voice commands</span></span>
- <span data-ttu-id="d0bc3-111">Узнайте, как использовать возможности преобразования речи в текст</span><span class="sxs-lookup"><span data-stu-id="d0bc3-111">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="d0bc3-112">Инструкция</span><span class="sxs-lookup"><span data-stu-id="d0bc3-112">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="d0bc3-113">Начало работы</span><span class="sxs-lookup"><span data-stu-id="d0bc3-113">Getting Started</span></span>

1. <span data-ttu-id="d0bc3-114">Запустите Unity и создайте новый проект.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-114">Start Unity, and create a new project.</span></span> <span data-ttu-id="d0bc3-115">Введите имя проекта модуль Learning SDK для распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-115">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="d0bc3-116">Выберите расположение для сохранения проекта.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-116">Choose a location for where to save your project.</span></span> <span data-ttu-id="d0bc3-117">Затем нажмите кнопку Создать проект.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-117">Then click Create Project.</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="d0bc3-119">Примечание. Убедитесь, что для шаблона задано значение 3D, как показано на рисунке выше.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-119">Note: Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="d0bc3-120">Скачайте пакет Unity [набора средств для смешанной реальности](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) и сохраните его в папку на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-120">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package, and save it to a folder on your PC.</span></span> <span data-ttu-id="d0bc3-121">Импортируйте пакет в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-121">Import the package into your Unity project.</span></span> <span data-ttu-id="d0bc3-122">Подробные инструкции о том, как это сделать, см. в разделе [базовый модуль урок 1](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="d0bc3-122">For detailed instructions on how to do this, please see [Base Module Lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="d0bc3-123">Скачайте и импортируйте пакет [SDK для службы распознавания речи](https://aka.ms/csspeech/unitypackage) Azure для пакета ресурсов Unity.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-123">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="d0bc3-124">Импортируйте пакет SDK для распознавания речи, щелкнув элемент "ресурсы", выбрав команду "Импорт пакета", а затем выбрав "пользовательский пакет".</span><span class="sxs-lookup"><span data-stu-id="d0bc3-124">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="d0bc3-125">Найдите пакет SDK для распознавания речи, скачанный ранее, и откройте его, чтобы начать процесс импорта.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-125">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span> 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="d0bc3-128">Во всплывающем окне далее нажмите кнопку Импорт, чтобы начать импорт пакета SDK для распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-128">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="d0bc3-129">Убедитесь, что проверяются все элементы, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-129">Ensure all items are checked as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. <span data-ttu-id="d0bc3-131">Скачайте пакет SDK для модуля распознавания речи, также известный как пакет Лунарком, щелкнув [эту ссылку](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span><span class="sxs-lookup"><span data-stu-id="d0bc3-131">Download the Speech SDK Module asset pack, also know as Lunarcom package by clicking on [this link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span></span> <span data-ttu-id="d0bc3-132">Пакет ресурсов Лунарком — это набор ресурсов и сценариев, разработанных для этой серии занятий, чтобы продемонстрировать практичное использование пакета SDK для распознавания речи Azure.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-132">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="d0bc3-133">Это терминал с голосовым интерфейсом, который в конечном итоге будет взаимодействовать с модулем разработки лунного модуля, разработанным в [руководстве по базовому модулю.](mrlearning-base-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="d0bc3-133">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>

6. <span data-ttu-id="d0bc3-134">Импортируйте пакет ресурсов Лунарком в проект Unity, выполнив аналогичные действия, которые были выполнены для импорта набора средств Mixed Reality Toolkit и Speech SDK.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-134">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="d0bc3-135">Настройте набор средств для смешанной реальности (МРТК).</span><span class="sxs-lookup"><span data-stu-id="d0bc3-135">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="d0bc3-136">Для этого щелкните панель набор средств смешанной реальности в верхней части окна, а затем выберите Добавить в сцену и настроить.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-136">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. <span data-ttu-id="d0bc3-140">В сцене теперь есть несколько новых элементов из МРТК.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-140">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="d0bc3-141">Сохраните сцену под другим именем, щелкнув "файл", "Сохранить как" и указав имя сцены Спичсцене.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-141">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span> 

> <span data-ttu-id="d0bc3-142">Примечание. Если вы нажмете кнопку Воспроизвести в сцене после добавления МРТК в проект и не введете режим воспроизведения, может потребоваться перезапустить Unity.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-142">Note: If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span> 

9. <span data-ttu-id="d0bc3-143">Выбрав объект Микседреалититулкит в иерархии, щелкните Копировать и настроить на панели Инспектор.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-143">With the MixedRealityToolkit object selected in your hierarchy, click Copy and Customize in the Inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="d0bc3-145">Кроме того, на панели инспектора (с объектом Микседреалититулкит, выбранным в иерархии) Отключите систему диагностики, отменив флажок справа от параметра включить систему диагностики.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-145">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. <span data-ttu-id="d0bc3-147">Чтобы включить Voice Commands, выберите только что созданный профиль МРТК для настройки.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-147">To enable voice commands, select the newly created MRTK profile to customize.</span></span> <span data-ttu-id="d0bc3-148">В этом руководстве мы используем команды ввода речи для распознавания речи и транскрипции.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-148">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="d0bc3-149">Позволяет клонировать входной профиль для внесения изменений в речевые параметры.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-149">Lets clone the input profile to make changes to speech settings.</span></span>

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. <span data-ttu-id="d0bc3-152">После клонирования входного профиля перейдите в раздел голосовые команды и выполните клонирование речевых команд.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-152">Once the input profile is cloned, go to speech commands and clone the speech commands.</span></span>

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. <span data-ttu-id="d0bc3-155">Теперь в разделе команды речи перейдите в раздел "Общие параметры" и задайте для параметра "поведение при запуске" значение "запуск вручную".</span><span class="sxs-lookup"><span data-stu-id="d0bc3-155">Now under speech commands, go to "General Settings" and set "Start Behavior" to "Manual Start"</span></span>

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. <span data-ttu-id="d0bc3-157">На панели проект разверните папку Лунарком и перетащите Lunarcom_Base prefab в иерархию.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-157">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. <span data-ttu-id="d0bc3-159">Выберите объект Lunarcom_Base в иерархии и убедитесь, что для параметра положением задано значение x = 0, y = 0, а z = 0, а для вращения задано значение x = 0, y = 0, а z = 0.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-159">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="d0bc3-160">Установите масштаб для чтения x = 0.008, y = 0.008 и z = 0,01.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-160">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="d0bc3-162">Щелкните Добавить компонент, найдите и выберите Лунаркомконтроллер.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-162">Click Add Component, and search for and select LunarcomController.</span></span> <span data-ttu-id="d0bc3-163">Этот сценарий включен в пакет ресурсов Лунарком, который вы импортировали на шаге 6.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-163">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="d0bc3-165">Чтобы подключить приложение к Azure Cognitive Services, необходимо ввести ключ подписки (также известный как ключ API) для службы речи.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-165">To connect our applicaiton to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="d0bc3-166">Чтобы получить бесплатный ключ подписки, выполните инструкции, приведенные [здесь](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) .</span><span class="sxs-lookup"><span data-stu-id="d0bc3-166">Follow the instructions at [here](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="d0bc3-167">После получения ключа подписки введите его в поле ключа API речевой службы компонента Лунаркомконтроллер на панели инспектора, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-167">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

18. <span data-ttu-id="d0bc3-168">Введите регион, который вы выбрали при регистрации ключа подписки в поле региона службы "речь" компонента Лунаркомконтроллер на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-168">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="d0bc3-169">Например, для региона "Западная часть США" в "westus"</span><span class="sxs-lookup"><span data-stu-id="d0bc3-169">For example, for the region "West US" type in "westus"</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="d0bc3-171">В иерархии разверните объект Lunarcom_Base, щелкнув стрелку слева от него.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-171">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="d0bc3-172">Затем сделайте то же самое для своего дочернего объекта «Terminal», как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-172">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="d0bc3-173">Хотя Lunarcom_Base выбран, щелкните и перетащите Лунарком текст из иерархии в выходной текстовый слот в компоненте Лунаркомконтроллер на панели инспектора, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-173">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

21. <span data-ttu-id="d0bc3-174">Сделайте то же самое с объектом терминала в слоте терминала и объектом Light соединения с слотом контроллера источника подключения.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-174">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="d0bc3-176">Щелкните стрелку рядом с разделом Лунарком Buttons сценария Лунаркомконтроллер на панели инспектора и измените размер на 3.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-176">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="d0bc3-177">Нажмите клавишу ВВОД или Return.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-177">Press Enter or Return.</span></span> <span data-ttu-id="d0bc3-178">Это приводит к отображению трех новых полей элементов.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-178">This causes three new Element fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="d0bc3-180">Разверните кнопки Лунарком, щелкнув стрелку рядом с ней в иерархии и используя тот же процесс, что и выше, перетащите микрофон, вспомогательный объект и Rocket объекты gameobject на элементы 0, 1 и 2, соответственно, в компонент Лунаркомконтроллер в Панель инспектора.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-180">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="d0bc3-182">Выберите объект Lunarcom_Base в иерархии.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-182">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="d0bc3-183">Щелкните Добавить компонент на панели инспектора и найдите и выберите Лунаркомвакевордрекогнизер.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-183">Click Add Component in the inspector panel, and search for and select LunarcomWakeWordRecognizer.</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="d0bc3-185">В слоте слова "Пробуждение" введите в поле активировать терминал.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-185">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="d0bc3-186">В области отклонить слово введите отклонить терминал.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-186">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a><span data-ttu-id="d0bc3-188">Разработка приложения для устройства</span><span class="sxs-lookup"><span data-stu-id="d0bc3-188">Build your application to your device</span></span>

1. <span data-ttu-id="d0bc3-189">Снова откройте окно параметры сборки, перейдя в файл > параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-189">Open the build settings window again by going to File>Build Settings.</span></span>

![Занятия 1 Chapter5 шаг 1](images/Lesson1Chapter5Step1.JPG)

2. <span data-ttu-id="d0bc3-191">Убедитесь, что необходимая сцена находится в списке Scenes in Build (Сцены в сборке), нажав кнопку Add Open Scenes (Добавить открытые сцены).</span><span class="sxs-lookup"><span data-stu-id="d0bc3-191">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="d0bc3-192">Нажмите кнопку Build (Сборка), чтобы начать процесс сборки.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-192">Press the Build button to begin the build process.</span></span>

![Занятия 1 Chapter5 шаг 3](images/Lesson1Chapter5Step3.JPG)

4. <span data-ttu-id="d0bc3-194">Создайте папку для приложения и укажите для нее название.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-194">Create and name a new folder for your application.</span></span> <span data-ttu-id="d0bc3-195">На приведенном ниже изображении для хранения приложения была создана папка с именем App.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-195">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="d0bc3-196">Щелкните Select Folder (Выбор папки), чтобы начать создание приложения в новой папке.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-196">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="d0bc3-197">После завершения создания вы можете закрыть окно Build Settings (Параметры сборки) в Unity.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-197">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 

![Занятия 1 Chapter5 шаг 4](images/Lesson1Chapter5Step4.JPG)

> <span data-ttu-id="d0bc3-199">ПРИМЕЧАНИЕ. Если сборка завершилась сбоем, попробуйте выполнить ее заново или перезапустите Unity и повторите попытку.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-199">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="d0bc3-200">Если отображается ошибка типа Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?) (Ошибка: CS0246 = не удалось найти тип или имя пространства имен XX (возможно, отсутствует директива using или ссылка на сборку)), установите [пакет SDK для Windows 10 (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>).</span><span class="sxs-lookup"><span data-stu-id="d0bc3-200">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span>

5. <span data-ttu-id="d0bc3-201">После завершения сборки откройте созданную папку, содержащую файлы только что созданного приложения.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-201">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="d0bc3-202">Дважды щелкните файл решения ". sln", чтобы открыть файл решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-202">Double click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

> <span data-ttu-id="d0bc3-203">Примечание. Обязательно откройте созданную папку (т. е. папку App, если вы следовали соглашениям об именовании из предыдущих шагов), так как за пределами этой папки будет находиться SLN-файл с аналогичным именем. Не путайте его с SLN-файлом, содержащимся в папке сборки.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-203">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Урок 1, раздел 5, шаг 5](images/Lesson1Chapter5Step5.JPG)

> <span data-ttu-id="d0bc3-205">Примечание. Если в Visual Studio появится запрос на установку новых компонентов, проверьте, установлены ли все обязательные компоненты, как описано на [этой странице](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d0bc3-205">Note: If Visual Studio asks you to install new components, please take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

6. <span data-ttu-id="d0bc3-206">Подключите HoloLens 2 к компьютеру с помощью USB-кабеля.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-206">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="d0bc3-207">Хотя в инструкциях этого урока предполагается, что вы будете развертывать тестирование на устройстве HoloLens 2, вы также можете выполнить развертывание на [эмуляторе HoloLens 2](using-the-hololens-emulator.md) или создать [пакет приложения для передачи данных на другое локальное устройство](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="d0bc3-207">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="d0bc3-208">Перед выполнением сборки для устройства включите на нем режим разработчика.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-208">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="d0bc3-209">Если вы впервые используете HoloLens 2, в Visual Studio может появиться запрос на подключение к HoloLens 2 с использованием PIN-кода.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-209">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="d0bc3-210">Выполните [эти инструкции](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio), если вам нужно включить режим разработчика или выполнить соединение с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-210">Please follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="d0bc3-211">Настройте Visual Studio для сборки на устройство HoloLens 2, выбрав конфигурацию "Выпуск" и архитектуру ARM.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-211">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

![Занятия 1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. <span data-ttu-id="d0bc3-213">Последний шаг — это сборка на вашем устройстве. Выберите "Отладка" > "Запуск без отладки".</span><span class="sxs-lookup"><span data-stu-id="d0bc3-213">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="d0bc3-214">Это приведет к немедленному запуску приложения на вашем устройстве после успешной сборки. Однако в Visual Studio сведения об отладке отображаться не будут.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-214">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="d0bc3-215">Это также означает, что вы можете отсоединить USB-кабель во время выполнения приложения на устройстве HoloLens 2, не прерывая его работу.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-215">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="d0bc3-216">Кроме того, вы можете выбрать "Сборка" > "Развернуть решение", чтобы развернуть решение на устройстве без автоматического запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-216">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

![Занятия 1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a><span data-ttu-id="d0bc3-218">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="d0bc3-218">Congratulations</span></span>

<span data-ttu-id="d0bc3-219">Вы настроили распознавание речи в приложении на платформе Azure.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-219">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="d0bc3-220">Запустите приложение, чтобы убедиться, что все функции и функции работают правильно.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-220">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="d0bc3-221">Начните с произнесения слова "Пробуждение", введенного на шаге 22, для активации терминала.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-221">Start with saying the wake word you typed in Step 22, Activate Terminal.</span></span> <span data-ttu-id="d0bc3-222">Нажмите кнопку микрофон, чтобы запустить распознавание речи.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-222">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="d0bc3-223">Начните говорить.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-223">Begin speaking.</span></span> <span data-ttu-id="d0bc3-224">Вы увидите слова расшифрованной в терминале во время диктовки.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-224">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="d0bc3-225">Нажмите кнопку с микрофоном еще раз, чтобы отключить распознавание речи.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-225">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="d0bc3-226">Выскажите «отклонить терминал», чтобы скрыть терминал Лунарком.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-226">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="d0bc3-227">На следующем занятии мы расскажем о том, как динамически переключаться на использование распознавания речи на основе устройств в ситуациях, когда недоступен пакет SDK для перевода в Azure из-за отсутствия подключения к сети HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d0bc3-227">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="d0bc3-228">Следующий учебник: 2. Добавление автономного режима для преобразования речи в текст в локальной среде</span><span class="sxs-lookup"><span data-stu-id="d0bc3-228">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)

