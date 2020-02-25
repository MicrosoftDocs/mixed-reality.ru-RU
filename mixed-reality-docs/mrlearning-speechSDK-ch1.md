---
title: Учебники по службам речи Azure — 1. Интеграция и использование распознавания речи и транскрипции
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 25e5aa05839845620a23c3dba6698ac7b5854d6d
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553980"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="63605-105">1. Интеграция и использование распознавания речи и транскрипции</span><span class="sxs-lookup"><span data-stu-id="63605-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="63605-106">Обзор</span><span class="sxs-lookup"><span data-stu-id="63605-106">Overview</span></span>

<span data-ttu-id="63605-107">В этом руководстве создается приложение смешанной реальности, в котором рассматривается использование пакета Azure Cognitive Services Speech SDK с HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="63605-107">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="63605-108">По завершении этой серии руководств вы сможете использовать микрофон устройства для транскрипция речи в текст в режиме реального времени, перевода речи на другие языки и использования функции речевого пакета SDK для понимания голосовых команд, использующих искусственные команды. аналитики.</span><span class="sxs-lookup"><span data-stu-id="63605-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="63605-109">Задачи</span><span class="sxs-lookup"><span data-stu-id="63605-109">Objectives</span></span>

* <span data-ttu-id="63605-110">Узнайте, как интегрировать пакет SDK для Azure для распознавания речи в приложение HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="63605-110">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
* <span data-ttu-id="63605-111">Узнайте, как использовать команды Voice</span><span class="sxs-lookup"><span data-stu-id="63605-111">Learn how to use voice commands</span></span>
* <span data-ttu-id="63605-112">Узнайте, как использовать возможности преобразования речи в текст</span><span class="sxs-lookup"><span data-stu-id="63605-112">Learn how to use speech-to-text capabilities</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63605-113">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="63605-113">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="63605-114">Если вы еще не выполнили серию [учебников по началу работы](mrlearning-base.md) , рекомендуется сначала выполнить эти учебники.</span><span class="sxs-lookup"><span data-stu-id="63605-114">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="63605-115">Компьютер с Windows 10, настроенный с требуемыми [установленными инструментами](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="63605-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="63605-116">Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.</span><span class="sxs-lookup"><span data-stu-id="63605-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="63605-117">Базовые навыки программирования на C#.</span><span class="sxs-lookup"><span data-stu-id="63605-117">Some basic C# programming ability</span></span>
* <span data-ttu-id="63605-118">Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="63605-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="63605-119">Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="63605-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="63605-120">Это заменяет все требования к версии Unity и рекомендации, указанные выше.</span><span class="sxs-lookup"><span data-stu-id="63605-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="getting-started"></a><span data-ttu-id="63605-121">Начало работы</span><span class="sxs-lookup"><span data-stu-id="63605-121">Getting Started</span></span>

