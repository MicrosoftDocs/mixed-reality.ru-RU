---
title: Пример использования - HoloSketch стандартных, пространственных макет и UX, составляя эскиз приложения для HoloLens
description: HoloSketch предназначен для пространственных макета на устройстве и UX, составляя эскиз средство для HoloLens, помогающими заложить holographic опыт.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, составляя эскиз приложения
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600136"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="eb07e-104">Пример использования - HoloSketch стандартных, пространственных макет и UX, составляя эскиз приложения для HoloLens</span><span class="sxs-lookup"><span data-stu-id="eb07e-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="eb07e-105">HoloSketch предназначен для пространственных макета на устройстве и UX, составляя эскиз средство для HoloLens, помогающими заложить holographic опыт.</span><span class="sxs-lookup"><span data-stu-id="eb07e-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="eb07e-106">HoloSketch работает с помощью парных Bluetooth клавиатуры и мыши, а также жестов и голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="eb07e-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="eb07e-107">HoloSketch предназначена для обеспечения простого средства макета UX быструю визуализацию и итерации.</span><span class="sxs-lookup"><span data-stu-id="eb07e-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="eb07e-108">![HoloSketch: Пространственные макета и UX, составляя эскиз приложения для HoloLens.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="eb07e-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="eb07e-109">*HoloSketch: Пространственные макет и UX, составляя эскиз приложения для HoloLens*</span><span class="sxs-lookup"><span data-stu-id="eb07e-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="eb07e-110">![Простое средство макета UX для быструю визуализацию и итерации.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="eb07e-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="eb07e-111">*Простое средство макета UX для быструю визуализацию и итерации*</span><span class="sxs-lookup"><span data-stu-id="eb07e-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="eb07e-112">Компоненты</span><span class="sxs-lookup"><span data-stu-id="eb07e-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="eb07e-113">Примитивы для быстрого внедрения и создания прототипов масштабирования</span><span class="sxs-lookup"><span data-stu-id="eb07e-113">Primitives for quick studies and scale-prototyping</span></span>

