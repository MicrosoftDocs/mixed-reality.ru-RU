---
title: Пакет SDK для понимания сцены
description: Инструкции по программированию для пакета SDK для сцены
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: Основные сведения о сцене, пространственное сопоставление, Windows Mixed Reality, Unity
ms.openlocfilehash: 88138622987800ff86a24d05e1308e694e2dd2b1
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/10/2019
ms.locfileid: "68941241"
---
## <a name="scene-understanding-sdk-overview"></a>Общие сведения о пакете SDK для сцены

Цель «понимание сцены» состоит в том, чтобы преобразовать неструктурированные данные датчика среды, записанные устройством смешанной реальности, и преобразовать их в эффективное, но абстрактное представление, которое интуитивно понятно и легко разрабатывается для. Пакет SDK выступает в качестве коммуникационного уровня между приложением и сцены среды выполнения. Он предназначен для имитации существующих стандартных конструкций, таких как графики трехмерных сцен для трехмерных представлений и двумерных прямоугольников и панелей для двумерных приложений. Хотя сцены конструкций понимают, что имитирует сопоставление с конкретными платформами, которые можно использовать, в целом Сценеундерстандинг является независимым от платформы и обеспечивает взаимодействие между различными платформами, которые взаимодействуют с ним. По мере того, как в сцене понимается развитие роли пакета SDK, мы видим, что новые представления и возможности по-прежнему будут доступны в единой инфраструктуре. В этом документе мы сперва предложим основные понятия, которые помогут вам ознакомиться с средой разработки и использованием, а затем предоставить более подробную документацию по конкретным классам и конструкциям.

## <a name="where-do-i-get-the-sdk"></a>Где получить пакет SDK?

Пакет SDK для Сценеундерстандинг загружается через NuGet.

