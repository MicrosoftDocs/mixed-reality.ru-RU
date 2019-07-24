---
title: Пространственный 230 — пространственное сопоставление
description: Выполните приведенное ниже пошаговое руководство по программированию с помощью Unity, Visual Studio и HoloLens, чтобы получить сведения о концепциях пространственного сопоставления.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: холотулкит, микседреалититулкит, микседреалититулкит-Unity, Academy, руководство, пространственное сопоставление, реконструкция поверхностей, сеть
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993561"
---
>[!NOTE]
>Учебники по смешанной реальности Academy были разработаны с учетом захватывающих головных телефонов HoloLens (1-го поколения) и смешанной реальности.  Поэтому важно оставить эти руководства на месте для разработчиков, которые по-прежнему ищут рекомендации по разработке для этих устройств.  Эти учебники **_не_** будут обновлены с использованием последних наборов инструментов или взаимодействий, используемых для HoloLens 2.  Они будут сохранены для продолжения работы на поддерживаемых устройствах. Появится новая серия руководств, которые будут опубликованы в будущем, где будет показано, как разрабатывать данные для HoloLens 2.  Это уведомление будет обновлено ссылкой на эти учебники при их публикации.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>Индекс MR 230: Пространственное сопоставление

[Пространственное сопоставление](spatial-mapping.md) объединяет реальный и виртуальный мир вместе с голограммами о среде. В MR-пространственном 230 (Project планетариум) мы расскажем:

* Проверьте окружение и передайте данные с HoloLens на компьютер разработки.
* Изучите шейдеры и Узнайте, как их использовать для визуализации своего пространства.
* Разбейте сетку помещений на простые плоскости с помощью обработки сетки.
* Выйдите за пределы приемов размещения, которые мы узнали в статье об [основных 101](holograms-101.md), и предоставьте отзыв о том, где можно поместить голограмму в среду.
* Изучите эффекты перекрытия, так что когда ваша голограмма находится за реальным объектом, вы по-прежнему можете увидеть ее с помощью концепции x-ray!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Хождение</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивные гарнитуры</a></th>
</tr><tr>
<td>Индекс MR 230: Пространственное сопоставление</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>предварительные требования

