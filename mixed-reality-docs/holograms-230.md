---
title: Пространственный MR 230 - пространственное сопоставление
description: Выполните кодирование Пошаговое руководство по использованию Unity, Visual Studio и HoloLens пространственное сопоставление понятий подробные сведения.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, учебник, пространственное сопоставление, восстановления на поверхности, сетки
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993561"
---
>[!NOTE]
>Учебники Academy реальности Mixed были разработаны с HoloLens (1-го поколения) и смешанной реальности Иммерсивную в виду.  Таким образом мы думаем, что это важно, чтобы эти учебники на месте для разработчиков, которые по-прежнему необходимы сведения при разработке приложений для этих устройств.  Эти руководства будут **_не_** дополняться последние наборы инструментов или взаимодействия, используемых для HoloLens 2.  Они будут сохранены, чтобы продолжить работу на поддерживаемых устройствах. Будет существовать новую серию учебников, которые будут опубликованы в будущем, демонстрируют способ разработки для HoloLens 2.  Это уведомление будет обновляться со ссылкой на эти руководства, когда они учитываются.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR пространственных 230: Пространственное сопоставление

[Пространственное сопоставление](spatial-mapping.md) объединяет реального мира и виртуальный мир путем указания голограммы о среде. В пространственных 230 MR (проект планетарий) вы узнаете, как:

* Проверки среды и передачи данных из HoloLens на свой компьютер разработки.
* Изучите шейдеры и узнайте, как использовать их для визуализации модуля.
* Разделите место сетки в простой плоскости с помощью обработки сетки.
* Выйдите за рамки методики размещения, нам удалось выучить за [101 основы MR](holograms-101.md)и оставить отзыв о которой голограмма могут быть помещены в среде.
* Изучите эффекты перекрытия, поэтому если вашей голограмма находится за реальным объектом, его можно по-прежнему просматривать с рентгеновское зрение!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Поддержка устройств

<table>
<tr>
<th>Курс</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Иммерсивную</a></th>
</tr><tr>
<td>MR пространственных 230: Пространственное сопоставление</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Прежде чем начать

### <a name="prerequisites"></a>предварительные требования

