---
title: 'Пример использования: создание Холоскетч, пространственного макета и приложения для наброска, нарисуйте пользовательский интерфейс для HoloLens'
description: Холоскетч — это пространственный макет на устройстве и средство создания наброска UX для HoloLens, помогающее в создании Holographic.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Холоскетч, HoloLens, Windows Mixed Reality, набросок, приложение
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524435"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="6c852-104">Пример использования: создание Холоскетч, пространственного макета и приложения для наброска, нарисуйте пользовательский интерфейс для HoloLens</span><span class="sxs-lookup"><span data-stu-id="6c852-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="6c852-105">Холоскетч — это пространственный макет на устройстве и средство создания наброска UX для HoloLens, помогающее в создании Holographic.</span><span class="sxs-lookup"><span data-stu-id="6c852-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="6c852-106">Холоскетч работает с помощью парной клавиатуры и мыши Bluetooth, а также команд жестов и голоса.</span><span class="sxs-lookup"><span data-stu-id="6c852-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="6c852-107">Цель Холоскетч — предоставить простое средство компоновки UX для быстрой визуализации и итерации.</span><span class="sxs-lookup"><span data-stu-id="6c852-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="6c852-108">![Холоскетч: Пространственный макет и приложение наметки UX для HoloLens.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="6c852-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="6c852-109">*Холоскетч: пространственный макет и приложение для наброска пользовательского интерфейса для HoloLens*</span><span class="sxs-lookup"><span data-stu-id="6c852-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="6c852-110">![Простое средство компоновки UX для быстрой визуализации и итерации.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="6c852-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="6c852-111">*Простое средство компоновки UX для быстрой визуализации и итерации*</span><span class="sxs-lookup"><span data-stu-id="6c852-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="6c852-112">Компоненты</span><span class="sxs-lookup"><span data-stu-id="6c852-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="6c852-113">Примитивы для быстрых исследований и масштабирования — создание прототипов</span><span class="sxs-lookup"><span data-stu-id="6c852-113">Primitives for quick studies and scale-prototyping</span></span>

