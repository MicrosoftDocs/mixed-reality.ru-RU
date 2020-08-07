# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

Unity позволяет создать кроссплатформенное полнофункциональное приложение смешанной реальности. См. статью [Обзор разработки в Unity](../unity-development-overview.md), чтобы приступить к разработке в Unity для HoloLens или иммерсивных гарнитур Windows Mixed Reality.

## <a name="what-does-unity-offer"></a>Что предлагает Unity?

Unity — это одна из ведущих платформ разработки в реальном времени с обширной экосистемой, в которую входят специализированная [платформа обучения](https://unity.com/products/learn-premium), [магазин ресурсов](https://assetstore.unity.com/), [полный пакет документации](https://docs.unity3d.com/Manual/index.html) и активное сообщество. Базовый код выполнения Unity написан на C++, но все скрипты создаются на C#. Независимо от того, какие задачи вам нужно выполнять (создавать игры, синематику для фильмов и анимации или даже визуализировать архитектурные либо инженерные концепции в виртуальном мире), Unity предоставит вам необходимую инфраструктуру.

## <a name="available-hardware-platforms"></a>Доступные аппаратные платформы

Для создания приложений смешанной реальности с помощью Unity есть несколько вариантов оборудования и эмуляторов. Хотя в нашей документации для разработчиков в основном описывается устройство HoloLens, вы также можете найти разделы поддержки для устройств с подробными сведениями о развертывании для иммерсивных гарнитур (если это применимо).

**Устройства дополненной реальности**
* [HoloLens (1-го поколения)](https://docs.microsoft.com/hololens/hololens1-hardware)
* [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)

**Иммерсивные гарнитуры виртуальной реальности**
* HP Reverb и Reverb G2
* Samsung Odyssey и Odyssey+
* Гарнитура HP Windows Mixed Reality
* Lenovo Explorer
* Acer AH101
* Dell Visor
* Asus HC102
* Acer OJO 500

## <a name="available-tools-and-sdks"></a>Доступные инструменты и пакеты SDK

|  Инструмент или пакет SDK  |  Описание  |
| --- | --- |
| [Набор средств для смешанной реальности для Unity](../mrtk-getting-started.md) | Набор средств для смешанной реальности для Unity — это кросс-платформенный набор разработки с открытым кодом, который ускоряет создание приложений, предназначенных для Microsoft HoloLens, иммерсивных гарнитур виртуальной реальности Windows Mixed Reality и платформы OpenVR. |

## <a name="examples"></a>Примеры

Мы предлагаем несколько [примеров приложений](../samples.md) с открытым кодом, которые вы можете скачать и протестировать, чтобы лучше понять, как выглядит конечный продукт смешанной реальности в Unity. Кроме того, вы можете воспользоваться примерами сцен в MRTK для тестирования определенных функций:
* [Пример сцены с взаимодействием с помощью рук (MRTK) для Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#open-and-run-the-handinteractionexamples-scene-in-editor) — пример сцены HandInteractionExamples.unity содержит различного вида взаимодействия и элементы управления пользовательского интерфейса, выделяемые при вводе с помощью рук.

* [Примеры с отслеживанием глаз (MRTK) для Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_ExamplesOverview.html) — на этой странице объясняется, как быстро приступить к работе с отслеживанием движений глаз с помощью соответствующих примеров в MRTK.

>[!NOTE]
>Для работы с обоими примерами сцен MRTK необходимо установить пакет MRTK Foundation и пакет примеров Unity.

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

Unity позволяет создать кросс-платформенное полнофункциональное приложение смешанной реальности с помощью движка Unreal. См. сведения о [разработке Unreal для HoloLens](../unreal-development-overview.md).

## <a name="what-does-unreal-offer"></a>Что предлагает Unreal?

Unreal Engine 4 — это мощная подсистема разработки с открытым кодом, обладающая полной поддержкой смешанной реальности в C++ и Blueprints. Начиная с версии Unreal Engine 4.25, поддержка HoloLens считается полной и пригодной для рабочей среды.

## <a name="available-hardware-platforms"></a>Доступные аппаратные платформы

Для создания приложений смешанной реальности с помощью Unreal Engine есть несколько вариантов оборудования, эмуляторов и потоковой передачи. В нашей документации для разработчиков в основном описываются устройства HoloLens, но вы можете упаковывать проекты Unreal как классические приложения x64 и просто запускать их на иммерсивных гарнитурах.

**Устройства дополненной реальности**
* [HoloLens (1-го поколения)](https://docs.microsoft.com/hololens/hololens1-hardware)
* [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)

**Иммерсивные гарнитуры виртуальной реальности**
* HP Reverb и Reverb G2
* Samsung Odyssey и Odyssey+
* Гарнитура HP Windows Mixed Reality
* Lenovo Explorer
* Acer AH101
* Dell Visor
* Asus HC102
* Acer OJO 500

## <a name="available-tools-and-sdks"></a>Доступные инструменты и пакеты SDK

|  Инструмент или пакет SDK  |  Описание  |
| --- | --- |
| [Набор средств для смешанной реальности для Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) | Набор средств смешанной реальности для Unreal (MRTK-Unreal) представляет собой набор таких компонентов, как подключаемые модули, примеры и документы, созданных для ускорения разработки приложений смешанной реальности с использованием Unreal Engine. |


# <a name="web"></a>[Интернет](#tab/web)

![Интернет](../images/javascript_logo_banner.png)

API устройства WebXR — это открытая спецификация, которая позволяет работать с приложениями смешанной реальности в браузере на любой платформе. Сведения о том, как создавать приложения смешанной реальности для любой платформы, см. в [обзоре разработки на Javascript](../javascript-development-overview.md).


# <a name="native-openxr"></a>[Нативные решения (OpenXR)](#tab/native)

 ![Собственный](../images/native_logo_banner.png)

Создавайте приложения смешанной реальности, непосредственно используя интерфейсы API Windows Mixed Reality. Сведения о том, как создавать нативные приложения с помощью OpenXR или старой версии WinRT для иммерсивных гарнитур HoloLens 2 или Windows Mixed Reality см. в [обзоре разработки с помощью нативных инструментов](../directx-development-overview.md). API Windows Mixed Reality поддерживает приложения, написанные на C++ и C#. Это позволяет создать собственную платформу или ПО промежуточного слоя на любом из этих языков.

## <a name="what-does-openxr-offer"></a>Что предлагает OpenXR?

OpenXR — это открытый бесплатный стандарт API от Khronos, который предоставляет возможности нативного доступа к широкому спектру устройств от поставщиков решений смешанной реальности. Вы можете разрабатывать приложения, используя OpenXR с HoloLens 2 или иммерсивную гарнитуру Windows Mixed Reality с компьютером. Если у вас нет гарнитуры, доступны эмуляторы для гарнитур HoloLens 2 и Windows Mixed Reality.

## <a name="available-hardware-platforms"></a>Доступные аппаратные платформы

Для создания приложений смешанной реальности с помощью OpenXR есть несколько вариантов оборудования, эмуляторов и потоковой передачи. 

**Устройства дополненной реальности**
* [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)

**Иммерсивные гарнитуры виртуальной реальности**
* HP Reverb и Reverb G2
* Samsung Odyssey и Odyssey+
* Гарнитура HP Windows Mixed Reality
* Lenovo Explorer
* Acer AH101
* Dell Visor
* Asus HC102
* Acer OJO 500

## <a name="available-tools-and-sdks"></a>Доступные инструменты и пакеты SDK

|  Инструмент или пакет SDK  |  Описание  |
| --- | --- |
| [Средства разработчика OpenXR](../openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) | Содержит сцену с демонстрацией различных функций OpenXR, а также страницу "Состояние системы", которая предоставляет важную информацию о текущей среде выполнения и текущей гарнитуре. |
| [Спецификация OpenXR](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html) |  Здесь объясняется, что собой представляет OpenXR, описаны возможности и функции этого API, а также указаны способы его реализации в проектах. |
| [Загрузчик OpenXR](../openxr-getting-started.md#integrate-the-openxr-loader-into-a-project) | Обнаруживает активную среду выполнения OpenXR на устройстве и предоставляет доступ к основным функциям и реализуемым функциям расширений. |

## <a name="examples"></a>Примеры

Протестируйте пример приложения, чтобы лучше понять, какие возможности вам доступны при использовании нативных средств разработки и средств разработки для смешанной реальности.

<!-- Go to actual GH link for more samples -->
* [BasicXrApp](https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp) демонстрирует простой пример OpenXR с двумя файлами проекта Visual Studio — для классического приложения Win32 и для приложения UWP HoloLens 2.