* ПК Windows 10, настроены с правильным [установлены средства](install-the-tools.md).
* Основные C# возможности программирования.
* Необходимо завершить [101 основы MR](holograms-101.md).
* Устройство HoloLens [настроенных для разработки для](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Файлы проекта

* Скачайте [файлы](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) требуемые для проекта. Требуется компонент Unity 2017.2 или более поздней версии.
  * Если вам по-прежнему требуется поддержка Unity 5.6, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Если вам по-прежнему требуется поддержка Unity 5.5, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Если вам по-прежнему требуется поддержка Unity 5.4, используйте [этого выпуска](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Удаление архива файлы рабочего стола или других легко положения.

>[!NOTE]
>Если вы хотите просмотреть исходный код перед загрузкой, он имеет [на сайте GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Примечания

* «Включить только мой код» в Visual Studio, необходимо отключить (*unchecked*) в разделе Сервис > Параметры > Отладка для точки останова в коде.

## <a name="unity-setup"></a>Программа установки Unity

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Запуск **Unity**.
* Выберите **New** для создания нового проекта.
* Назовите проект **планетарий**.
* Убедитесь, что **3D** выбран параметр.
* Нажмите кнопку **Создание проекта**.
* После запуска Unity перейдите на **изменить > Параметры проекта > проигрывателя**.
* В **инспектор** панели найдите и выберите зеленый **Windows Store** значок.
* Разверните **другие параметры**.
* В **визуализации** установите флажок **поддерживается виртуальной реальности** параметр.
* Убедитесь, что **Windows Holographic** появится в списке **виртуальной реальности SDK**. Если это не так, выберите **+** кнопку в нижней части списка и выберите **Windows Holographic**.
* Разверните **Настройка публикации**.
* В **возможности** раздела, проверьте следующие параметры:
    * internetClientServer
    * privateNetworkClientServer
    * Микрофон
    * SpatialPerception
* Перейдите к **изменить > Параметры проекта > качества**
* В **инспектор** панели под значком Windows Store, выберите черной стрелкой раскрывающегося списка под строкой «Default» и измените значение параметра по умолчанию на **очень низкий**.
* Перейдите к **ресурсы > Импорт пакета > пользовательского пакета**.
* Перейдите к **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** папки.
* Щелкните **Planetarium.unitypackage**.
* Нажмите кнопку **Открыть**.
* **Импорт пакета Unity** должно появиться окно, щелкните **импорта** кнопки.
* Дождитесь Unity импортировать все ресурсы, которые требуется для выполнения этого проекта.
* В **иерархии** панели, удалите **Main Camera**.
* В **проекта** панели **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** папки, найти **Main Camera** объекта.
* Перетаскивание **Main Camera** prefab в **иерархии** панели.
* В **иерархии** панели, удалите **направленный свет** объекта.
* В **проекта** панели **голограммы** папки, найдите **курсор** объекта.
* Перетаскивание **курсор** prefab в **иерархии**.
* В **иерархии** панели, выберите **курсор** объекта.
* В **инспектор** панели, щелкните **слой** раскрывающегося списка и выберите **слои изменить...** .
* Имя **слой пользовательского 31** как "**SpatialMapping**«.
* Сохраните новую сцену: **Файл > Сохранить сцену как...**
* Нажмите кнопку **новую папку** и назовите папку **сцены**.
* Назовите файл «**планетарий**"и сохраните его в **сцены** папки.

## <a name="chapter-1---scanning"></a>Глава 1 - сканирование

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Цели**
* Сведения о SurfaceObserver и как она влияет на параметры взаимодействия и производительности.
* Создайте комнату, проверку качества для сбора сетки комнате.

**Инструкции**
* В **проекта** панели **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** папки, найти **SpatialMapping** prefab.
* Перетаскивание **SpatialMapping** prefab в **иерархии** панели.

**Построение и развертывание (часть 1)**
* В Unity, выберите **файл > Параметры сборки**.
* Нажмите кнопку **добавьте откройте сцены** добавление **планетарий** сцены в сборке.
* Выберите **универсальной платформы Windows** в **платформы** списке и нажмите кнопку **переключить платформу**.
* Задайте **SDK** для **универсальной 10** и **тип сборки UWP** для **D3D**.
* Проверьте **Unity C# проекты**.
* Щелкните **Сборка**.
* Создание **новую папку** с именем «Приложение».
* Одним щелчком мыши **приложения** папки.
* Нажмите клавишу **Выбор папки** кнопки.
* После завершения Unity построения, появится окно проводника.
* Дважды щелкните **приложения** папку, чтобы открыть его.
* Дважды щелкните **Planetarium.sln** загрузить проект в Visual Studio.
* В Visual Studio, использовать верхней панели инструментов для изменения конфигурации для **выпуска**.
* Изменение платформы на **x86**.
* Щелкните стрелку раскрывающегося списка справа от «Локальный компьютер» и выберите **удаленный компьютер**.
* Введите [IP-адрес вашего устройства](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) в адресе и измените режим проверки подлинности, **универсальный (незашифрованный протокол)**.
* Нажмите кнопку **Отладка -> Запуск без отладки** или нажмите клавишу **Ctrl + F5**.
* Контрольные значения **вывода** панели в Visual Studio для сборки и состояние развертывания.
* Когда приложение развернуто, сильна комнате. Вы увидите окружающей поверхности, охваченных черно-белый каркас сеток.
* Сканировать обстановке. Убедитесь, что рассмотрим стены, максимальных и пол.

**Построение и развертывание (часть 2)**

Теперь давайте рассмотрим, как пространственных сопоставление может повлиять на производительность.
* В Unity, выберите **окна > Profiler**.
* Нажмите кнопку **добавьте Profiler > GPU**.
* Нажмите кнопку **Active Profiler > <Enter IP>** .
* Введите **IP-адрес** из вашей HoloLens.
* Нажмите кнопку **Подключить**.
* Наблюдайте за время в миллисекундах, необходимое для графического Процессора для подготовки к просмотру кадр.
* Остановите запуск на устройстве приложений.
* Вернитесь в Visual Studio и откройте **SpatialMappingObserver.cs**. Вы найдете его в папке HoloToolkit\SpatialMapping проекта сборки-CSharp (универсальной Windows).
* Найти **Awake()** и добавим следующий код: **TrianglesPerCubicMeter = 1200;**
* Повторно разверните проект на устройстве, а затем **повторного подключения профилировщика**. Понаблюдайте за изменением количество миллисекунд для подготовки к просмотру кадр.
* Остановите запуск на устройстве приложений.

**Сохранить и загрузить в Unity**

Наконец сохраните наших место сетки и загрузить их в Unity.
* Вернитесь в Visual Studio и удаление **TrianglesPerCubicMeter** строки, который был добавлен в **Awake()** функции во время предыдущего раздела.
* Повторно разверните проект на устройство. Мы теперь выполняется с **500** треугольники за третьего метр.
* Откройте браузер и введите в вашей HoloLens IP-адрес для перехода к **Windows Device Portal**.
* Выберите **объемного вида** параметр на панели слева.
* В разделе **область реконструкции** выберите **обновления** кнопки.
* Посмотрите, как области, которые проверены на вашей HoloLens отображаются в окне просмотра.
* Чтобы сохранить место проверки, нажмите клавишу **Сохранить** кнопки.
* Откройте ваш **Скачивает** папку, чтобы найти сохраненные комнаты модель **SRMesh.obj**.
* Копировать **SRMesh.obj** для **активы** папку проекта Unity.
* В Unity, выберите **SpatialMapping** объекта в **иерархии** панели.
* Найдите **наблюдателя поверхность объекта (скрипт)** компонента.
* Щелкните этот кружок справа от **модели комнаты** свойство.
* Найдите и выберите **SRMesh** объекта, а затем закройте окно.
* Убедитесь, что **модели комнаты** свойство в **инспектор** панели теперь настроен для **SRMesh**.
* Нажмите клавишу **воспроизведение** кнопку, чтобы перейти в режим предварительного просмотра Unity.
* Компонент SpatialMapping загрузит сетки из сохраненного комнаты модели, их можно использовать в Unity.
* Переключиться в режим **сцены** представление, чтобы увидеть все модели комнаты отображаются с шейдером, каркасной модели.
* Нажмите клавишу **воспроизведение** кнопку еще раз, чтобы выйти из режима предварительного просмотра.

**ПРИМЕЧАНИЕ.** Следующий раз, что режим предварительного просмотра в Unity, выполняется загрузка сохраненного место сетки по умолчанию.

## <a name="chapter-2---visualization"></a>Глава 2 - визуализации

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Цели**
* Ознакомиться с основами шейдеров.
* Визуализация обстановке.

**Инструкции**
* В Unity **иерархии** панели, выберите **SpatialMapping** объекта.
* В **инспектор** панели, найти **пространственных Manager сопоставления (скрипт)** компонента.
* Щелкните этот кружок справа от **материала поверхности** свойство.
* Найдите и выберите **BlueLinesOnWalls** материал и закройте окно.
* В **проекта** панели **шейдеры** папки, дважды щелкните **BlueLinesOnWalls** для открытия шейдеров в Visual Studio.
* Это простой пиксель (вершины фрагментировать) шейдера, который выполняет следующие задачи:
    1. Преобразует вершины расположение в абсолютном пространстве.
    2. Проверяет, что вершины могут определить, является ли пикселя по вертикали.
    3. Задает цвет пикселя для подготовки к просмотру.

**Создание и развертывание**
* Вернуться к Unity и нажмите клавишу **воспроизведение** в режим предварительного просмотра.
* Синие линии отображаются на всех поверхностях вертикальной сетки комнаты (который автоматически загружается из наших сохраненные данные сканирования).
* Переключиться в режим **сцены** tab, чтобы настроить отображение комнаты и увидите, как отображается сетка всего места в Unity.
* В **проекта** панели, найти **материалы** папку и выберите **BlueLinesOnWalls** материал.
* Изменить некоторые свойства и увидеть, как изменения отображаются в редакторе Unity.
    * В **инспектор** панели, Настройка **LineScale** значение, чтобы сделать толще или более тонкие линии.
    * В **инспектор** панели, Настройка **LinesPerMeter** значение изменение количества строк на каждую стену.
* Нажмите кнопку **воспроизведение** еще раз, чтобы выйти из режима предварительного просмотра.
* Построение и развертывание для HoloLens и наблюдать, как отображается шейдера отрисовки на реальном поверхностях.

Unity выполняет большую работу Предварительный просмотр материалов, но настоятельно рекомендуется извлечения отрисовка в устройство.

## <a name="chapter-3---processing"></a>Глава 3 - обработки

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Цели**
* Ознакомьтесь с приемами для обработки пространственное сопоставление данных для использования в приложении.
* Анализ пространственное сопоставление данных для поиска плоскости и удалить треугольники.
* Используйте плоскостей голограмма размещения.

**Инструкции**
* В Unity **проекта** панели **голограммы** папки, найти **SpatialProcessing** объекта.
* Перетаскивание **SpatialProcessing** в коллекцию **иерархии** панели.

SpatialProcessing prefab включает в себя компоненты для обработки данных пространственное сопоставление. **SurfaceMeshesToPlanes.cs** найдет и создать на основе данных пространственное сопоставление плоскости. Мы будем использовать плоскостей в нашем приложении для представления стены, пол и перекрытия. Также включает этот prefab **RemoveSurfaceVertices.cs** которого можно удалить вершины из пространственное сопоставление сети. Это можно использовать для создания бреши в системе в сети или чтобы удалить лишние треугольники, которые больше не требуются (поскольку плоскости можно использовать вместо этого).
* В Unity **проекта** панели **голограммы** папки, найти **SpaceCollection** объекта.
* Перетаскивание **SpaceCollection** в коллекцию **иерархии** панели.
* В **иерархии** панели, выберите **SpatialProcessing** объекта.
* В **инспектор** панели, найти **воспроизведения диспетчера пространства (скрипт)** компонента.
* Дважды щелкните **PlaySpaceManager.cs** чтобы открыть его в Visual Studio.

PlaySpaceManager.cs содержит код для конкретного приложения. Мы добавим функциональность в этот сценарий, чтобы включить следующее поведение:
1. Остановите процесс сбора данных пространственное сопоставление, после превышения сканирования ограничение времени (10 секунд).
2. Процесс сопоставления пространственных данных:
    1. Используйте SurfaceMeshesToPlanes для создания простой представление мира в виде плоскости (стены, пол, максимальных и т. д).
    2. С помощью RemoveSurfaceVertices удалить поверхности треугольники, которые попадают в границы плоскости.
3. Создает коллекцию голограммы в мире и помещает их на стене и floor плоскостей рядом с пользователем.

Завершите упражнений по кодированию помечены в PlaySpaceManager.cs или замените скрипт готового решения из приведенных ниже:

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

**Создание и развертывание**
* Перед развертыванием в HoloLens, нажмите клавишу **воспроизведение** кнопки в Unity, чтобы перейти в режим воспроизведения.
* После загрузки сетки комнаты из файла, подождите 10 секунд, до начала обработки на сетке пространственное сопоставление.
* По завершении обработки плоскостей будет отображаться для представления floor, стены, ceiling, и т.д.
* В конце концов из плоскостей нет, вы должны увидеть Солнечная система отображаются в таблице floor рядом с камеры.
* Два плакаты слишком появится на стене, рядом с камеры. Переключиться в режим **сцены** вкладку, если они не видны в **игру** режим.
* Нажмите клавишу **воспроизведение** кнопку еще раз, чтобы выйти из режима play.
* Создание и развертывание в HoloLens, как обычно.
* Дождитесь завершения сканирования и обработки данных пространственное сопоставление для завершения.
* Как только вы увидите плоскости, попробуйте найти Солнечной системы и плакаты в ваш мир.

## <a name="chapter-4---placement"></a>Глава 4 – размещения

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Цели**
* Определите, если голограмма помещается в рабочей области.
* Предоставить отзыв пользователя когда голограмма могут или не помещаются в рабочей области.

**Инструкции**
* В Unity **иерархии** панели, выберите **SpatialProcessing** объекта.
* В **инспектор** панели, найти **поверхности сетки на плоскости (скрипт)** компонента.
* Изменение **рисования плоскостей** свойства **Nothing** чтобы снять выделение.
* Изменение **рисования плоскостей** свойства **стены**, так что отображается только по часам плоскости.
* В **проекта** панели **сценарии** папки, дважды щелкните **Placeable.cs** чтобы открыть его в Visual Studio.

**Placeable** сценарий уже присоединен к плакаты и поле проекции, созданные после завершения поиск плоскости. Нам нужно сделать всего лишь раскомментируйте код, и этот сценарий позволяет достичь следующих:
1. Определите, если голограмма может поместиться на рабочую область, точные точки для отслеживания из центра и четырех углов ограничивающего куба.
2. Проверьте обычные для определения того, является достаточно smooth для голограмма зафиксированных ставятся в рабочей области.
3. Отображать ограничивающий куб вокруг голограмма, чтобы показывать его фактический размер во время помещения.
4. Уводят в тень в группе или отставать от голограмма, чтобы показать, где будет располагаться на floor/wall.
5. Отрисовки тени красным цветом, если она не могут размещаться на поверхности, и зеленым, если это возможно.
6. Получите новую ориентацию голограмма в соответствии с поверхности тип (вертикальные или горизонтальные), что он имеет сходство.
7. Плавно снабдить выбранную поверхность, чтобы избежать переход, привязывание голограмма.

Раскомментируйте весь код в фрагмент кода, или использовать это решение, завершенные в **Placeable.cs**:

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

**Создание и развертывание**
* Как и раньше постройте проект и разверните HoloLens.
* Дождитесь завершения сканирования и обработки данных пространственное сопоставление для завершения.
* Обнаружив Солнечной системы помощи на поле проекции ниже и выполните жест, выберите ее перенос. Во время проекции поле выбрано, ограничивающий куб будет отображаться вокруг поля проекции.
* Переместите head для помощи в другом месте в комнате. Поле проекции должен следовал за вашим взглядом. При тени под полем проекции станет красным, она не удается разместить в этой области. При тени под полем проекции станет зеленой, можно поместить голограмма путем выполнения другой выберите жест.
* Найдите и выберите один из holographic плакатов на стене, чтобы переместить его в новое расположение. Обратите внимание на то, что нельзя размещать плакат на floor и ceiling, и что он остается правильную ориентацию для каждой стенки при перемещении курсора.

## <a name="chapter-5---occlusion"></a>Глава 5 - перекрытия

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Цели**
* Определите, если голограмма является перекрыто по сетке пространственное сопоставление.
* Применить перекрытия различные способы достижения интересную эффект.

**Инструкции**

Во-первых мы собираемся разрешить сетке пространственное сопоставление, чтобы скрывать другие голограммы без occluding реального мира:
* В **иерархии** панели, выберите **SpatialProcessing** объекта.
* В **инспектор** панели, найти **воспроизведения диспетчера пространства (скрипт)** компонента.
* Щелкните этот кружок справа от **дополнительный материал** свойство.
* Найдите и выберите **перекрытия** материал и закройте окно.

Затем мы собираемся добавить специальное поведение для поверхности Земли, чтобы он включал синяя рамка, каждый раз, когда он становится перекрыто другой голограмма (например, sun) или пространственное сопоставление сети:
* В **проекта** на панели **голограммы** папку, разверните **SolarSystem** объекта.
* Щелкните **Earth**.
* В **инспектор** панели, где находится множество материалов Земли (нижней компонент).
* В **раскрывающегося списка шейдера**, измените шейдер для **Custom > OcclusionRim**. Это сделает синяя рамка вокруг Earth всякий раз, когда он является перекрыто другим объектом.

Наконец мы собираемся включить эффект концепции рентгеновский снимок для планет нашей Солнечной системы. Нам потребуется изменить **PlanetOcclusion.cs** (находится в папке Scripts\SolarSystem) для достижения следующих:
1. Определите, если планеты перекрыто уровнем SpatialMapping (место сетки и плоскости).
2. Показать представление каркас планеты, каждый раз, когда он является перекрыто уровнем SpatialMapping.
3. Скрыть каркас представлением планеты, когда она не заблокирована на уровне SpatialMapping.

Выполните фрагмент кода в PlanetOcclusion.cs или использовать следующее решение:

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

**Создание и развертывание**
* Создавайте и развертывайте приложения для HoloLens, как обычно.
* Дождитесь сканирования и обработки данных пространственное сопоставление завершения (вы увидите синие линии отображаются на стене).
* Найдите и выберите поле проекции Солнечной системы и задайте поле рядом с стене или за счетчика.
* Можно просмотреть основные перекрытия, скрытие за поверхности для узла в поле плакат или проекции.
* Найдите поверхности Земли, должно быть эффекта синяя рамка всякий раз, когда оно выходит за пределы другой голограмма или области.
* Следите за планеты переместить за wall или других областей в комнате. Теперь имеют рентгеновское зрение и можно увидеть их скелетов каркас!

## <a name="the-end"></a>Конец

Поздравляем! Вы завершили **пространственных 230 MR: Пространственное сопоставление**.
* Вы знаете, как выполнить проверку данных вашей среды и нагрузки пространственное сопоставление для Unity.
* Вы знакомы с основами преобразователей текстур и как материалы можно использовать для повторного визуализации мира.
* Вы узнаете о новые методы обработки для поиска плоскости и снятие сетки треугольников.
* Можно было переместить, и размещать голограммы на поверхности, в которые было уместно.
* Произошел другой перекрытия методов и использовали возможности рентгеновское зрение!