[Пакет SDK для Сценеундерстандинг](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

Прежде чем начать, обратите внимание, что пакет SDK выполняется поверх UWP и требует Windows SDK версии 18362 или более поздней. 

### <a name="the-scene"></a>Сцена

Устройство Mixed Reality постоянно интегрирует информацию о том, что она видит в вашей среде. При понимании сцены создаются все эти источники данных и создается одна единая абстракция. Понятие "сцена" создает сцены, представляющие собой композицию [сценеобжектс](scene-understanding-SDK.md#sceneobjects) , которая представляет экземпляр одной вещи (например, стены, потолка или этажа). Сами объекты сцены являются композицией [сценекомпонентс](scene-understanding-SDK.md#scenecomponents) , представляющей более детализированные элементы, составляющие этот сценеобжект. Примерами компонентов являются четыре и сетки, но в будущем они могут представлять ограничивающие рамки, конфликты мехсес, метаданные и т. д.

Процесс преобразования необработанных данных датчика в сцену является потенциально дорогостоящей операцией, которая может занять секунды для средних пробелов (~ 10x10m) в минутах для очень больших пробелов (~ 50x50m) и, следовательно, не будет вычисляться устройством без запрос приложения. Вместо этого создание сцены активируется вашим приложением по запросу. Класс Сценеобсервер содержит статические методы, которые могут вычислять или десериализовать сцену, которые затем можно перечислить или взаимодействовать с. Действие "вычисление" выполняется по требованию и выполняется в ЦП, но в отдельном процессе (драйвер Mixed Reality). Однако, пока мы выполняем вычисление в другом процессе, полученные данные сцены сохраняются и обслуживаются в приложении в объекте сцены. 

Ниже приведена схема, на которой показан этот поток процесса, и приведены примеры двух приложений, взаимодействующих с сценой выполнения. 

![Схема процесса](images/SU-ProcessFlow.png)

В левой части находится схема среды выполнения Mixed Reality, которая всегда включена и выполняется в собственном процессе. Эта среда выполнения отвечает за выполнение отслеживания устройств, а также воспроизводить и другие операции, которые помогут понять, что в мире используется для понимания и причины вокруг всего мира. В правой части схемы показаны два теоретических приложения, которые используют понимание сцены. Первое приложение взаимодействует с МРТК, которое использует для внутренних целей пакет SDK, второе приложение выполняет вычисление и использует два экземпляра сепереате сцены. Все три сцены на этой схеме создают отдельные экземпляры сцен, драйвер не отслеживает глобальное состояние, которое совместно используется приложениями, а объекты сцены в одной сцене не находятся в другой. Понимание сцены обеспечивает механизм отслеживания по времени, но это делается с помощью пакета SDK и кода. код, который выполняет это отслеживание, выполняется в пакете SDK в процессе приложения.

Поскольку каждый монтажный кадр хранит данные в памяти приложения, можно предположить, что все функции объекта сцены или внутренние данные всегда выполняются в процессе приложения.

#### <a name="layout"></a>Макет

Чтобы работать с сценами, полезно знать и понять, как среда выполнения представляет компоненты логически и физически. Сцена представляет данные с определенным макетом, который был выбран для простоты при сохранении базовой структуры, плиабле в соответствии с будущими требованиями, не требуя значительных изменений. Сцена делает это, сохраняя все компоненты (стандартные блоки для всех объектов сцены) в плоском списке и определяя иерархию и композицию с помощью ссылок, где определенные компоненты ссылаются на другие.

Ниже представлен пример структуры как в плоской, так и в логической форме.

<table>
<tr><th>Логический макет</th><th>Физический макет</th></tr>
<tr>
<td>
<ul>
  Сцены
  <ul>
  <li>SceneObject_1
    <ul>
      <li>Mesh_1</li>
      <li>Quad_1</li>
      <li>Quad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>Quad_1</li>
      <li>Quad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>Mesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>Quad_1</li>
  <li>Quad_2</li>
  <li>Quad_3</li>
  <li>Mesh_1</li>
  <li>Mesh_2</li>
</ul>
</td>
</tr>
</table>

На этом рисунке показана разница между физическим и логическим макетом сцены. Справа мы видим иерархический макет данных, отображаемых приложением при перечислении сцены. Слева видно, что сцена на деле состоит из 12 отдельных компонентов, доступных по отдельности при необходимости. При обработке новой сцены мы предполагаем, что приложения будут логически проходить эту иерархию, однако при отслеживании обновлений сцены некоторые приложения могут заинтересовать только те компоненты, которые являются общими для двух сцен.

### <a name="high-level-overview"></a>Общие сведения о высоком уровне

В следующем разделе представлен общий обзор конструкций в представлении сцены. В этом разделе вы узнаете, как представлено представление сцены, а также о том, для чего используются различные компоненты. В следующем разделе приводятся конкретные примеры кода и дополнительные сведения, которые будут включены в этот обзор.

#### <a name="scenecomponents"></a>сценекомпонентс

Теперь, когда вы понимаете логическую структуру сцен, теперь можно представить концепцию Сценекомпонентс и то, как они используются для создания иерархии. Сценекомпонентс — это наиболее детализированные декомпозиции в Сценеундерстандинг, представляющие одну основную вещь, например сетку или четырехъядерный прямоугольник. Сценекомпонентс — это вещи, которые могут обновляться независимо друг от друга и на которые могут ссылаться другие Сценекомпонентс, поэтому у них есть одно глобальное свойство с уникальным идентификатором, разрешающее этот тип механизма отслеживания и создания ссылок. Идентификаторы используются для логической композиции иерархии сцены, а также для сохранения объектов (действия по обновлению одной сцены относительно другой). 

Если все недавно вычисленные сцены обрабатываются как разные, и просто перечисление всех данных в нем, идентификаторы в значительной степени прозрачны. Однако если вы планируете отслеживание компонентов по нескольким обновлениям, вы будете использовать идентификаторы для индексирования и поиска Сценекомпонентс между объектами сцены.

#### <a name="sceneobjects"></a>сценеобжектс

Сценеобжект — это Сценекомпонент, представляющий экземпляр "вещи", например стены, этаж, потолк и т. д. выражается по свойству Kind. Сценеобжектс являются геометрическими и, следовательно, имеют функции и свойства, представляющие их расположение в пространстве, однако они не содержат геометрическую или логическую структуру. Вместо этого Сценеобжектс ссылаться на другие Сценекомпонентс, в частности Сценекуадс и Сценемешес, которые предоставляют различные представления, поддерживаемые системой. При вычислении новой сцены приложение, скорее всего, будет перечислять Сценеобжектс сцены, чтобы обработать его интерес.

Сценеобжектс может иметь одно из следующих:

<table>
<tr>
<th>сценеобжекткинд</th> <th>Описание</th>
</tr>
<tr><td>Фон</td><td>Известно, что Сценеобжект <b>не</b> является одним из других распознаваемых видов объекта сцены. Этот класс не следует путать с неизвестным, где фон может не быть стенным, этажным, потолком и т. д. Хотя эта категория неизвестна, она еще не классифицирована.</b></td></tr>
<tr><td>Брандмауэр</td><td>Физическая стенка. Предполагается, что стены являются неперемещаемыми структурами окружающей среды.</td></tr>
<tr><td>Фабрич</td><td>Полs — это любые поверхности, на которых может пройти один проход. Примечание. лестницы не являются этажами. Кроме того, обратите внимание, что в этом этаже предполагается любая неанализируемойная поверхность и, следовательно, нет явного предположений в единственном этаже. Многоуровневые структуры, пандуси и т. д. Все категории должны классифицироваться как пол.</td></tr>
<tr><td>Толок</td><td>Верхняя поверхность комнаты.</td></tr>
<tr><td>Платформа</td><td>Крупная плоская поверхность, на которую можно поместить голограммы. Они обычно представляют таблицы, каунтертопс и другие крупные горизонтальные поверхности.</td></tr>
<tr><td>World</td><td>Зарезервированная метка для геометрических данных, не зависящая от меток. Сетка, созданная путем установки флага обновления Енаблеворлдмеш, будет классифицироваться как мир.</td></tr>
<tr><td>Неизвестно</td><td>Этот объект сцены еще не классифицирован и ему назначен тип. Это не следует путать с фоном, так как этот объект может быть любым, система просто не поступила с достаточной классификацией.</td></tr>
</tr>
</table>

#### <a name="scenemesh"></a>SceneMesh

Сценемеш — это Сценекомпонент, который приблизительно отражает геометрию произвольных геометрических объектов с помощью списка треугольников. Сценемешес используются в нескольких разных контекстах, они могут представлять компоненты структуры ячеек ватертигхт или в виде Ворлдмеш, представляющего неограниченную реконструкции поверхности, связанную с сценой. Данные индекса и вершины, предоставляемые в каждой сетке, используют тот же привычный макет, что [и буферы вершин и индексов](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) , которые используются для отрисовки сеток треугольников во всех современных API-интерфейсах отрисовки. Обратите внимание, что в сцене основные сведения об использовании сеток используют 32-разрядные индексы, и их необходимо разбить на фрагменты для определенных механизмов визуализации.

#### <a name="scenequad"></a>сценекуад

Сценекуад — это Сценекомпонент, представляющий двумерные поверхности, занимающие трехмерный мир. Сценекуадс можно использовать аналогично ARKit Арпланеанчор или Аркоре плоскости, но они предлагают более высокоуровневые функции, такие как двумерные холсты для использования в неструктурированных приложениях или дополненные UX. для четырех массивов предусмотрены двумерные API, которые делают размещение и разметку простыми в использовании, а разработка (за исключением отрисовки) с четырьмя областями должна быть более похожей на работу с плоскими холстами, чем с трехмерными сетками.

### <a name="scene-understanding-sdk-details-and-reference"></a>Сцены сведения о пакете SDK и справочнике

#### <a name="sdk"></a>SDK

Следующий раздел поможет вам ознакомиться с основами Сценеундерстандинг. В этом разделе приводятся основные сведения, в которых вы должны получить достаточно контекста для просмотра примеров приложений, чтобы увидеть, как Сценеундерстандинг используется глобально.

#### <a name="initialization"></a>Инициализация

Первым шагом для работы с Сценеундерстандинг является получение ссылки на объект сцены в приложении. Это можно сделать одним из двух способов: сцена может вычисляться драйвером, или существующая сцена, которая была вычислена в прошлом, может быть десериализована. Последнее особенно полезно для работы с Сценеундерстандинг во время разработки, где приложения и опыт можно быстро создавать прототипы без устройства смешанной реальности.

Сцены вычисляются с помощью Сценеобсервер. Перед созданием сцены приложение должно запросить устройство, чтобы убедиться, что оно поддерживает Сценеундерстандинг, а также запросить доступ пользователей для получения информации, которая необходима Сценеундерстандинг.

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Если не вызывается Рекуестакцессасинк (), то Вычисление новой сцены завершится ошибкой. Далее мы вычислим новую сцену, которая находится в корне вокруг гарнитуры смешанной реальности и имеет 10-м радиус.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.Compute(querySettings, 10.0f);
```

#### <a name="initialization-from-data-aka-the-pc-path"></a>Инициализация из данных (т. е. Путь к компьютеру)

В то время как сцены можно вычислять для прямого потребления, их также можно вычислить в сериализованной форме для последующего использования. Это оказалось очень полезным для разработки, так как позволяет разработчикам работать и тестировать сцены без необходимости использования устройства. Процесс сериализации сцены практически идентичен его вычислению, поэтому данные возвращаются в приложение, а не десериализуется локально с помощью пакета SDK. Вы можете выполнить десериализацию самостоятельно или сохранить его для будущего использования.

```cs
// Create Query settings for the scene update
SceneUnderstanding.QuerySettings querySettings;

// Compute a scene but serialized as a byte array
byte[] newSceneBlob = SceneObserver.ComputeSerialized(querySettings, 10.0f);

// If we want to use it immediatley we can de-serialize the scene ourselves
Scene mySceneDeSerialized = Scene.Deserialize(newSceneBlob);

// Save newSceneBlob for later
```

#### <a name="sceneobject-enumeration"></a>Перечисление Сценеобжект

Теперь, когда приложение содержит сцену, приложение будет искать и взаимодействовать с Сценеобжектс. Это делается путем обращения к свойству **сценеобжектс** :

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

#### <a name="component-update-and-re-finding-components"></a>Обновление компонентов и их повторное обнаружение

Существует другая функция, извлекающая компоненты в сцене с именем ***финдкомпонент***. Эта функция полезна при обновлении объектов отслеживания и их поиске в последующих сценах. Следующий код вычислит новую сцену относительно предыдущей сцены, а затем найдет этаж в новой сцене.

```cs
// Compute a new scene, but tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.Compute(querySettings, 10.0f, myScene);

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attatched to this floor transform
}
```

### <a name="accessing-meshes-and-quads-from-scene-objects"></a>Доступ к сеткам и четырем из объектов сцены

После обнаружения Сценеобжектс приложение, скорее всего, захочет получить доступ к данным, содержащимся в этих объемах. Доступ к этим данным осуществляется с помощью свойств « ***четыре*** » и « ***сетки*** ». Следующий код будет перечислять все четыре и сетки нашего объекта Floor.

```cs

// Get the matrix for the SceneObject
System.Numerics.Matrix4x4 floorTransform = firstFloor.LocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Обратите внимание, что это Сценеобжект, который имеет преобразование относительно начала сцены. Это обусловлено тем, что Сценеобжект представляет экземпляр "вещь" и размещаемые в пространстве, а четыре части и сетки представляют геометрию, которая преобразуется относительно родительской. Можно использовать отдельный Сценеобжектс для ссылки на один и тот же Сценемеш или Сценекуад Сценекомпоневнтс. Кроме того, возможно, что у Сценеобжект есть более одного Сценемеш/Сценекуад.

### <a name="dealing-with-transforms"></a>Работа с преобразованиями

Понимание сцены предоставило намеренную попытку выполнить согласование с традиционными представлениями трехмерной сцены при работе с преобразованиями. Таким образом, каждая сцена ограничена одной системой координат, похожей на наиболее распространенные трехмерные представления среды. Если ваше приложение работает с монтажными кадрами, которые претягивают ограничение на один источник, можно привязать Сценеобжектс к Спатиаланчорс или создать несколько сцен и объединить их вместе, но для простоты предполагается, что ватертигхт сцены существуют самостоятельно. Источник, локализованный с помощью одного NodeId, определенного сценами:: Оригинспатиалграфнодеид.

В следующем примере кода Unity показано, как использовать восприятие Windows и API Unity для совмещения систем координат:


```cs
    public static System.Numerics.Matrix4x4? GetSceneToUnityTransform(Guid nodeId)
    {
        System.Numerics.Matrix4x4? sceneToUnityTransform; 
       
        SpatialCoordinateSystem sceneSpatialCoordinateSystem = Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(nodeId);
        SpatialCoordinateSystem unitySpatialCoordinateSystem = (SpatialCoordinateSystem)System.Runtime.InteropServices.Marshal.GetObjectForIUnknown(UnityEngine.XR.WSA.WorldManager.GetNativeISpatialCoordinateSystemPtr());

        sceneToUnityTransform = sceneSpatialCoordinateSystem.TryGetTransformTo(unitySpatialCoordinateSystem);

        if (sceneToUnityTransform != null)
        {
            sceneToUnityTransform = TransformUtils.ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
        }
        
        return sceneToUnityTransform;
    }

    // Converts from right-handed to left handed coordinates
    public System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 transformationMatrix)
    {
        transformationMatrix.M13 = -transformationMatrix.M13;
        transformationMatrix.M23 = -transformationMatrix.M23;
        transformationMatrix.M43 = -transformationMatrix.M43;

        transformationMatrix.M31 = -transformationMatrix.M31;
        transformationMatrix.M32 = -transformationMatrix.M32;
        transformationMatrix.M34 = -transformationMatrix.M34;

        return transformationMatrix;
    }
```

И следующий код вызывает эту функцию:

```cs
System.Numerics.Matrix4x4? sceneToUnityTransform = TransformUtils.GetSceneToUnityTransform(scene.OriginSpatialGraphNodeId);

// Set the root transform
Vector3 t;
Quaternion r;
Vector3 s;

System.Numerics.Matrix4x4.Decompose(sceneToUnityTransform, out s, out r, out t);
SceneRoot.Transform.SetPositionAndRotation(t, r);
```

### <a name="quad"></a>Четырехъядерный

Четыре из них были разработаны для упрощения сценариев размещения 2D-файлов и должны рассматриваться как расширения для элементов UX в двумерных холстах. Хотя четыре компонента являются компонентами Сценеобжектс и могут быть визуализированы в трехмерном виде, четыре интерфейса API предполагают, что четыре структуры являются 2D-структурами. Они предлагают такие сведения, как экстент, форма и предоставление API для размещения.

Четыре имеют прямоугольные экстенты, но они представляют собой произвольные геоповерхности. Чтобы включить размещение на этих 2D-поверхностях, взаимодействующих с четырьмя трехмерными средами, можно использовать служебные программы для обеспечения этого взаимодействия. В настоящее время понятие сцены предоставляет две такие функции: **финдцентермостплацемент** и **жетокклусионмаск**. Финдцентермостплацемент — это интерфейс API высокого уровня, который определяет положение на самом большом месте, где может быть размещен объект, и пытается найти лучшее место для объекта, гарантируя, что ограничивающий прямоугольник будет находиться на базовой поверхности.

В следующем примере показано, как найти центермост место и привязать голограмму к четырем.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new node QuadTransformNode as a child of Root, and set the transform from quad[0].Transform
                // Step 2: Create your hologram and set it as a child of QuadTransformNode
                // Step 3: Set the QuadTransformNode tranform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

Шаги 1-3 сильно зависят от конкретной платформы или реализации, но темы должны быть похожи. Важно отметить, что четыре обычно не предназначены, просто представляет ограниченную двухмерную плоскость, локализованную в пространстве. Так как ваш модуль или платформа знает, где четыре – и в корне объекты находятся по сравнению с четырьмя, самые голограммы будут размещены правильно. Для получения более подробных сведений ознакомьтесь с нашими примерами на четырех, которые демонстрируют конкретные реализации.

### <a name="mesh"></a>Сетчат

Сетки представляют геометрические представления объектов или сред. Подобно [пространственному](spatial-mapping.md)сопоставлению, индекс сетки и данные вершин, предоставляемые каждой сетке пространственных областей, используют тот же привычный макет, что и буферы вершин и индексов, которые используются для отрисовки сеток треугольников во всех современных API-интерфейсах отрисовки. Ниже перечислены конкретные API-интерфейсы, используемые для ссылки на эти данные.

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(float[] vertices);
```

\* * Примечание. Метод onвершины возвращает список вершин, каждый из трех кортежей значений с плавающей запятой которых представляет одну координату в координатах x, y и z.

В следующем коде приведен пример создания списка треугольников из структуры сетки.

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
float[] positions = new float[mesh.VertexCount * 3];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

Буферы индексов и вершин должны быть > = количество индексов или вершин, но в противном случае можно изменить размер произвольного размера, допуская эффективное использование памяти.

### <a name="developing-with-scene-understandings"></a>Разработка с использованием сцен

На этом этапе вы должны понимать основные строительные блоки сцены, посвященные среде выполнения и пакету SDK. Многие возможности и сложность основаны на шаблонах доступа, взаимодействии с трехмерными платформами и средствах, которые могут быть написаны поверх этих API для выполнения более сложных задач, таких как пространственное планирование, анализ комнаты, навигация, физика и т. д. Мы надеемся, что они записываются в примеры, которые будут надеяться вам в правильном направлении. Если у вас есть образцы или сценарии, которые мы не используем, сообщите нам, и мы попытаемся попытаться документировать или обменять нужные объекты.

## <a name="see-also"></a>См. также

* [пространственное сопоставление](spatial-mapping.md)