1. <span data-ttu-id="63605-122">Запустите Unity и создайте новый проект.</span><span class="sxs-lookup"><span data-stu-id="63605-122">Start Unity, and create a new project.</span></span> <span data-ttu-id="63605-123">Введите имя проекта модуль Learning SDK для распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="63605-123">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="63605-124">Выберите расположение для сохранения проекта.</span><span class="sxs-lookup"><span data-stu-id="63605-124">Choose a location for where to save your project.</span></span> <span data-ttu-id="63605-125">Нажмите кнопку Создать проект.</span><span class="sxs-lookup"><span data-stu-id="63605-125">Click Create Project.</span></span>

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    ><span data-ttu-id="63605-127">Убедитесь, что для шаблона задано значение 3D, как показано на рисунке выше.</span><span class="sxs-lookup"><span data-stu-id="63605-127">Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="63605-128">Скачайте [пакет 2.3.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) для [набора средств Mixed Reality для различных](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) версий и сохраните его в папку на своем компьютере.</span><span class="sxs-lookup"><span data-stu-id="63605-128">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.3.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) and save it to a folder on your PC.</span></span> <span data-ttu-id="63605-129">Импортируйте пакет в проект Unity.</span><span class="sxs-lookup"><span data-stu-id="63605-129">Import the package into your Unity project.</span></span> <span data-ttu-id="63605-130">Подробные инструкции по выполнению этой задачи см [. в учебнике Приступая к работе. Инициализация проекта и первого приложения](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="63605-130">For detailed instructions on how to do this, see the [Getting started tutorials - Lesson 2. Initializing your project and first application](mrlearning-base-ch1.md).</span></span>

3. <span data-ttu-id="63605-131">Скачайте и импортируйте пакет [SDK для службы распознавания речи](https://aka.ms/csspeech/unitypackage) Azure для пакета ресурсов Unity.</span><span class="sxs-lookup"><span data-stu-id="63605-131">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="63605-132">Импортируйте пакет SDK для распознавания речи, щелкнув элемент "ресурсы", выбрав команду "Импорт пакета", а затем выбрав "пользовательский пакет".</span><span class="sxs-lookup"><span data-stu-id="63605-132">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="63605-133">Найдите пакет SDK для распознавания речи, скачанный ранее, и откройте его, чтобы начать процесс импорта.</span><span class="sxs-lookup"><span data-stu-id="63605-133">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span>

    ![mrlearning-Speech-CH1-1-step3a. png](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-Speech-CH1-1-step3b. png](images/mrlearning-speech-ch1-1-step3b.png)

4. <span data-ttu-id="63605-136">Во всплывающем окне далее нажмите кнопку Импорт, чтобы начать импорт пакета SDK для распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="63605-136">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="63605-137">Убедитесь, что выбраны все элементы, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="63605-137">Ensure all items are checked, as shown in the image below.</span></span>

    ![mrlearning-Speech-CH1-1-step4. png](images/mrlearning-speech-ch1-1-step4.png)

5. <span data-ttu-id="63605-139">Скачайте учебные материалы по:</span><span class="sxs-lookup"><span data-stu-id="63605-139">Download the tutorial assets:</span></span>
    * [<span data-ttu-id="63605-140">МРТК. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.3.0.2. пакет unitypackage</span><span class="sxs-lookup"><span data-stu-id="63605-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * <span data-ttu-id="63605-141">[Спичсдкассетс. пакет unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/Speech_2/SpeechSDKAssets.unitypackage) (версия 1,2)</span><span class="sxs-lookup"><span data-stu-id="63605-141">[SpeechSDKAssets.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/Speech_2/SpeechSDKAssets.unitypackage) (version 1.2)</span></span>

    <span data-ttu-id="63605-142">Пакет ресурсов Спичсдкассетс — это набор ресурсов и сценариев, разработанных для этой серии руководств, для демонстрации практичного использования пакета SDK для распознавания речи Azure.</span><span class="sxs-lookup"><span data-stu-id="63605-142">The SpeechSDKAssets asset package is a collection of assets and scripts developed for this tutorial series to showcase practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="63605-143">Это терминал с голосовыми командами, который в конечном итоге будет взаимодействовать с процессом запуска Rocket, разработанным в [руководствах по началу работы — занятие 7. Создание примера приложения лунного модуля](mrlearning-base-ch6.md).</span><span class="sxs-lookup"><span data-stu-id="63605-143">It is a voice-command terminal that will ultimately interface with the Rocket Launcher assembly experience developed in the [Getting started tutorials - Lesson 7. Creating a Lunar Module sample application](mrlearning-base-ch6.md).</span></span>

6. <span data-ttu-id="63605-144">Импортируйте два пакета активов учебника в проект Unity, выполнив аналогичные действия, которые были выполнены для импорта набора средств Mixed Reality Toolkit и Speech SDK.</span><span class="sxs-lookup"><span data-stu-id="63605-144">Import the two tutorial asset packages into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>

7. <span data-ttu-id="63605-145">Настройте набор средств для смешанной реальности (МРТК).</span><span class="sxs-lookup"><span data-stu-id="63605-145">Configure the Mixed Reality Toolkit (MRTK).</span></span>

    <span data-ttu-id="63605-146">Для этого щелкните панель набор средств смешанной реальности в верхней части окна, а затем выберите Добавить в сцену и настроить.</span><span class="sxs-lookup"><span data-stu-id="63605-146">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

    ![mrlearning-Speech-CH1-1-step7a. png](images/mrlearning-speech-ch1-1-step7a.png)

    <span data-ttu-id="63605-148">Выбрав объект Микседреалититулкит в иерархии сцены, в окне инспектора выберите DefaultHoloLens2ConfigurationProfile, чтобы сделать его активным профилем для набора средств Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="63605-148">With the MixedRealityToolkit object selected in your scene hierarchy, in the Inspector window, select DefaultHoloLens2ConfigurationProfile to make it the Active Profile for the Mixed Reality Toolkit.</span></span>

    ![mrlearning-Speech-CH1-1-step7b. png](images/mrlearning-speech-ch1-1-step7b.png)

8. <span data-ttu-id="63605-150">В сцене теперь есть несколько новых элементов из МРТК.</span><span class="sxs-lookup"><span data-stu-id="63605-150">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="63605-151">Сохраните сцену под другим именем, щелкнув "файл", "Сохранить как" и указав имя сцены Спичсцене.</span><span class="sxs-lookup"><span data-stu-id="63605-151">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="63605-152">Если вы нажмете кнопку Воспроизвести в сцене после добавления МРТК в проект и не введете режим воспроизведения, может потребоваться перезапустить Unity.</span><span class="sxs-lookup"><span data-stu-id="63605-152">If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span>

9. <span data-ttu-id="63605-153">Выбрав объект Микседреалититулкит в иерархии сцены, щелкните Копировать & настроить на панели инспектора, чтобы открыть всплывающее окно профиля клона.</span><span class="sxs-lookup"><span data-stu-id="63605-153">With the MixedRealityToolkit object selected in your scene hierarchy, click Copy & Customize in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="63605-154">В всплывающем окне профиля клона введите подходящее имя для пользовательского профиля, например Custom HoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="63605-154">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2ConfigurationProfile.</span></span> <span data-ttu-id="63605-155">Щелкните клонировать, чтобы создать настраиваемый профиль конфигурации и задать его в качестве активного профиля.</span><span class="sxs-lookup"><span data-stu-id="63605-155">Click Clone to create your custom configuration profile and set it as the active profile.</span></span>

    ![mrlearning-Speech-CH1-1-step9. png](images/mrlearning-speech-ch1-1-step9.png)

10. <span data-ttu-id="63605-157">Кроме того, на панели инспектора (с объектом Микседреалититулкит, выбранным в иерархии) Отключите систему диагностики, отменив флажок справа от параметра включить систему диагностики.</span><span class="sxs-lookup"><span data-stu-id="63605-157">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

    ![mrlearning-Speech-CH1-1-step10. png](images/mrlearning-speech-ch1-1-step10.png)

11. <span data-ttu-id="63605-159">В этом руководстве мы используем команды ввода речи для распознавания речи и транскрипции.</span><span class="sxs-lookup"><span data-stu-id="63605-159">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="63605-160">Попробуем клонировать входной профиль, чтобы внести изменения в параметры речи.</span><span class="sxs-lookup"><span data-stu-id="63605-160">Let's clone the input profile to make changes to speech settings.</span></span>

    <span data-ttu-id="63605-161">Если объект Микседреалититулкит все еще выбран в иерархии сцены, нажмите кнопку малый клон на панели инспектора, чтобы открыть всплывающее окно профиля клона.</span><span class="sxs-lookup"><span data-stu-id="63605-161">With the MixedRealityToolkit object still selected in your scene hierarchy, click the small Clone button in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="63605-162">В всплывающем окне Профиль клона введите подходящее имя для пользовательского профиля, например Custom HoloLens2InputSystemProfile, а затем нажмите кнопку клонировать, чтобы создать пользовательский профиль входной системы и задать его в качестве активного профиля.</span><span class="sxs-lookup"><span data-stu-id="63605-162">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2InputSystemProfile, and then click Clone to create your custom input system profile and set it as the active profile.</span></span>

    ![mrlearning-Speech-CH1-1-step11. png](images/mrlearning-speech-ch1-1-step11.png)

12. <span data-ttu-id="63605-164">После клонирования входного профиля разверните раздел речь и выполните тот же процесс, что и на предыдущем шаге, чтобы клонировать профиль речевых команд.</span><span class="sxs-lookup"><span data-stu-id="63605-164">Once the input profile is cloned, expand the Speech section and follow the same process as in the previous step to clone the speech commands profile.</span></span>

    ![mrlearning-Speech-CH1-1-step12. png](images/mrlearning-speech-ch1-1-step12.png)

13. <span data-ttu-id="63605-166">В разделе речь перейдите к разделу Общие параметры и измените поведение при запуске вручную.</span><span class="sxs-lookup"><span data-stu-id="63605-166">Under the Speech section, go to General Settings and change Start Behavior to Manual Start.</span></span>

    ![mrlearning-Speech-CH1-1-step13. png](images/mrlearning-speech-ch1-1-step13.png)

14. <span data-ttu-id="63605-168">На панели проект разверните папку Лунарком и перетащите Lunarcom_Base prefab в иерархию сцены.</span><span class="sxs-lookup"><span data-stu-id="63605-168">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your scene hierarchy.</span></span>

    ![mrlearning-Speech-CH1-1-step14. png](images/mrlearning-speech-ch1-1-step14.png)

15. <span data-ttu-id="63605-170">Выберите объект Lunarcom_Base в иерархии и убедитесь, что для параметра положением задано значение x = 0, y = 0, а z = 0, а для вращения задано значение x = 0, y = 0, а z = 0.</span><span class="sxs-lookup"><span data-stu-id="63605-170">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="63605-171">Установите масштаб для чтения x = 0.008, y = 0.008 и z = 0,01.</span><span class="sxs-lookup"><span data-stu-id="63605-171">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="63605-173">Щелкните Добавить компонент, найдите и выберите контроллер Лунарком.</span><span class="sxs-lookup"><span data-stu-id="63605-173">Click Add Component, and search for and select Lunarcom Controller.</span></span> <span data-ttu-id="63605-174">Этот сценарий включен в пакет ресурсов Лунарком, который вы импортировали на шаге 6.</span><span class="sxs-lookup"><span data-stu-id="63605-174">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="63605-176">Чтобы подключить приложение к Azure Cognitive Services, необходимо ввести ключ подписки (также известный как ключ API) для службы речи.</span><span class="sxs-lookup"><span data-stu-id="63605-176">To connect our application to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="63605-177">Чтобы получить бесплатный ключ подписки, выполните инструкции, приведенные [здесь](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) .</span><span class="sxs-lookup"><span data-stu-id="63605-177">Follow the instructions at [here](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="63605-178">После получения ключа подписки введите его в поле ключа API речевой службы компонента Лунаркомконтроллер на панели инспектора, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="63605-178">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel, as shown in the image below.</span></span>

18. <span data-ttu-id="63605-179">Введите регион, который вы выбрали при регистрации ключа подписки в поле региона службы "речь" компонента Лунаркомконтроллер на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="63605-179">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="63605-180">Например, для региона "Западная часть США" введите "westus".</span><span class="sxs-lookup"><span data-stu-id="63605-180">For example, for the region West US type in "westus".</span></span>

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="63605-182">В иерархии разверните объект Lunarcom_Base, щелкнув стрелку слева от него.</span><span class="sxs-lookup"><span data-stu-id="63605-182">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="63605-183">Затем сделайте то же самое для своего дочернего объекта «Terminal», как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="63605-183">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="63605-184">Пока Lunarcom_Base выбрано, щелкните и перетащите Лунарком текст из иерархии в выходной текстовый слот в компоненте Лунаркомконтроллер на панели инспектора, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="63605-184">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel, as shown in the image below.</span></span>

21. <span data-ttu-id="63605-185">Сделайте то же самое с объектом терминала в слоте терминала и объектом Light соединения с слотом контроллера источника подключения.</span><span class="sxs-lookup"><span data-stu-id="63605-185">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="63605-187">Щелкните стрелку рядом с разделом Лунарком Buttons сценария Лунаркомконтроллер на панели инспектора и измените размер на 3.</span><span class="sxs-lookup"><span data-stu-id="63605-187">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="63605-188">Нажмите клавишу ВВОД или Return.</span><span class="sxs-lookup"><span data-stu-id="63605-188">Press Enter or Return.</span></span> <span data-ttu-id="63605-189">Это приводит к отображению трех новых полей элементов.</span><span class="sxs-lookup"><span data-stu-id="63605-189">This causes three new Element fields to appear.</span></span>

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="63605-191">Разверните кнопки Лунарком, щелкнув стрелку рядом с ней в иерархии и используя тот же процесс, что и выше, перетащите микрофон, вспомогательный объект и Rocket объекты gameobject на элементы 0, 1 и 2, соответственно, в компонент Лунаркомконтроллер в Панель инспектора.</span><span class="sxs-lookup"><span data-stu-id="63605-191">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="63605-193">Выберите объект Lunarcom_Base "в иерархии.</span><span class="sxs-lookup"><span data-stu-id="63605-193">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="63605-194">Щелкните Добавить компонент на панели инспектора и найдите и выберите Лунарком распознавания речи.</span><span class="sxs-lookup"><span data-stu-id="63605-194">Click Add Component in the inspector panel and search for and select Lunarcom Speech Recognizer.</span></span> <span data-ttu-id="63605-195">Повторите те же действия, чтобы добавить распознаватель слов Лунарком Wake.</span><span class="sxs-lookup"><span data-stu-id="63605-195">Repeat the same steps to add Lunarcom Wake Word Recognizer.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="63605-197">В слоте слова "Пробуждение" введите в поле активировать терминал.</span><span class="sxs-lookup"><span data-stu-id="63605-197">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="63605-198">В области отклонить слово введите отклонить терминал.</span><span class="sxs-lookup"><span data-stu-id="63605-198">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="63605-200">Разработка приложения для устройства</span><span class="sxs-lookup"><span data-stu-id="63605-200">Build your application to your device</span></span>

1. <span data-ttu-id="63605-201">Снова откройте окно параметры сборки, перейдя в файл > параметры сборки.</span><span class="sxs-lookup"><span data-stu-id="63605-201">Open the build settings window again by going to File>Build Settings.</span></span>

    ![Images/мрлеарнинг-Speech-CH1-2-шаг 1](images/mrlearning-speach-ch1-2-step1.jpg)

2. <span data-ttu-id="63605-203">Убедитесь, что необходимая сцена находится в списке Scenes in Build (Сцены в сборке), нажав кнопку Add Open Scenes (Добавить открытые сцены).</span><span class="sxs-lookup"><span data-stu-id="63605-203">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="63605-204">Нажмите кнопку Параметры проигрывателя и выберите Параметры публикации.</span><span class="sxs-lookup"><span data-stu-id="63605-204">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="63605-205">В разделе возможности включите: Интернет, клиентский сервер Интернет, сервер клиента частной сети, микрофон и пространственное восприятие.</span><span class="sxs-lookup"><span data-stu-id="63605-205">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Microphone and Spatial Perception.</span></span>

4. <span data-ttu-id="63605-206">В том же параметрах проигрывателя перейдите к параметрам XR и выберите Виртуальная реальность, поддерживаемая в ON.</span><span class="sxs-lookup"><span data-stu-id="63605-206">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>

5. <span data-ttu-id="63605-207">Нажмите кнопку Build (Сборка), чтобы начать процесс сборки.</span><span class="sxs-lookup"><span data-stu-id="63605-207">Press the Build button to begin the build process.</span></span>

    ![мрлеарнинг-Speech-CH1-2-шаг 5](images/mrlearning-speach-ch1-2-step5.jpg)

6. <span data-ttu-id="63605-209">Создайте папку для приложения и укажите для нее название.</span><span class="sxs-lookup"><span data-stu-id="63605-209">Create and name a new folder for your application.</span></span> <span data-ttu-id="63605-210">На приведенном ниже изображении для хранения приложения была создана папка с именем App.</span><span class="sxs-lookup"><span data-stu-id="63605-210">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="63605-211">Щелкните Select Folder (Выбор папки), чтобы начать создание приложения в новой папке.</span><span class="sxs-lookup"><span data-stu-id="63605-211">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="63605-212">После завершения создания вы можете закрыть окно Build Settings (Параметры сборки) в Unity.</span><span class="sxs-lookup"><span data-stu-id="63605-212">After the build has completed, you may close the "Build Settings" window in Unity.</span></span>

    ![мрлеарнинг-Speech-CH1-2-шаг 6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    ><span data-ttu-id="63605-214">Если сборка завершилась сбоем, попробуйте выполнить ее заново или перезапустите Unity и повторите попытку.</span><span class="sxs-lookup"><span data-stu-id="63605-214">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="63605-215">Если отображается ошибка, например "ошибка: CS0246 = не удалось найти тип или имя пространства имен" XX "(возможно, отсутствует директива using или ссылка на сборку?)", возможно, потребуется установить [пакет SDK для Windows 10 (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) .</span><span class="sxs-lookup"><span data-stu-id="63605-215">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span>

7. <span data-ttu-id="63605-216">После завершения сборки откройте созданную папку, содержащую файлы только что созданного приложения.</span><span class="sxs-lookup"><span data-stu-id="63605-216">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="63605-217">Дважды щелкните файл решения ". sln", чтобы открыть файл решения в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63605-217">Double-click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="63605-218">Не забудьте открыть созданную папку (т. е. папку App), если следовать соглашениям об именовании, указанным в предыдущих шагах, так как файл с расширением. sln находится за пределами этой папки, отличающейся от файла sln в папке Build.</span><span class="sxs-lookup"><span data-stu-id="63605-218">Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is different from the .sln file inside the build folder.</span></span> 

    ![мрлеарнинг-Speech-CH1-2-Step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    ><span data-ttu-id="63605-220">Если Visual Studio предложит установить новые компоненты, убедитесь, что все необходимые компоненты установлены, как указано на [странице "Установка средств"](install-the-tools.md) .</span><span class="sxs-lookup"><span data-stu-id="63605-220">If Visual Studio asks you to install new components, ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

8. <span data-ttu-id="63605-221">Подключите HoloLens 2 к компьютеру с помощью USB-кабеля.</span><span class="sxs-lookup"><span data-stu-id="63605-221">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="63605-222">Хотя в инструкциях этого урока предполагается, что вы будете развертывать тестирование на устройстве HoloLens 2, вы также можете выполнить развертывание на [эмуляторе HoloLens 2](using-the-hololens-emulator.md) или создать [пакет приложения для передачи данных на другое локальное устройство](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="63605-222">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

9. <span data-ttu-id="63605-223">Перед выполнением сборки для устройства включите на нем режим разработчика.</span><span class="sxs-lookup"><span data-stu-id="63605-223">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="63605-224">Если вы впервые используете HoloLens 2, в Visual Studio может появиться запрос на подключение к HoloLens 2 с использованием PIN-кода.</span><span class="sxs-lookup"><span data-stu-id="63605-224">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="63605-225">Выполните [эти инструкции](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio), если вам нужно включить режим разработчика или выполнить соединение с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63605-225">Please follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

10. <span data-ttu-id="63605-226">Настройте Visual Studio для сборки на устройство HoloLens 2, выбрав конфигурацию "Выпуск" и архитектуру ARM.</span><span class="sxs-lookup"><span data-stu-id="63605-226">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

    ![мрлеарнинг-Speech-CH1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. <span data-ttu-id="63605-228">Последний шаг — это сборка на вашем устройстве. Выберите "Отладка" > "Запуск без отладки".</span><span class="sxs-lookup"><span data-stu-id="63605-228">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="63605-229">Это приведет к немедленному запуску приложения на вашем устройстве после успешной сборки. Однако в Visual Studio сведения об отладке отображаться не будут.</span><span class="sxs-lookup"><span data-stu-id="63605-229">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="63605-230">Это также означает, что вы можете отсоединить USB-кабель во время выполнения приложения на устройстве HoloLens 2, не прерывая его работу.</span><span class="sxs-lookup"><span data-stu-id="63605-230">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="63605-231">Кроме того, вы можете выбрать "Сборка" > "Развернуть решение", чтобы развернуть решение на устройстве без автоматического запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="63605-231">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

    ![мрлеарнинг-Speech-CH1-2-step11. ФОРМАТЕ](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a><span data-ttu-id="63605-233">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="63605-233">Congratulations</span></span>

<span data-ttu-id="63605-234">Вы настроили распознавание речи в приложении на платформе Azure.</span><span class="sxs-lookup"><span data-stu-id="63605-234">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="63605-235">Запустите приложение, чтобы убедиться, что все функции и функции работают правильно.</span><span class="sxs-lookup"><span data-stu-id="63605-235">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="63605-236">Начните с произнесения слова «Wake», введенного на шаге 25, «активировать терминал».</span><span class="sxs-lookup"><span data-stu-id="63605-236">Start with saying the wake word you typed in Step 25, Activate Terminal.</span></span> <span data-ttu-id="63605-237">Нажмите кнопку микрофон, чтобы запустить распознавание речи.</span><span class="sxs-lookup"><span data-stu-id="63605-237">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="63605-238">Начните говорить.</span><span class="sxs-lookup"><span data-stu-id="63605-238">Begin speaking.</span></span> <span data-ttu-id="63605-239">Вы увидите слова расшифрованной в терминале во время диктовки.</span><span class="sxs-lookup"><span data-stu-id="63605-239">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="63605-240">Нажмите кнопку с микрофоном еще раз, чтобы отключить распознавание речи.</span><span class="sxs-lookup"><span data-stu-id="63605-240">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="63605-241">Выскажите «отклонить терминал», чтобы скрыть терминал Лунарком.</span><span class="sxs-lookup"><span data-stu-id="63605-241">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="63605-242">На следующем занятии вы узнаете, как динамически переключиться на использование распознавания речи на основе устройств для ситуаций, когда пакет SDK для распознавания символов Azure недоступен из-за того, что HoloLens 2 находится в автономном режиме.</span><span class="sxs-lookup"><span data-stu-id="63605-242">In the next lesson, you'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="63605-243">Следующий учебник: 2. Добавление автономного режима для локального перевода речи в текст</span><span class="sxs-lookup"><span data-stu-id="63605-243">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)