![С помощью простых фигур](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="eb07e-115">Простые фигуры можно используйте для быстрого внедрения massing и создания прототипов масштабирования.</span><span class="sxs-lookup"><span data-stu-id="eb07e-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="eb07e-116">Импорт объектов через OneDrive</span><span class="sxs-lookup"><span data-stu-id="eb07e-116">Import objects through OneDrive</span></span>

![Импорт объектов](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="eb07e-118">Импорт изображения PNG и JPG или трехмерные объекты FBX (требуется упаковки в Unity) в смешанной реальности посредством OneDrive.</span><span class="sxs-lookup"><span data-stu-id="eb07e-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="eb07e-119">Работать с объектами</span><span class="sxs-lookup"><span data-stu-id="eb07e-119">Manipulate objects</span></span>

![Обработка объектов](images/manipulate-objects-640px.jpg)

<span data-ttu-id="eb07e-121">Работать с объектами (перемещения и поворота/масштаб) с интерфейсом знакомы трехмерного объекта.</span><span class="sxs-lookup"><span data-stu-id="eb07e-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="eb07e-122">Bluetooth, мыши или клавиатуры, жестов и голосовых команд</span><span class="sxs-lookup"><span data-stu-id="eb07e-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![поддерживает Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="eb07e-124">HoloSketch поддерживает мыши или клавиатуры Bluetooth, жестов и голосовых команд.</span><span class="sxs-lookup"><span data-stu-id="eb07e-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="eb07e-125">Фон</span><span class="sxs-lookup"><span data-stu-id="eb07e-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="eb07e-126">Важность возникновения данного дизайна, в устройстве</span><span class="sxs-lookup"><span data-stu-id="eb07e-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="eb07e-127">Если что-нибудь для HoloLens, очень важно для данного дизайна, в устройстве.</span><span class="sxs-lookup"><span data-stu-id="eb07e-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="eb07e-128">Один из самых больших проблем в смешанной реальности проектирование приложений — это трудно получить представление о масштабирования, положение и глубина, особенно через традиционный 2D чертежей.</span><span class="sxs-lookup"><span data-stu-id="eb07e-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="eb07e-129">Обмен данными по стоимости двумерные</span><span class="sxs-lookup"><span data-stu-id="eb07e-129">Cost of 2D based communication</span></span>

<span data-ttu-id="eb07e-130">Для эффективного взаимодействия потоки пользовательского интерфейса и сценариев для других пользователей, конструктор может оказаться тратит слишком много времени на создание ресурсов с помощью традиционных средств 2D, например Illustrator, Photoshop и PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="eb07e-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="eb07e-131">Таких 2D макетов часто требует дополнительных усилий, чтобы преобразовать их в 3D.</span><span class="sxs-lookup"><span data-stu-id="eb07e-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="eb07e-132">Некоторые идеи, теряются при это преобразование из 2D в 3D.</span><span class="sxs-lookup"><span data-stu-id="eb07e-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="eb07e-133">Процесс развертывания сложных</span><span class="sxs-lookup"><span data-stu-id="eb07e-133">Complex deployment process</span></span>

<span data-ttu-id="eb07e-134">Так как смешанной реальности находится новый холст для нас, он включает в себя много итерации разработки и проб и ошибок по своей природе.</span><span class="sxs-lookup"><span data-stu-id="eb07e-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="eb07e-135">Для конструктора, кто не знаком с инструментами, например Unity и Visual Studio не просто применить какое-то в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="eb07e-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="eb07e-136">Обычно необходимо пройти через процесс ниже, чтобы увидеть двухмерных и трехмерных графических объектов в устройство.</span><span class="sxs-lookup"><span data-stu-id="eb07e-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="eb07e-137">Это было больших препятствием для конструкторов быстро итерации идеи и сценарии.</span><span class="sxs-lookup"><span data-stu-id="eb07e-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="eb07e-138">![Процесс развертывания сложных](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="eb07e-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="eb07e-139">*Процесс развертывания*</span><span class="sxs-lookup"><span data-stu-id="eb07e-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="eb07e-140">Упрощенный процесс с HoloSketch</span><span class="sxs-lookup"><span data-stu-id="eb07e-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="eb07e-141">С помощью HoloSketch мы хотели упростить этот процесс без привлечения средства разработки и портала связывание устройств.</span><span class="sxs-lookup"><span data-stu-id="eb07e-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="eb07e-142">Использование OneDrive, пользователи могут легко помещать двухмерных и трехмерных ресурсов в HoloLens.</span><span class="sxs-lookup"><span data-stu-id="eb07e-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="eb07e-143">![Упрощенный процесс с HoloSketch](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="eb07e-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="eb07e-144">*Упрощенный процесс с HoloSketch*</span><span class="sxs-lookup"><span data-stu-id="eb07e-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="eb07e-145">Поощряя трехмерного проектирования мышление и решения</span><span class="sxs-lookup"><span data-stu-id="eb07e-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="eb07e-146">Мы подумали, что это средство даст конструкторы возможность изучите решения в полностью трехмерном пространстве, а не зависнуть в 2D.</span><span class="sxs-lookup"><span data-stu-id="eb07e-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="eb07e-147">Они не придется задумываться о создании 3D фона для их пользовательского интерфейса, так как фон является реального мира в случае Hololens.</span><span class="sxs-lookup"><span data-stu-id="eb07e-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="eb07e-148">HoloSketch открывает позволяет разработчикам легко просматривать трехмерной графикой на устройство Hololens.</span><span class="sxs-lookup"><span data-stu-id="eb07e-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="eb07e-149">Начало работы</span><span class="sxs-lookup"><span data-stu-id="eb07e-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="eb07e-150">Как импортировать в HoloSketch двумерные изображения (JPG или PNG)</span><span class="sxs-lookup"><span data-stu-id="eb07e-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="eb07e-151">Отправьте изображения JPG/PNG в папке OneDrive «Документы/HoloSketch».</span><span class="sxs-lookup"><span data-stu-id="eb07e-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="eb07e-152">Из меню OneDrive в HoloSketch можно выбрать и поместить изображение в среде.</span><span class="sxs-lookup"><span data-stu-id="eb07e-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="eb07e-153">![Импорт изображения](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="eb07e-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="eb07e-154">*Импорт изображений и трехмерных объектов через OneDrive*</span><span class="sxs-lookup"><span data-stu-id="eb07e-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="eb07e-155">Импорт трехмерных объектов в HoloSketch</span><span class="sxs-lookup"><span data-stu-id="eb07e-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="eb07e-156">Перед отправкой в папке OneDrive, выполните следующие действия, чтобы упаковать трехмерных объектов в набор средств Unity.</span><span class="sxs-lookup"><span data-stu-id="eb07e-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="eb07e-157">С помощью этого процесса можно импортировать файлы FBX/OBJ из Maya, кинотеатрах 4 D и Microsoft Paint 3D 3D программ.</span><span class="sxs-lookup"><span data-stu-id="eb07e-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="eb07e-158">В настоящее время поддерживается создание пакета средств с 5.4.5f1 версии Unity.</span><span class="sxs-lookup"><span data-stu-id="eb07e-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="eb07e-159">Скачайте и откройте проект Unity [«AssetBunlder_Unity»](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span><span class="sxs-lookup"><span data-stu-id="eb07e-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="eb07e-160">Этот проект Unity включает скрипт для средства формирования пакета.</span><span class="sxs-lookup"><span data-stu-id="eb07e-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="eb07e-161">Создайте новый объект GameObject.</span><span class="sxs-lookup"><span data-stu-id="eb07e-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="eb07e-162">Имя GameObject, на основе содержимого.</span><span class="sxs-lookup"><span data-stu-id="eb07e-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="eb07e-163">На панели Инспектора нажмите кнопку «Добавить компонент» и добавьте «Collider поле».</span><span class="sxs-lookup"><span data-stu-id="eb07e-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![На панели Инспектора нажмите кнопку «Добавить компонент» и добавьте «Collider поле»](images/holosketch-10a-assetbundles-1000px.png)
   
   ![На панели Инспектора нажмите кнопку «Добавить компонент» и добавьте «Поле Collider» #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="eb07e-166">Импорт трехмерного FBX файла, перетащив его в панель «проект».</span><span class="sxs-lookup"><span data-stu-id="eb07e-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="eb07e-167">Перетащите объект на панели «иерархии» **в ваш новый объект GameObject**.</span><span class="sxs-lookup"><span data-stu-id="eb07e-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Перетащите объект на панели иерархии под ваш новый объект GameObject](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="eb07e-169">Настройте измерения collider, если он не совпадает с объектом.</span><span class="sxs-lookup"><span data-stu-id="eb07e-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="eb07e-170">Повернуть объект сталкиваются **оси z**.</span><span class="sxs-lookup"><span data-stu-id="eb07e-170">Rotate the object to face **Z-axis**.</span></span>

   ![Настройте collider измерения, если он не совпадает с объектом.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="eb07e-172">Перетащите объект из панели «иерархии» на панели «проект», чтобы **сделать prefab**.</span><span class="sxs-lookup"><span data-stu-id="eb07e-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="eb07e-173">В нижней части панели Инспектора откройте раскрывающийся список, создать и назначить новое уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="eb07e-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="eb07e-174">Ниже примере показано добавление и назначение «brownchair» для имени AssetBundle.</span><span class="sxs-lookup"><span data-stu-id="eb07e-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![На нижней панели Инспектора откройте раскрывающийся список и назначить новое уникальное имя.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="eb07e-176">Подготовьте эскиз для объекта модели.</span><span class="sxs-lookup"><span data-stu-id="eb07e-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="eb07e-177">![Перетащите изображения на панель «проект» и назначить имя, используемое для объекта.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="eb07e-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="eb07e-178">Создайте папку с именем «Assetbundles», «Средства» в папке проекта Unity.</span><span class="sxs-lookup"><span data-stu-id="eb07e-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="eb07e-179">В меню ресурсов выберите «Создать AssetBundles», чтобы создать файл.</span><span class="sxs-lookup"><span data-stu-id="eb07e-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="eb07e-180">![В меню ресурсов выберите «Создать AssetBundles», чтобы создать файл.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="eb07e-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="eb07e-181">**Отправьте созданный файл в папку /Files/Documents/HoloSketch в OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="eb07e-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="eb07e-182">Отправьте файл asset_unique_name только.</span><span class="sxs-lookup"><span data-stu-id="eb07e-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="eb07e-183">Не нужно передать файлы манифеста или AssetBundles файл.</span><span class="sxs-lookup"><span data-stu-id="eb07e-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="eb07e-184">![Добавление файлов в файлы/документы/HoloSketch/папку](images/holosketch-onedriveupload-1000px.png)
![вы увидите добавлены трехмерный объект, в меню HoloSketch в OneDrive](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="eb07e-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="eb07e-185">Как работать с объектами</span><span class="sxs-lookup"><span data-stu-id="eb07e-185">How to manipulate the objects</span></span>

<span data-ttu-id="eb07e-186">HoloSketch поддерживает традиционный интерфейс, который широко используется в трехмерных программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="eb07e-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="eb07e-187">Вы можете использовать перемещение, поворот, масштабирование объектов с помощью жестов и мыши.</span><span class="sxs-lookup"><span data-stu-id="eb07e-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="eb07e-188">Кроме того, можно быстро переключаться между различными режимами с помощью голоса или клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="eb07e-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="eb07e-189">Режимы обработки объектов</span><span class="sxs-lookup"><span data-stu-id="eb07e-189">Object manipulation modes</span></span>

<span data-ttu-id="eb07e-190">![Как работать с объектами](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="eb07e-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="eb07e-191">*Как работать с объектами*</span><span class="sxs-lookup"><span data-stu-id="eb07e-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="eb07e-192">Меню контекстуальное и инструментарий</span><span class="sxs-lookup"><span data-stu-id="eb07e-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="eb07e-193">**С помощью контекстных меню**</span><span class="sxs-lookup"><span data-stu-id="eb07e-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="eb07e-194">Двойные жест касания, чтобы открыть контекстное меню.</span><span class="sxs-lookup"><span data-stu-id="eb07e-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="eb07e-195">Элементы меню:</span><span class="sxs-lookup"><span data-stu-id="eb07e-195">Menu items:</span></span>
* <span data-ttu-id="eb07e-196">**Область макета:** Это — это трехмерной сетки система, где вы можете макета несколько объектов и управлять ими как группой.</span><span class="sxs-lookup"><span data-stu-id="eb07e-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="eb07e-197">Двойные air касание в области макета, чтобы добавить объекты к нему.</span><span class="sxs-lookup"><span data-stu-id="eb07e-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="eb07e-198">**Примитивы:** Используйте кубы, сфер, цилиндров и конусы для massing внедрения.</span><span class="sxs-lookup"><span data-stu-id="eb07e-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="eb07e-199">**OneDrive:** Откройте меню OneDrive для импорта объектов.</span><span class="sxs-lookup"><span data-stu-id="eb07e-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="eb07e-200">**Справка:** Отображает справку экрана.</span><span class="sxs-lookup"><span data-stu-id="eb07e-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="eb07e-201">![Контекстные меню](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="eb07e-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="eb07e-202">*Контекстные меню*</span><span class="sxs-lookup"><span data-stu-id="eb07e-202">*Contextual menu*</span></span>

<span data-ttu-id="eb07e-203">**С помощью меню средства лента**</span><span class="sxs-lookup"><span data-stu-id="eb07e-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="eb07e-204">Перемещение, поворот, масштабирование, сохранения и загрузки сцены меню будут доступны средства лента.</span><span class="sxs-lookup"><span data-stu-id="eb07e-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="eb07e-205">С помощью клавиатуры, жестов и голосовых команд</span><span class="sxs-lookup"><span data-stu-id="eb07e-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="eb07e-206">![Клавиатуры, жестов и голосовых команд](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="eb07e-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="eb07e-207">*Клавиатуры, жестов и голосовых команд*</span><span class="sxs-lookup"><span data-stu-id="eb07e-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="eb07e-208">Загрузка приложения</span><span class="sxs-lookup"><span data-stu-id="eb07e-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="eb07e-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Загрузите и установите приложение HoloSketch бесплатно из Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="eb07e-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="eb07e-210">Известные проблемы</span><span class="sxs-lookup"><span data-stu-id="eb07e-210">Known issues</span></span>
* <span data-ttu-id="eb07e-211">В настоящее время создания пакета ресурса поддерживается с **5.4.5f1 версии Unity.**</span><span class="sxs-lookup"><span data-stu-id="eb07e-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="eb07e-212">В зависимости от объема данных в OneDrive приложение может отображаться так, как если бы он был остановлен при загрузке содержимого OneDrive</span><span class="sxs-lookup"><span data-stu-id="eb07e-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="eb07e-213">В настоящее время сохранения и загрузки функция поддерживает только простые объекты</span><span class="sxs-lookup"><span data-stu-id="eb07e-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="eb07e-214">Текст, звук, видео и фотографий меню отключены в контекстные меню</span><span class="sxs-lookup"><span data-stu-id="eb07e-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="eb07e-215">«Воспроизвести» в меню «инструментарий» удаляет элементы управления</span><span class="sxs-lookup"><span data-stu-id="eb07e-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="eb07e-216">Общий доступ к вашей чертежей</span><span class="sxs-lookup"><span data-stu-id="eb07e-216">Sharing your sketches</span></span>

<span data-ttu-id="eb07e-217">Можно использовать функцию записи видео в HoloLens, необходимо указать "Привет, Кортана, запуск и остановка записи".</span><span class="sxs-lookup"><span data-stu-id="eb07e-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="eb07e-218">Нажмите клавишу тома вверх/вниз ключ друг с другом, чтобы сделать снимок вашего эскиза.</span><span class="sxs-lookup"><span data-stu-id="eb07e-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="eb07e-219">Об авторах</span><span class="sxs-lookup"><span data-stu-id="eb07e-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="eb07e-220"><b>Park Yoon донг</b></span><span class="sxs-lookup"><span data-stu-id="eb07e-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="eb07e-221">Конструктор UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb07e-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="eb07e-222"><b>Патрик Sebring</b></span><span class="sxs-lookup"><span data-stu-id="eb07e-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="eb07e-223">Разработчик @Microsoft</span><span class="sxs-lookup"><span data-stu-id="eb07e-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