* КОМПЬЮТЕР с Windows 10, на котором [установлены правильные средства](install-the-tools.md).
* Некоторые базовые C# возможности программирования.
* Вы должны были выполнить [Основные сведения о MR 101](holograms-101.md).
* Устройство HoloLens, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) , необходимые для проекта. Требуется Unity 2017,2 или более поздней версии.
  * Если вам по-прежнему требуется поддержка Unity 5,6, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Если вам по-прежнему требуется поддержка Unity 5,5, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Если вам по-прежнему требуется поддержка Unity 5,4, используйте [Этот выпуск](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Отмена архивации файлов на Рабочий стол или другого места для удобства доступа.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он [доступен на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Примечания

* Параметр "включить Только мой код" в Visual Studio должен быть отключен (*снят*) в разделе Сервис > Параметры > Отладка для попадания в точки останова в коде.

## <a name="unity-setup"></a>Установка Unity

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Запустите **Unity**.
* Выберите **создать** , чтобы создать новый проект.
* Назовите проект **планетариум**.
* Убедитесь, что выбран параметр **3D** .
* Щелкните **Create Project** (Создать проект).
* После запуска Unity перейдите в раздел **правка > параметры проекта > Player**.
* На панели **инспектора** найдите и выберите зеленый значок **магазина Windows** .
* Разверните **другие параметры**.
* В разделе " **Подготовка** к просмотру" установите флажок **поддерживаемый виртуальный реальность** .
* Убедитесь, что **Windows holographic** отображается в списке **пакетов SDK виртуальной реальности**. В противном случае нажмите **+** кнопку в нижней части списка и выберите **Windows holographic**.
* Разверните узел **Параметры публикации**.
* В разделе **возможности** проверьте следующие параметры.
    * интернетклиентсервер
    * приватенетворкклиентсервер
    * Микрофон
    * спатиалперцептион
* Перейдите к разделу **изменение > параметры проекта > качество**
* На панели **инспектора** под значком магазина Windows выберите черную стрелку раскрывающегося списка в строке "по умолчанию" и измените значение по умолчанию на **очень низкое**.
* Перейдите в раздел **активы > импортировать пакет > настраиваемый пакет**.
* Перейдите в папку **. ..\холографикакадеми-холограмс-230-спатиалмаппинг\стартинг** .
* Щелкните **Планетариум. пакет unitypackage**.
* Нажмите кнопку **Открыть**.
* Появится окно **Импорт пакета Unity** , нажмите кнопку **Импорт** .
* Дождитесь, пока Unity завершит импорт всех ресурсов, которые понадобятся нам для выполнения этого проекта.
* На панели **Иерархия** удалите **основную камеру**.
* На панели **проект** в папке **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** найдите **основной объект Camera** .
* Перетащите **основной prefab камеры** в панель Иерархия.
* На панели **Иерархия** удалите объект **направленного освещения** .
* На панели **проект** в папке **голограммы** выберите объект курсора  .
* Перетащите & курсора  prefab в иерархию .
* На панели **Иерархия** выберите объект **курсора** .
* На панели **инспектора** щелкните раскрывающийся список **слой** и выберите **изменить слои..** ..
* Присвойте **пользовательскому уровню 31** значение "**спатиалмаппинг**".
* Сохраните новую сцену: **Файл > сохранить сцену как...**
* Щелкните **создать папку** и присвойте имя папке **сцены**.
* Назовите файл «**планетариум**» и сохраните его в папке « **сцены** ».

## <a name="chapter-1---scanning"></a>Глава 1. сканирование

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Служит**
* Узнайте о Сурфацеобсервер и о том, как его параметры влияют на работу и производительность.
* Создайте процесс сканирования комнаты для сбора сеток комнаты.

**Водим**
* В папке **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** на панели **проекта** найдите **спатиалмаппинг** prefab.
* Перетащите & **спатиалмаппинг** prefab на панель Иерархия  .

**Сборка и развертывание (часть 1)**
* В Unity выберите **файл > параметры сборки**.
* Нажмите кнопку **Добавить открытые сцены** , чтобы добавить сцену **планетариум** в сборку.
* Выберите **универсальная платформа Windows** в списке **платформа** и щелкните **параметр платформа**.
* Установите для **пакета SDK** значение **универсальной 10** , а для **типа сборки UWP** — **D3D**.
* Проверьте **проекты C# Unity**.
* Щелкните **Сборка**.
* Создайте **новую папку** с именем App.
* Щелкните папку **приложения** одним щелчком мыши.
* Нажмите кнопку **Выбор папки** .
* После завершения сборки Unity появится окно проводника.
* Дважды щелкните папку **приложения** , чтобы открыть ее.
* Дважды щелкните **Планетариум. sln** , чтобы загрузить проект в Visual Studio.
* В Visual Studio используйте верхнюю панель инструментов, чтобы изменить конфигурацию на **выпуск**.
* Измените платформу на **x86**.
* Щелкните стрелку раскрывающегося списка справа от "локальный компьютер" и выберите **Удаленный компьютер**.
* Введите [IP-адрес устройства](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) в поле адрес и измените режим проверки подлинности на **универсальный (незашифрованный протокол)** .
* Щелкните **Отладка-> начать без отладки** или нажмите клавиши **CTRL + F5**.
* Просмотрите панель **вывода** в Visual Studio для состояния сборки и развертывания.
* После развертывания приложения обходится комната. Вы увидите окружающие области, покрытые черными и белыми проволочными сетками.
* Сканирование окружающей среды. Обязательно взгляните на стены, цеилингс и пол.

**Сборка и развертывание (часть 2)**

Теперь давайте рассмотрим, как пространственное сопоставление может повлиять на производительность.
* В Unity выберите **Window > Profiler**.
* Щелкните **Добавить профилировщик > GPU**.
* Щелкните **активный профилировщик > <Enter IP>** .
* Введите **IP-адрес** HoloLens.
* Нажмите кнопку **Подключить**.
* Обратите внимание на число миллисекунд, необходимое для отображения кадра графическим процессором.
* Останавливает выполнение приложения на устройстве.
* Вернитесь в Visual Studio и откройте **SpatialMappingObserver.CS**. Он будет находиться в папке Холотулкит\спатиалмаппинг проекта Assembly-CSharp (универсальные приложения Windows).
* Найдите функцию " **спящий ()** " и добавьте следующую строку кода: **Трианглесперкубикметер = 1200;**
* Повторно разверните проект на устройстве, а затем снова **Подключите профилировщик**. Обратите внимание на изменение количества миллисекунд для отображения кадра.
* Останавливает выполнение приложения на устройстве.

**Сохранение и загрузка в Unity**

Наконец, давайте экономим сетку комнаты и загружая ее в Unity.
* Вернитесь в Visual Studio и удалите строку **трианглесперкубикметер** , добавленную в функцию спящего режима **()** во время предыдущего раздела.
* Повторно разверните проект на устройстве. Теперь мы должны работать с **500** треугольниками на кубический метр.
* Откройте браузер и введите свой IP-адрес HoloLens, чтобы перейти на **портал устройств Windows**.
* Выберите параметр **объемное представление** на панели слева.
* В разделе **реконструкция поверхности** нажмите кнопку **Обновить** .
* Следите за тем, как области, просмотренные на HoloLens, отображаются в окне отображения.
* Чтобы сохранить сканирование комнаты, нажмите кнопку **сохранить** .
* Откройте папку **downloads** , чтобы найти сохраненную модель комнаты **срмеш. obj**.
* Скопируйте **срмеш. obj** в папку **Assets** проекта Unity.
* В Unity выберите объект **спатиалмаппинг** на панели Иерархия  .
* Нахождение компонента **наблюдателя поверхности объектов (script)** .
* Щелкните окружность справа от свойства **модель комнаты** .
* Найдите и выберите объект **срмеш** , а затем закройте окно.
* Убедитесь, что свойство " **модель комнаты** "  на панели инспектора теперь имеет значение **срмеш**.
* Нажмите кнопку **Воспроизведение** , чтобы войти в режим предварительного просмотра Unity.
* Компонент Спатиалмаппинг загрузит сетки из сохраненной модели комнаты, чтобы их можно было использовать в Unity.
* Переключитесь в представление **сцены** , чтобы увидеть всю модель комнаты, отображаемую с помощью каркасного шейдера.
* Нажмите кнопку **воспроизвести** еще раз, чтобы выйти из режима предварительного просмотра.

**ПРИМЕЧАНИЕ.** При следующем входе в режим предварительного просмотра в Unity по умолчанию будет загружена сохраненная сетка комнаты.

## <a name="chapter-2---visualization"></a>Глава 2. Визуализация

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Служит**
* Изучите основы шейдеров.
* Визуализация окружающей среды.

**Водим**
* На панели **Иерархия** Unity выберите объект **спатиалмаппинг** .
* На панели **инспектора** найдите компонент **Диспетчер пространственных сопоставлений (script)** .
* Щелкните окружность справа от свойства " **материал поверхности** ".
* Найдите и выберите материал **блуелинесонваллс** и закройте окно.
* В папке " **шейдеры** " панели **проекта** дважды щелкните **блуелинесонваллс** , чтобы открыть шейдер в Visual Studio.
* Это простой шейдер пикселей (вершина на фрагмент), который выполняет следующие задачи:
    1. Преобразует расположение вершины в мировое пространство.
    2. Проверяет нормальную вершину, чтобы определить, является ли пиксель вертикальным.
    3. Задает цвет пикселя для отрисовки.

**Сборка и развертывание**
* Вернитесь в Unity и нажмите кнопку **Play** , чтобы перейти в режим предварительного просмотра.
* Синие линии будут отображаться на всех вертикальных поверхностях сетки комнаты (которая автоматически загружается из сохраненных данных сканирования).
* Перейдите на вкладку **сцена** , чтобы настроить представление комнаты и увидеть, как вся сетка комнаты отображается в Unity.
* На панели **проект** найдите папку **материалы** и выберите материал **блуелинесонваллс** .
* Измените некоторые свойства и посмотрите, как изменения отображаются в редакторе Unity.
    * На панели **инспектора** измените значение **линескале** , чтобы линии были более толстыми или более тонкими.
    * На панели **инспектора** настройте значение **линесперметер** , чтобы изменить количество линий, отображаемых на каждой стене.
* Снова нажмите кнопку **воспроизвести** , чтобы выйти из режима просмотра.
* Выполните сборку и развертывание в HoloLens и обратите внимание на то, как отрисовка шейдера отображается на реальных поверхностях.

Unity — это отличная работа по предварительному просмотру материалов, но рекомендуется всегда отвлекаться от просмотра на устройстве.

## <a name="chapter-3---processing"></a>Глава 3. обработка

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Служит**
* Узнайте о методах обработки данных пространственного сопоставления для использования в приложении.
* Анализ данных пространственного сопоставления для поиска плоскостей и удаления треугольников.
* Используйте плоскости для размещения голограмм.

**Водим**
* На панели **проекта** Unity в папке **голограмм** найдите объект **спатиалпроцессинг** .
* Перетащите & объект **спатиалпроцессинг** на панель Иерархия  .

Спатиалпроцессинг prefab включает компоненты для обработки данных пространственного сопоставления. **SurfaceMeshesToPlanes.CS** найдет и создаст плоскости на основе данных пространственного сопоставления. Для представления стен, этажей и цеилингс мы будем использовать плоскости в нашем приложении. Этот prefab также включает **RemoveSurfaceVertices.CS** , который может удалять вершины из сетки пространственных сопоставлений. Это можно использовать для создания отверстий в сетке или удаления лишних треугольников, которые больше не нужны (так как вместо них можно использовать плоскости).
* На панели **проекта** Unity в папке **голограмм** найдите объект **спацеколлектион** .
* Перетащите объект **спацеколлектион** на панель Иерархия.
* На панели **Иерархия** выберите объект **спатиалпроцессинг** .
* На панели **инспектора** найдите компонент **диспетчер пространства воспроизведения (script)** .
* Дважды щелкните **PlaySpaceManager.CS** , чтобы открыть его в Visual Studio.

PlaySpaceManager.cs содержит код, зависящий от приложения. Мы добавим в этот скрипт функциональные возможности, чтобы обеспечить следующее поведение:
1. Прерывать сбор данных пространственного сопоставления после превышения предельного времени сканирования (10 секунд).
2. Обработка данных пространственного сопоставления:
    1. Используйте Сурфацемешестопланес для создания более простого представления мира в виде плоскостей (стен, пол, цеилингс и т. д.).
    2. Используйте Ремовесурфацевертицес, чтобы удалить треугольники Surface, которые попадают в границы плоскости.
3. Создавайте коллекцию голограмм в мире и размещайте их на стенных и этажных плоскостях рядом с пользователем.

Выполните упражнения по написанию кода, помеченные в PlaySpaceManager.cs, или замените скрипт завершенным решением ниже:

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**Сборка и развертывание**
* Перед развертыванием в HoloLens нажмите кнопку **воспроизведения** в Unity, чтобы войти в режим воспроизведения.
* После загрузки сетки комнаты из файла подождите 10 секунд, прежде чем обработка начнется в сетке пространственных сопоставлений.
* После завершения обработки отобразятся плоскости, представляющие этаж, стены, потолк и т. д.
* После того как все плоскости будут найдены, в таблице пола рядом с камерой появится Солнечная система.
* В стены рядом с камерой должны появиться два плаката. Перейдите на вкладку **сцена** , если вы не видите их в **игровом** режиме.
* Нажмите кнопку **воспроизвести** еще раз, чтобы выйти из режима воспроизведения.
* Выполните сборку и развертывание в HoloLens, как обычно.
* Дождитесь завершения проверки и обработки данных пространственного сопоставления.
* Получив плоскости, попытайтесь найти солнечную систему и афиши в мире.

## <a name="chapter-4---placement"></a>Глава 4. размещение

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Служит**
* Определить, умещается ли голограмма на поверхности.
* Предоставьте отзыв пользователю, когда голограмма может уместиться на поверхности.

**Водим**
* На панели **Иерархия** Unity выберите объект **спатиалпроцессинг** .
* На панели **инспектора** найдите элемент " **сетки поверхности" для компонента "плоскости (скрипт)"** .
* Измените значение свойства **Draw плоскости** на **Nothing** , чтобы снять выделение.
* Измените значение свойства **Draw плоскости** на **настенный**, чтобы отображались только стены.
* На панели **проект** в папке **скрипты** дважды щелкните **Placeable.CS** , чтобы открыть ее в Visual Studio.

**Размещенный** скрипт уже присоединен к полю афиши и проекции, созданному после завершения поиска на плоскости. Все, что нам нужно сделать, — это раскомментировать некоторый код, и этот сценарий выполнит следующие действия:
1. Определить, помещается ли голограмма на поверхность, райкастинг от центра и четырех углов ограничивающего Куба.
2. Проверьте нормальную поверхность, чтобы определить, достаточно ли она для записи на голограмму.
3. Отрисовка ограничивающего Куба вокруг голограммы для отображения ее фактического размера во время размещения.
4. Приведите тень в разделе/позади голограммы, чтобы узнать, где она будет размещена на этаже или стене.
5. Отрисовывает тень как красный, если она не может быть размещена на поверхности или зеленого, если это возможно.
6. Измените ориентацию голограммы так, чтобы она выработала с типом поверхности (вертикально или горизонтально), с которым он имеет сходство.
7. Плавно размещайте голограмму на выбранной поверхности, чтобы избежать появления или привязки.

Раскомментируйте весь код в приведенном ниже упражнении кода или используйте это законченное решение в **Placeable.CS**:

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**Сборка и развертывание**
* Как и ранее, выполните сборку проекта и разверните его в HoloLens.
* Дождитесь завершения проверки и обработки данных пространственного сопоставления.
* Когда появится Солнечная система, Взгляните на поле проекции ниже и выполните жест выбора, чтобы его переместить. Пока выбрано поле проекции, ограничивающий куб будет виден вокруг поля проекции.
* Переместите заголовку, чтобы Взгляните на другое место в комнате. Поле проекции должно следовать за вашим взглядом. Когда тень под полем проекции становится красным, вы не сможете поместить голограмму на этой поверхности. Когда тень под полем проекции становится зеленой, можно поместить голограмму, выполнив другой жест выбора.
* Найдите и выберите один из holographic-афиш на стене, чтобы переместить его в новое место. Обратите внимание, что вы не можете поместить афишу в этаж или потолк и правильно ориентироваться на каждую стену по мере движения.

## <a name="chapter-5---occlusion"></a>Глава 5-перекрытия

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Служит**
* Определить, перекрыто ли голограмма в сетке пространственных сопоставлений.
* Применение различных методов перекрытия для достижения привлекательного воздействия.

**Водим**

Во первых, мы собираемся разрешить сетке пространственных сопоставлений окклуде другие голограммы без окклудинг реального мира:
* На панели **Иерархия** выберите объект **спатиалпроцессинг** .
* На панели **инспектора** найдите компонент **диспетчер пространства воспроизведения (script)** .
* Щелкните окружность справа от свойства **дополнительного материала** .
* Найдите и выберите материал **перекрытия** и закройте окно.

Далее мы добавим к земле особое поведение, чтобы оно выглядело синим цветом, когда он станет перекрыто другой голограммой (например, солнце) или сеткой пространственного сопоставления:
* На панели « **проект** » в папке « **голограммы** » разверните объект **соларсистем** .
* Щелкните **Земля**.
* На панели **инспектора** найдите материал земли (нижний компонент).
* В раскрывающемся списке **шейдер**замените шейдер на **Custom > окклусионрим**. Это приведет к отображению синего выделения вокруг земли всякий раз, когда он перекрыто другим объектом.

Наконец, мы будем включать результат концепции x-ray для планет в нашей солнечной системе. Для достижения следующих целей необходимо изменить **PlanetOcclusion.CS** (находится в папке скриптс\соларсистем).
1. Определите, перекрыто ли Планета на уровне Спатиалмаппинг (сеток и плоскостей комнаты).
2. Отображение каркасного представления планеты, когда она перекрыто слоем Спатиалмаппинг.
3. Скрыть каркасное представление планеты, если оно не заблокировано слоем Спатиалмаппинг.

Выполните упражнения по написанию кода в PlanetOcclusion.cs или используйте следующее решение:

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**Сборка и развертывание**
* Создайте и разверните приложение в HoloLens, как обычно.
* Дождитесь завершения проверки и обработки данных пространственного сопоставления (на стены должны отобразиться синие линии).
* Найдите и выберите поле проекция солнечной системы, а затем установите флажок рядом с простенкой или за счетчиком.
* Вы можете просмотреть базовые перекрытия, скрывая поверхности к узлу в виде афиши или проекции.
* Взгляните на земле. при переходе на другую голограмму или поверхность должен быть выделен синий цвет.
* Следите за тем, как планеты перемещаются позади стены или других поверхностей комнаты. Теперь у вас есть концепция x-ray и видна их каркасы.

## <a name="the-end"></a>Конец

Поздравляем! Теперь вы завершили **MR 230: Пространственное**сопоставление.
* Вы узнаете, как проверить среду и загрузить данные пространственного сопоставления в Unity.
* Вы понимаете основы шейдеров и то, как можно использовать материалы для повторного визуализации мира.
* Вы узнали о новых методах обработки для поиска плоскостей и удалении треугольников из сетки.
* Вы смогли переместить и разместить голограммы на поверхностях, имеющих смысл.
* Вы столкнулись с различными методами перекрытия и использовали преимущества концепции x-ray!
