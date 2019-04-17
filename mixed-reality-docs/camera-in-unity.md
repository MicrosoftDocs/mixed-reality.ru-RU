---
title: Камеры в Unity
description: Как использовать разработки Unity Main камеры для Windows Mixed Reality сделать holographic отрисовки
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, holographic отрисовки, точку фокуса holographic, создающий эффект присутствия, буфер глубины, ориентация только, позиционные, непрозрачный и прозрачный, клип
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597779"
---
# <a name="camera-in-unity"></a>Камеры в Unity

Когда приходится гарнитуры смешанной реальности, становится центре окружающего мира holographic. Unity [камеры](http://docs.unity3d.com/Manual/class-Camera.html) компонент автоматически обработает stereoscopic отрисовки и будет следовать перемещения и поворота при проект имеет «Виртуальной реальности поддерживается» выбрано с «Windows Mixed Reality» в качестве устройства ( Другие параметры раздел Параметры проигрывателя Windows Store). Это могут быть указаны как «Windows Holographic» в более старых версий Unity.

Тем не менее для полной оптимизации качества и [голограмма стабильность](hologram-stability.md), необходимо задать параметры камеры, описанных ниже.

>[!NOTE]
>Эти параметры должны применяться к камере в каждой сцены приложения.
>
>По умолчанию при создании новой сцены в Unity, он будет содержать объект GameObject камеры Main в иерархии, который включает компонент камеры, но не имеет параметров ниже надлежащим образом применяются.

## <a name="holographic-vs-immersive-headsets"></a>Holographic и иммерсивную

Параметры по умолчанию этот компонент Unity камеры используются для традиционных трехмерных приложений, которым требуется фона skybox по принципу, как у них нет реальном мире.
* При работе на  **[иммерсивных гарнитура](immersive-headset-hardware-details.md)**, выполняется подготовка к просмотру все, что видит пользователь, и таким образом вы скорее всего захотите сохранить skybox.
* Тем не менее при работе на **holographic гарнитура** как [HoloLens](hololens-hardware-details.md), реальный мир должен отображаться за все камеры подготавливает к просмотру. Чтобы сделать это, Меняем цвет фона камеры прозрачным (в HoloLens, черный подготавливает к просмотру как прозрачный) вместо текстуры Skybox:
    1. Выберите Main Camera на панели «иерархии»
    2. На панели Инспектора найти компонент камеры и измените в раскрывающемся списке снимите флажки с Skybox на сплошным цветом
    3. Выберите палитру цветов фона и измените значения RGBA (0, 0, 0, 0)

Код сценария можно использовать для определения во время выполнения гарнитура иммерсивных или holographic путем проверки [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).


## <a name="positioning-the-camera"></a>Размещение камеры

Упростить процесс для создания приложения Если imagine Начальная позиция пользователя как (X: 0, Y: 0, Z: 0). Поскольку Main Camera отслеживает перемещение головы пользователя, задавая начальное положение Main Camera можно задать начальную позицию пользователь.
1. Выберите Main Camera на панели «иерархии»
2. На панели Инспектора найти компонент преобразования и изменить позицию, начиная с (X: 0, Y: 1 -10 Z:) к (X: 0, Y: 0, Z: 0)

   ![Камеры в панели инспектора в Unity](images/maincamera-350px.png)<br>
   *Камеры в панели инспектора в Unity*

## <a name="clip-planes"></a>Обрезать плоскостей

Отображение содержимого слишком близко к пользователю можно вызвать беспокойство в смешанной реальности. Вы можете настроить [практически, а также гораздо обрезать плоскостей](hologram-stability.md#hologram-render-distances) в компоненте камеры.
1. Выберите Main Camera на панели «иерархии»
2. На панели Инспектора найдите плоскостей компонента обрезки камеры и измените практически текстовое поле с 0.3 для.85. Содержимое отображается еще ближе может привести к discomfort пользователя следует избегать использования каждого [визуализации расстояние рекомендации](hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Несколько камеры

При наличии нескольких компонентов камеры в сцене, Unity знает, какая камера, используемый для отрисовки stereoscopic и головной отслеживания, установив какие GameObject имеет MainCamera тега.

## <a name="recentering-a-seated-experience"></a>Recentering за кресло качества

Если вы создаете [сидели высококлассные возможности](coordinate-systems.md), вы можете origin world центровку Unity в текущем положении головной пользователя путем вызова **[XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** метод.

## <a name="reprojection-modes"></a>Режимы reprojection

HoloLens и иммерсивную будет reproject каждого кадра, приложение выполняет визуализацию с учетом любой неверным прогнозированием действительную позицию головной пользователя при photons создаются.

По умолчанию:

* **Иммерсивную** выполнит позиционные reprojection, настраивая ваш голограммы для неверным прогнозированием в положение и ориентацию, в том случае, если приложение предоставляет буфер глубины для заданного кадра.  Если буфер глубины не указан, система только исправит исполнениями в ориентации.
* **Holographic гарнитуры** как HoloLens выполнит позиционные reprojection ли приложение предоставляет свой буфер глубины или нет.  Позиционные reprojection невозможен без буферов глубины на HoloLens, как отрисовки часто является разреженным фоне стабильной, предоставляемый реальной жизни.

Если вы знаете, что вы создаете [только для ориентации интерфейс](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) с содержимым на строго заблокирован для текста (например 360 градусов видеосодержимого), можно явно задать режим reprojection, который должен быть ориентация только заданием [ HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) для [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Общий доступ к вашей буферов глубины с Windows

Совместное использование буфер глубины вашего приложения для Windows, каждого кадра даст приложения один из двух повышает стабильность голограмма, в зависимости от типа гарнитура отрисовки для:
* **Иммерсивную** позиционные reprojection можно выполнить, если буфер глубины, настройка вашей голограммы для неверным прогнозированием в положение и ориентацию.
* **Holographic гарнитуры** как HoloLens автоматически выберет [сосредоточиться точки](focus-point-in-unity.md) если буфер глубины, оптимизация голограмма стабильности плоскости, которая пересекает больше всего содержимого.

Чтобы указать режим буфер глубины предоставит вашим приложением Unity для Windows:
1. Перейдите к **изменить** > **параметры проекта** > **проигрывателя** > **вкладке универсальной платформы Windows**  >  **XR параметры**.
2. Разверните **смешанной реальности SDK Windows** элемента.
3. Установите или снимите флажок **разрешить общий буфер глубины** "флажок".  Это будет проверяться по умолчанию в новых проектах, создан, так как эта функция была добавлена к Unity и будет снят по умолчанию для более старых проектов, которые были обновлены.

Предоставляя буфер глубины для Windows может повысить качество изображения, до тех пор, пока Windows может точно сопоставить значения глубины нормализованное каждого пикселя в свой буфер глубины к расстояния в метрах, с использованием ближней и дальней плоскости, который вы задали в Unity на главной камеры.  Если вашей визуализации передает дескриптор глубины значения в типичных задач, обычно можно здесь, на то, что Полупрозрачный отрисовки передает, которые выполняют запись в буфер глубины во время отображения на существующие цвета пикселей может запутать reprojection нормально.  Если вы знаете, что ваши визуализации передает оставит многие ваши окончательный глубину точек со значениями неточные глубины, вы, скорее всего, для получения повышения качества изображения, сняв флажок «Включить глубина буфера общий доступ».

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a>Настройка автоматического сцены смешанной реальности из набора средств
При импорте [Unity пакеты выпуска MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) или клонируйте проект со страницы [репозиторий GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), нужно найти новое меню «Смешанной реальности Toolkit» в Unity. В меню «Настройка» вы увидите меню «Применить смешанной реальности сцены параметры». Если щелкнуть его, он удаляет камеры по умолчанию и добавляет основных компонентов — [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), и [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Меню MRTK для установки сцены](images/MRTK_Input_Menu.png)<br>
*Меню MRTK для установки сцены*

![Настройка автоматического сцены в MRTK](images/MRTK_HowTo_Input1.png)<br>
*Настройка автоматического сцены в MRTK*

## <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefab
Их можно также вручную добавить из панели «проект». Эти компоненты можно найти как prefabs. При поиске **MixedRealityCamera**, можно увидеть два различных камеры prefabs. Разница в том, **MixedRealityCamera** только в том случае камеры prefab в то время как **MixedRealityCameraParent** включает дополнительные компоненты для иммерсивную, например Teleportation движения Контроллер и границ.

![Плоскости камеры MRTK](images/MRTK_HowTo_Input2.png)<br>
*Плоскости камеры MRTK*

**MixedRealtyCamera** поддерживает HoloLens и иммерсивных гарнитуры. Он определяет тип устройства и оптимизирует такие свойства как очистить флаги и Skybox. Далее представлены некоторые полезные свойства можно настроить, например пользовательский курсор, контроллер движения модели и Floor.

![Свойства для контроллера движения курсора и Floor](images/MRTK_HowTo_Input3.png)<br>
*Свойства для контроллера движения курсора и Floor*

## <a name="see-also"></a>См. также
* [Голограмма стабильность](hologram-stability.md)
* [Camera.prefab MixedRealityToolkit Main](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