![Использование примитивных фигур](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="6c852-115">Используйте примитивные фигуры для быстрой массовой практики и масштабирования — создания прототипов.</span><span class="sxs-lookup"><span data-stu-id="6c852-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="6c852-116">Импорт объектов с помощью OneDrive</span><span class="sxs-lookup"><span data-stu-id="6c852-116">Import objects through OneDrive</span></span>

![Импорт объектов](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="6c852-118">Импорт изображений PNG/JPG или трехмерных объектов FBX (требуется упаковка в Unity) в пространство смешанной реальности с помощью OneDrive.</span><span class="sxs-lookup"><span data-stu-id="6c852-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="6c852-119">Обработка объектов</span><span class="sxs-lookup"><span data-stu-id="6c852-119">Manipulate objects</span></span>

![Обработка объектов](images/manipulate-objects-640px.jpg)

<span data-ttu-id="6c852-121">Управлять объектами (перемещение, вращение и масштабирование) с помощью привычного интерфейса трехмерных объектов.</span><span class="sxs-lookup"><span data-stu-id="6c852-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="6c852-122">Bluetooth, мышь, клавиатура, жесты и команды Voice</span><span class="sxs-lookup"><span data-stu-id="6c852-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![поддерживает Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="6c852-124">Холоскетч поддерживает мышь Bluetooth/клавиатуру, жесты и команды Voice.</span><span class="sxs-lookup"><span data-stu-id="6c852-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="6c852-125">Фон</span><span class="sxs-lookup"><span data-stu-id="6c852-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="6c852-126">Важность проекта на устройстве</span><span class="sxs-lookup"><span data-stu-id="6c852-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="6c852-127">Если вы разрабатываете что-то для HoloLens, очень важно поработать с вашим дизайном на устройстве.</span><span class="sxs-lookup"><span data-stu-id="6c852-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="6c852-128">Одна из крупнейших проблем в проектировании приложения смешанной реальности заключается в том, что трудно получить представление о масштабе, положении и глубине, особенно с помощью традиционных двумерных эскизов.</span><span class="sxs-lookup"><span data-stu-id="6c852-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="6c852-129">Стоимость соединения на основе 2D</span><span class="sxs-lookup"><span data-stu-id="6c852-129">Cost of 2D based communication</span></span>

<span data-ttu-id="6c852-130">Для эффективного обмена потоками и сценариями UX с другими разработчиками может потребоваться потратить много времени на создание ресурсов с помощью традиционных инструментов 2D, таких как Illustrator, Photoshop и PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="6c852-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="6c852-131">Эти двумерные модели часто потребовали дополнительных усилий по преобразованию их в трехмерную графику.</span><span class="sxs-lookup"><span data-stu-id="6c852-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="6c852-132">Некоторые идеи в этом переводе теряются с 2D на 3D.</span><span class="sxs-lookup"><span data-stu-id="6c852-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="6c852-133">Сложный процесс развертывания</span><span class="sxs-lookup"><span data-stu-id="6c852-133">Complex deployment process</span></span>

<span data-ttu-id="6c852-134">Так как Смешанная реальность — это новый холст для нас, он включает в себя множество итераций и пробных версий, а также ошибок по своей природе.</span><span class="sxs-lookup"><span data-stu-id="6c852-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="6c852-135">Для проектировщиков, которые не знакомы с такими инструментами, как Unity и Visual Studio, не очень просто разместить что-то в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6c852-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="6c852-136">Как правило, для просмотра 2D-и трехмерной иллюстраций на устройстве необходимо выполнить приведенный ниже процесс.</span><span class="sxs-lookup"><span data-stu-id="6c852-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="6c852-137">Это было большое препятствие для разработчиков, быстро просматривая идеи и сценарии.</span><span class="sxs-lookup"><span data-stu-id="6c852-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="6c852-138">![Сложный процесс развертывания](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6c852-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="6c852-139">*Процесс развертывания*</span><span class="sxs-lookup"><span data-stu-id="6c852-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="6c852-140">Упрощенный процесс с помощью Холоскетч</span><span class="sxs-lookup"><span data-stu-id="6c852-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="6c852-141">С Холоскетч мы хотели упростить этот процесс, не прибегая к средствам разработки и связыванию портала устройств.</span><span class="sxs-lookup"><span data-stu-id="6c852-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="6c852-142">С помощью OneDrive пользователи могут легко размещать 2D-или трехмерные ресурсы в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6c852-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="6c852-143">![Упрощенный процесс с помощью Холоскетч](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6c852-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="6c852-144">*Упрощенный процесс с помощью Холоскетч*</span><span class="sxs-lookup"><span data-stu-id="6c852-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="6c852-145">Поощрение проектирования и решений, основанных на трехмерном проектировании</span><span class="sxs-lookup"><span data-stu-id="6c852-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="6c852-146">Мы думали, что это средство предоставит дизайнерам возможность исследовать решения в действительно трехмерном пространстве и не зависнуть в двухмерном виде.</span><span class="sxs-lookup"><span data-stu-id="6c852-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="6c852-147">Им не нужно думать о создании трехмерного фона для пользовательского интерфейса, так как в случае с Hololens фон является реальным миром.</span><span class="sxs-lookup"><span data-stu-id="6c852-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="6c852-148">Холоскетч открывает способ, позволяющий дизайнерам легко исследовать трехмерную структуру на Hololens.</span><span class="sxs-lookup"><span data-stu-id="6c852-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="6c852-149">Начало работы</span><span class="sxs-lookup"><span data-stu-id="6c852-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="6c852-150">Импорт 2D-изображений (JPG/PNG) в Холоскетч</span><span class="sxs-lookup"><span data-stu-id="6c852-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="6c852-151">Отправка изображений в формате JPG/PNG в папку OneDrive "Documents/Холоскетч".</span><span class="sxs-lookup"><span data-stu-id="6c852-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="6c852-152">В меню OneDrive в Холоскетч можно будет выбрать и поместить образ в среду.</span><span class="sxs-lookup"><span data-stu-id="6c852-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="6c852-153">![Импорт 2D-изображений](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6c852-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="6c852-154">*Импорт изображений и трехмерных объектов с помощью OneDrive*</span><span class="sxs-lookup"><span data-stu-id="6c852-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="6c852-155">Импорт трехмерных объектов в Холоскетч</span><span class="sxs-lookup"><span data-stu-id="6c852-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="6c852-156">Перед отправкой в папку OneDrive выполните следующие действия, чтобы упаковать трехмерные объекты в пакет ресурсов Unity.</span><span class="sxs-lookup"><span data-stu-id="6c852-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="6c852-157">С помощью этого процесса можно импортировать файлы FBX/OBJ из трехмерного программного обеспечения, например Maya, кинотеатров 4D и Microsoft Paint 3D.</span><span class="sxs-lookup"><span data-stu-id="6c852-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="6c852-158">В настоящее время создание пакета активов поддерживается в Unity версии 5.4.5 F1.</span><span class="sxs-lookup"><span data-stu-id="6c852-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="6c852-159">Скачайте и откройте проект Unity ["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span><span class="sxs-lookup"><span data-stu-id="6c852-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="6c852-160">Этот проект Unity включает скрипт для создания ресурсов пакета.</span><span class="sxs-lookup"><span data-stu-id="6c852-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="6c852-161">Создайте новый GameObject.</span><span class="sxs-lookup"><span data-stu-id="6c852-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="6c852-162">Назовите GameObject на основе содержимого.</span><span class="sxs-lookup"><span data-stu-id="6c852-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="6c852-163">На панели инспектора нажмите кнопку "добавить компонент" и добавьте "Box конфликтует".</span><span class="sxs-lookup"><span data-stu-id="6c852-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![На панели инспектора нажмите кнопку "добавить компонент" и добавьте "Box конфликтует".](images/holosketch-10a-assetbundles-1000px.png)
   
   ![На панели инспектора нажмите кнопку "добавить компонент" и добавьте "Box конфликтует" #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="6c852-166">Импортируйте 3D-файл FBX, перетащив его на панель проекта.</span><span class="sxs-lookup"><span data-stu-id="6c852-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="6c852-167">Перетащите объект на панель Иерархия **под новым GameObject**.</span><span class="sxs-lookup"><span data-stu-id="6c852-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Перетащите объект на панель Иерархия под новым GameObject](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="6c852-169">Измените измерение, если оно не соответствует объекту.</span><span class="sxs-lookup"><span data-stu-id="6c852-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="6c852-170">Поворот объекта на лицевую **ось Z**.</span><span class="sxs-lookup"><span data-stu-id="6c852-170">Rotate the object to face **Z-axis**.</span></span>

   ![Настройте измерение "конфликты", если оно не соответствует объекту.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="6c852-172">Перетащите объект с панели Иерархия на панель проект, чтобы **сделать его prefab**.</span><span class="sxs-lookup"><span data-stu-id="6c852-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="6c852-173">В нижней части панели инспектора щелкните раскрывающийся список, создайте и назначьте новое уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="6c852-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="6c852-174">Ниже приведен пример добавления и назначения "бровнчаир" для имени Ассетбундле.</span><span class="sxs-lookup"><span data-stu-id="6c852-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![В нижней части панели инспектора щелкните раскрывающийся список и назначьте новое уникальное имя.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="6c852-176">Подготовка эскиза для объекта модели.</span><span class="sxs-lookup"><span data-stu-id="6c852-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="6c852-177">![Перетащите изображение на панель проекта и назначьте имя, используемое для объекта.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6c852-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="6c852-178">Создайте папку с именем "Ассетбундлес" в папке "Asset" проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="6c852-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="6c852-179">В меню "активы" выберите "Build Ассетбундлес" (создать файл).</span><span class="sxs-lookup"><span data-stu-id="6c852-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="6c852-180">![В меню "активы" выберите "Build Ассетбундлес" (создать файл).](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="6c852-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="6c852-181">**Отправьте созданный файл в папку/Филес/документс/холоскетч в OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="6c852-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="6c852-182">Отправьте только файл asset_unique_name.</span><span class="sxs-lookup"><span data-stu-id="6c852-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="6c852-183">Не нужно отправлять файлы манифеста или файл Ассетбундлес.</span><span class="sxs-lookup"><span data-stu-id="6c852-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="6c852-184">![Добавить файлы в файлы/документы/холоскетч/папку](images/holosketch-onedriveupload-1000px.png)
![вы увидите добавленный трехмерный объект в меню OneDrive для холоскетч](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6c852-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="6c852-185">Как управлять объектами</span><span class="sxs-lookup"><span data-stu-id="6c852-185">How to manipulate the objects</span></span>

<span data-ttu-id="6c852-186">Холоскетч поддерживает традиционный интерфейс, широко используемый в трехмерном программном обеспечении.</span><span class="sxs-lookup"><span data-stu-id="6c852-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="6c852-187">Можно использовать перемещение, вращение, масштабировать объекты с помощью жестов и мыши.</span><span class="sxs-lookup"><span data-stu-id="6c852-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="6c852-188">Можно быстро переключаться между различными режимами с помощью голоса или клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="6c852-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="6c852-189">Режимы обработки объектов</span><span class="sxs-lookup"><span data-stu-id="6c852-189">Object manipulation modes</span></span>

<span data-ttu-id="6c852-190">![Как управлять объектами](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6c852-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="6c852-191">*Как управлять объектами*</span><span class="sxs-lookup"><span data-stu-id="6c852-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="6c852-192">Контекстные меню и служебная лента инструментов</span><span class="sxs-lookup"><span data-stu-id="6c852-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="6c852-193">**Использование контекстного меню**</span><span class="sxs-lookup"><span data-stu-id="6c852-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="6c852-194">Дважды коснитесь, чтобы открыть контекстное меню.</span><span class="sxs-lookup"><span data-stu-id="6c852-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="6c852-195">Пункты меню:</span><span class="sxs-lookup"><span data-stu-id="6c852-195">Menu items:</span></span>
* <span data-ttu-id="6c852-196">**Область макета:** Это система трехмерной сетки, в которой можно разработать несколько объектов и управлять ими как группой.</span><span class="sxs-lookup"><span data-stu-id="6c852-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="6c852-197">Дважды коснитесь области макета, чтобы добавить в нее объекты.</span><span class="sxs-lookup"><span data-stu-id="6c852-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="6c852-198">**Primitives** Используйте Кубы, шарик, цилиндры и конес для массовых исследований.</span><span class="sxs-lookup"><span data-stu-id="6c852-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="6c852-199">**Хранилища** Откройте меню OneDrive, чтобы импортировать объекты.</span><span class="sxs-lookup"><span data-stu-id="6c852-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="6c852-200">**Справка:** Отображает экран справки.</span><span class="sxs-lookup"><span data-stu-id="6c852-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="6c852-201">![Контекстное меню](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="6c852-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="6c852-202">*Контекстное меню*</span><span class="sxs-lookup"><span data-stu-id="6c852-202">*Contextual menu*</span></span>

<span data-ttu-id="6c852-203">**Использование меню "лента инструментов"**</span><span class="sxs-lookup"><span data-stu-id="6c852-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="6c852-204">В меню лента инструментов можно перемещать, вращать, масштабировать, сохранять и загружать сцены.</span><span class="sxs-lookup"><span data-stu-id="6c852-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="6c852-205">Использование клавиатуры, жестов и Voice Command</span><span class="sxs-lookup"><span data-stu-id="6c852-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="6c852-206">![Клавиатура, жесты и команды Voice](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="6c852-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="6c852-207">*Клавиатура, жесты и команды Voice*</span><span class="sxs-lookup"><span data-stu-id="6c852-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="6c852-208">Скачать приложение</span><span class="sxs-lookup"><span data-stu-id="6c852-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="6c852-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Скачайте и установите бесплатное приложение Холоскетч из Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="6c852-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="6c852-210">Известные проблемы</span><span class="sxs-lookup"><span data-stu-id="6c852-210">Known issues</span></span>
* <span data-ttu-id="6c852-211">В настоящее время создание пакета активов поддерживается в **Unity версии 5.4.5 F1.**</span><span class="sxs-lookup"><span data-stu-id="6c852-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="6c852-212">В зависимости от объема данных в OneDrive приложение может выглядеть так, как если бы оно было остановлено при загрузке содержимого OneDrive.</span><span class="sxs-lookup"><span data-stu-id="6c852-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="6c852-213">В настоящее время функция сохранения и загрузки поддерживает только примитивные объекты</span><span class="sxs-lookup"><span data-stu-id="6c852-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="6c852-214">Меню "текст", "звук", "видео" и "Фото" отключены в контекстном меню</span><span class="sxs-lookup"><span data-stu-id="6c852-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="6c852-215">Кнопка воспроизведение в меню лента инструментов очищает приспособлений манипуляции</span><span class="sxs-lookup"><span data-stu-id="6c852-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="6c852-216">Совместное использование заэскизов</span><span class="sxs-lookup"><span data-stu-id="6c852-216">Sharing your sketches</span></span>

<span data-ttu-id="6c852-217">Вы можете использовать функцию записи видео в HoloLens, выполнив слово "Привет, запуск и завершение записи".</span><span class="sxs-lookup"><span data-stu-id="6c852-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="6c852-218">Нажмите клавишу "вверх/вниз", чтобы создать изображение своего эскиза.</span><span class="sxs-lookup"><span data-stu-id="6c852-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="6c852-219">Об авторах</span><span class="sxs-lookup"><span data-stu-id="6c852-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="6c852-220"><b>Донг Йоон</b></span><span class="sxs-lookup"><span data-stu-id="6c852-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="6c852-221">Конструктор UX@Microsoft</span><span class="sxs-lookup"><span data-stu-id="6c852-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="6c852-222"><b>Патрик Себринг</b></span><span class="sxs-lookup"><span data-stu-id="6c852-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="6c852-223">Developer@Microsoft</span><span class="sxs-lookup"><span data-stu-id="6c852-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
