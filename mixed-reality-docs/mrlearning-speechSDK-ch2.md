## <a name="lesson-2"></a><span data-ttu-id="81866-101">Занятие 2</span><span class="sxs-lookup"><span data-stu-id="81866-101">Lesson 2</span></span>

<span data-ttu-id="81866-102">На занятии 2, мы добавим автономный режим, который позволит нам для выполнения локальных перевода речи в текст, когда не удалось подключиться к службе Azure, и мы будет *имитировать* отключенном состоянии.</span><span class="sxs-lookup"><span data-stu-id="81866-102">In Lesson 2, we will add an Offline mode that will allow us to perform local speech-to-text translation when we are unable to connect to the Azure service and we will *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="81866-103">Выберите объект «Lunarcom_Base» в иерархии и нажмите кнопку «Добавить компонент» на панели инспектора.</span><span class="sxs-lookup"><span data-stu-id="81866-103">Select the "Lunarcom_Base" object in the hierarchy and click “Add Component” in the inspector panel.</span></span> <span data-ttu-id="81866-104">Найдите и выберите «Lunarcom автономной распознавания.»</span><span class="sxs-lookup"><span data-stu-id="81866-104">Search for and select the "Lunarcom Offline Recognition."</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. <span data-ttu-id="81866-106">Щелкните раскрывающийся список в «LunarcomOfflineRecognizer» и выберите «Включено».</span><span class="sxs-lookup"><span data-stu-id="81866-106">Click the dropdown in the “LunarcomOfflineRecognizer” and select “Enabled.”</span></span> <span data-ttu-id="81866-107">Это будет программы работают, как и у пользователя нет соединений проекта.</span><span class="sxs-lookup"><span data-stu-id="81866-107">This will program the project to act like the user doesn't have connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="81866-109">Теперь нажмите кнопку воспроизведения в редакторе Unity и протестируйте его.</span><span class="sxs-lookup"><span data-stu-id="81866-109">Now, press play on the Unity Editor and test it.</span></span> <span data-ttu-id="81866-110">Нажмите клавишу "микрофон" в левом нижнем углу в сцене и начните говорить.</span><span class="sxs-lookup"><span data-stu-id="81866-110">Press the microphone in the bottom left hand corner in the scene and begin speaking.</span></span> 

> <span data-ttu-id="81866-111">Обратите внимание: так как мы не в сети, функциональные возможности пробуждения Word был отключен.</span><span class="sxs-lookup"><span data-stu-id="81866-111">note: because we’re offline, the Wake Word functionality has been disabled.</span></span> <span data-ttu-id="81866-112">Таким образом, необходимо физически щелкните микрофон, каждый раз при необходимости получения речи распознается при автономном режиме.</span><span class="sxs-lookup"><span data-stu-id="81866-112">So, you will have to physically click the microphone every time you wish to have your speech recognized while offline.</span></span> 

<span data-ttu-id="81866-113">Ниже приведен пример сцены может выглядеть так:</span><span class="sxs-lookup"><span data-stu-id="81866-113">Below is an example of what your scene could look like:</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="81866-115">Поздравляем!</span><span class="sxs-lookup"><span data-stu-id="81866-115">Congratulations</span></span>

<span data-ttu-id="81866-116">Автономный режим работает!</span><span class="sxs-lookup"><span data-stu-id="81866-116">The offline mode has been enabled!</span></span> <span data-ttu-id="81866-117">Теперь когда вы будете от Интернета в любой форме, вы можете по-прежнему работать над проектом с помощью Speech SDK!</span><span class="sxs-lookup"><span data-stu-id="81866-117">Now when you're away from any form of internet, you can still work on your project with Speech-SDK!</span></span> 

[<span data-ttu-id="81866-118">Следующий урок. SpeechSDK занятие 3</span><span class="sxs-lookup"><span data-stu-id="81866-118">Next Lesson: SpeechSDK Lesson 3</span></span>](link placeholder)

