---
title: Модель приложения
description: Смешанная реальность Windows использует модель приложения, предоставляемые на универсальную платформу Windows, модели и среды для современных приложений Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, модель приложения, жизненный цикл, приостановка, возобновление, плитки, представления и контракты
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602999"
---
# <a name="app-model"></a>Модель приложения

Смешанная реальность Windows использует модель приложения, предоставляемые [универсальной платформы Windows](https://docs.microsoft.com/windows/uwp/get-started/) (UWP), модели и среды для современных приложений Windows. Модель приложения универсальной платформы Windows определяет, как приложения, установленные, обновленный, управление версиями и удалять безопасно, а полностью. Оно определяет жизненного цикла приложения — как приложения execute, переходили в спящий режим и завершить - и как они могут сохранять состояние. Здесь также рассматриваются интеграции и взаимодействия с операционной системы, файлы и другие приложения.

![2D приложений в Windows Mixed Reality домашней области завтрак](images/20160112-055908-hololens-500px.jpg)<br>
*Приложений с помощью двухмерное упорядочены в Windows Mixed Reality home*

## <a name="app-lifecycle"></a>Жизненный цикл приложения

Жизненный цикл приложения смешанной реальности включает в себя стандартное приложение концепции, такие как размещения, запуска, завершения и удаления.

### <a name="placement-is-launch"></a>Размещение по запуска

Каждое приложение запускается в смешанной реальности, поместив появляется Плитка приложения (только что [вторичная Плитка Windows](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) в [Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md). Эти плитки приложения на размещение, начнет выполнение приложения. Эти плитки приложений сохраняются и остаются в расположении, где они размещаются, выступающий в средствах запуска в любое время, вам необходимо вернуться в приложение.

![Размещение помещает вторичная Плитка в мире](images/slide1-600px.png)<br>
*Размещение помещает вторичная Плитка в мире*

Как только завершится размещения (Если размещение не была запущена [приложения в приложение](app-model.md#protocols) запуска), запуске приложения. Windows Mixed Reality одновременно выполнять ограниченный набор приложений. Как только вы разместить и запустить приложение, может приостановить других активных приложений, оставляя снимок состояния последнего приложения на его плитку приложения, везде, где он помещен. См. в разделе [жизненный цикл приложений Windows 10 UWP](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) Дополнительные сведения об обработке резюме и других событий жизненного цикла приложения.

![После помещения плитки, когда приложение запускается под управлением](images/slide2-500px.png) ![Диаграмма состояний для приложения, работающие, приостановленные или не запущена](images/ic576232-500px.png)<br>
*Слева: после помещения плитки, приложение запускается под управлением. Справа: Диаграмма состояний для приложения, работающие, приостановленные или не работает.*

### <a name="remove-is-closeterminate-process"></a>Удаление — закрытие или завершение процесса

При удалении плитки экземпляров размещенного приложения из мира, лежащие в основе процедуры закрыты. Это может быть полезно для убедитесь, что приложения прерывается или перезапуска проблемных приложений.

### <a name="app-suspensiontermination"></a>Приложение приостановки или остановки

В [Windows Mixed Reality домашней](navigating-the-windows-mixed-reality-home.md), пользователь не сможет создать несколько точек входа для приложения. Это делается путем запуска приложения из меню "Пуск" и помещения плитку приложения в мире. Каждая плитка приложения ведет себя как точку входа для другой и в системе есть экземпляр отдельные плитки. Запрос для [SecondaryTile.FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) приведет к **SecondaryTile** для каждого экземпляра приложения.

При приостановке приложения универсальной платформы Windows, снимок экрана взят текущего состояния.

![Снимки экрана для приостановленных приложений](images/slide9-800px.png)<br>
*Снимки экрана для приостановленных приложений*

Одно из основных отличий от других оболочек Windows 10 — как приложение получает сведения о активации экземпляра приложения с помощью [CoreApplication.Resuming](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) и [CoreWindow.Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) события.

|  Сценарий |  Возобновление  |  Активировано | 
|----------|----------|----------|
|  Запустите новый экземпляр приложения из меню "Пуск"  |   |  **Активировать** с новым [идентификатор TileId](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Запустите второй экземпляр приложения из меню "Пуск"  |   |  **Активировать** с новым **идентификатор TileId** | 
|  Выберите экземпляр приложения, которое не является активным  |   |  **Активировать** с **идентификатор TileId** связанный с экземпляром | 
|  Выберите другое приложение, а затем выберите ранее активный экземпляр  |  **Возобновление** возникает  |  | 
|  Выберите другое приложение, а затем выберите экземпляр, который был ранее неактивные  |  **Возобновление** возникает  |  Затем **Activated** с **идентификатор TileId** связанный с экземпляром | 

### <a name="extended-execution"></a>Расширенного выполнения

Иногда приложение должно продолжать работу в фоновом режиме или воспроизведения аудио. [Фоновые задачи](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) доступны на HoloLens.

![Приложения могут работать в фоновом режиме](images/slide10-800px.png)<br>
*Приложения могут работать в фоновом режиме*

## <a name="app-views"></a>Представления приложения

При активации приложения, можно выбрать, какой тип представления вы хотите отобразить. Для приложения **CoreApplication**, всегда есть основной [представлении приложения](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) и любым количеством дальнейшей представления приложения, вы хотите создать. На рабочем столе можно считать приложение представления окна. Наши шаблоны приложения смешанной реальности Создание проекта Unity, где основное приложение представления [иммерсивных](app-views.md). 

Приложения можно создать представление дополнительного 2D приложения с помощью технологии, как XAML, чтобы использовать функции Windows 10, такие как Покупка из приложения. Если приложение запущено как приложение универсальной платформы Windows для других устройств Windows 10, основного представления является двухмерной, но вы может «загораться» в смешанной реальности, добавив иммерсивных Показать интерфейс volumetrically представление дополнительных приложений. Предположим, создается приложение просмотра фотографий в XAML, где кнопка показа слайдов переключение иммерсивные приложения, летный фотографии из приложения по всему миру, а поверхности.

![Запущенное приложение может иметь двухмерное или иммерсивных представление](images/slide3-800px.png)<br>
*Запущенное приложение может иметь двухмерное или иммерсивных представление*

### <a name="creating-an-immersive-view"></a>Создание мощных представления

Приложения смешанной реальности те, которые Создание мощных Просмотр достигается за счет [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) типа.

Приложения, которое предназначено исключительно иммерсивных всегда следует создать иммерсивных представление при запуске, даже если запускается с рабочего стола. Насыщенные представления всегда отображаются в гарнитуры, независимо от того, где они были созданы из. Активация создавать впечатляющие представление отображает портале смешанной реальности и помочь пользователю, поместить на их гарнитуры.

Приложение, которое начинается с двухмерное на настольный монитор может создать вторичное представление иммерсивных для отображения содержимого в гарнитуры. Примером этого является окном 2D Edge на мониторе, отображающего видеозапись 360 градусов в гарнитуры.

![Приложения, работающие в режиме иммерсивных имеет только видимым](images/slide4-800px.png)<br>
*В приложении, работающем в иммерсивных представлении является единственным видимым*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Двухмерном виде в Windows Mixed Reality home

Ничего, кроме создавать впечатляющие представление отображается как двухмерное в ваш мир.

Приложение может иметь 2D представлений на настольный монитор и в гарнитуры. Обратите внимание, что новое представление 2D будут помещены в этот же интерпретатор команд как представления, создавшего его, либо на мониторе, либо в гарнитуры. Он не поддерживается в настоящее время для приложения или пользователя для перемещения двухмерное между домашней смешанной реальности и монитор.

![Приложения, работающие в двухмерное пространство в смешанной среде обмениваться с другими приложениями](images/slide5-800px.png)<br>
*Приложения, работающие в двухмерное пространство обмениваться с другими приложениями*

### <a name="placement-of-additional-app-tiles"></a>Размещение плиток дополнительных приложений

Вы можете разместить много приложений с двухмерной просмотра в свой мир с [дополнительный API-интерфейсы плитки](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles). Эти плитки «закрепленные» будет отображаться как экраны-заставки, что пользователям необходимо разместить и затем можно использовать для запуска приложения. Смешанная реальность Windows сейчас не поддерживает отрисовки 2D плитки содержимое в качестве живых плиток.

![Приложения могут иметь несколько размещения, используя вспомогательные плитки](images/slide6-800px.png)<br>
*Приложения могут иметь несколько размещения, используя вспомогательные плитки*

### <a name="switching-views"></a>Переключение представлений

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Переключение в представлении XAML 2D в иммерсивных представление

Если приложение использует XAML, а затем XAML [IFrameworkViewSource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) будет контролировать первое представление приложения. Приложение необходимо переключиться в представление иммерсивных перед активацией **CoreWindow**, чтобы при запуске приложения непосредственно в подробная информация.

Используйте [CoreApplication.CreateNewView](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) и [ApplicationViewSwitcher.SwitchAsync](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) чтобы сделать его активным представлением.

> [!NOTE]
>* Не указывайте [ApplicationViewSwitchingOptions.ConsolidateViews](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) флаг **SwitchAsync** когда переключение в представлении XAML для иммерсивных представления или листа, который запустил приложение будет удален из мира.
>* **SwitchAsync** должен вызываться с помощью [Dispatcher](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) связанные с входящего переключения в представление.
>* Вам нужно будет **SwitchAsync** вернуться к представлению XAML, если вам нужно запустить виртуальный клавиатуры или активировать другое приложение.

![Приложения можно переключаться между 2D и иммерсивных представления](images/slide7-600px.png) ![после приложение переходит в это иммерсивных представление, исчезают смешанной среде и другие приложения](images/slide8-600px.png)<br>
*Слева: приложения можно переключаться между 2D и иммерсивных представление. Справа: когда приложение выходит в более впечатляющие представления, домашних и других приложений Windows Mixed Reality исчезают.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Переключение из иммерсивных представления обратно на клавиатуре представления XAML

Одна из основных причин для перехода вперед и назад между представлениями отображает клавиатуры в приложении смешанной реальности. Оболочка находится только может отображать системную клавиатуру, если в приложении отображаются двухмерном виде. Если приложению необходимо получить текстовое поле, он может предоставить настраиваемое представление XAML с помощью поля ввода текста, перейти к нему и затем переключиться обратно после завершения ввода.

Как и в предыдущем разделе, можно использовать **ApplicationViewSwitcher.SwitchAsync** переход обратно в представление XAML из иммерсивных представления.

## <a name="app-size"></a>Размер приложения

Представления 2D приложения всегда отображаются в основных виртуальных баннер. Это делает все 2D представления Показать точно такого же объема содержимого. Ниже приведены некоторые дополнительные сведения о размер представления 2D вашего приложения.
* Соотношение сторон приложения сохраняется при изменении размера.
* Приложение [разрешения и масштаб фактор](building-2d-apps.md#2d-app-view-resolution-and-scale-factor) , не изменяются при изменении размера.
* Приложения не смогут запрашивать их фактического размера в мире.

![2D приложения отображаются с размерами основного окна](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Приложения с двухмерное, отображаются с размерами основного окна*

## <a name="app-tiles"></a>Плитки приложения

Меню "Пуск" использует стандартный маленькая Плитка и средняя Плитка для ПИН-кодов и **все приложения** списка в смешанной реальности. 

![Меню "Пуск" Windows Mixed Reality](images/start-500px.png)<br>
*Меню "Пуск" Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>Приложение для взаимодействия приложений

При построении приложений, у вас есть доступ к механизмы связи приложения в приложение с широкими возможностями, доступные в Windows 10. Многие из новых интерфейсов API протокола и регистрации файла работать идеально HoloLens для реализации запуска приложений и обмена данными. 

Обратите внимание, что для рабочего стола гарнитуры, приложения, связанный с указанным расширением файла или протокол может быть приложение Win32, который может использоваться только на настольный монитор или в содержание рабочего стола.

### <a name="protocols"></a>Протоколы

HoloLens поддерживает запуск приложения в приложение с помощью [Windows.System.Launcher API-интерфейсы](https://docs.microsoft.com/uwp/api/Windows.System.Launcher).

Есть несколько моментов, которые следует учитывать при запуске другого приложения:

* При выполнении запуска немодальном, такие как [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), установите приложение до взаимодействия с ним.

* При выполнении модальное запуска, например через [LaunchUriForResultsAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), модальное приложения помещается в верхней части окна.

* Windows Mixed Reality нельзя дополнительных приложений на основе эксклюзивные представлений. Чтобы можно было отобразить в запущенное приложение Windows направляет пользователя к системе для отображения приложения.

### <a name="file-pickers"></a>Выбор файла

HoloLens поддерживает как [FileOpenPicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) и [FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) контракты. Однако приложение не поставляется предварительно установленным, удовлетворяющего контрактами средства выбора файлов. Эти приложения — например, OneDrive — можно установить из Microsoft Store.

Если у вас установлено приложение выбора более одного файла, не появится неоднозначность пользовательского интерфейса по выбору какое приложение для запуска; Вместо этого будет выбран первый средства выбора файлов установки. При сохранении файла, создается имя файла, включая метку времени. Это не может изменяться пользователем.

По умолчанию локально поддерживаются следующие модули:

|  Приложение  |  Расширения | 
|----------|----------|
|  Фотографии  |  BMP, gif, jpg, png, avi, mov, mp4, wmv | 
|  Microsoft Edge  |  htm, html, pdf, svg, xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>Контракты и расширения Windows Mixed Reality приложений

Точки расширения и контракты приложения позволяют зарегистрировать свое приложение, чтобы воспользоваться преимуществами глубже функции операционной системы, такие как обработка расширение файла или с помощью фоновых задач. Это список поддерживаемых и неподдерживаемых контракты и расширения точки HoloLens.

|  Контракт или расширения  |  Поддерживается? | 
|----------|----------|
| [Поставщик изображений для учетной записи (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | Не поддерживается | 
| [оповещение](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | Не поддерживается | 
| [Службы приложений](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | Поддерживается, но не полностью функциональной | 
| [Поставщик встреч](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | Не поддерживается | 
| [Автозапуск (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | Не поддерживается | 
| [Фоновые задачи (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | Частично поддерживаемые (не все триггеры работают) | 
| [Обновление задачи (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | Поддерживается | 
| [Контракт средства обновления кэшированных файлов](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | Поддерживается | 
| [Параметры камеры (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | Не поддерживается | 
| [Протокол набора номера](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | Не поддерживается | 
| [Активации файла (расширения)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | Поддерживается | 
| [Контракт выбора открытых файлов](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | Поддерживается | 
| [Контракт выбора сохранения файла](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | Поддерживается | 
| [Вызов экрана блокировки](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | Не поддерживается | 
| [Воспроизведение мультимедиа](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | Не поддерживается | 
| [Воспроизвести на контракт](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | Не поддерживается | 
| [Предварительно установленные конфигурации задачи](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | Не поддерживается | 
| [Рабочий процесс трехмерной печати](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | Поддерживается | 
| [Параметры (расширение) печати](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | Не поддерживается | 
| [Активация URI (с расширением)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | Поддерживается | 
| [Ограниченный запуск](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | Не поддерживается | 
| [Контракт поиска](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | Не поддерживается | 
| [Контракт "Параметры"](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | Не поддерживается | 
| [Поделиться контрактом](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | Не поддерживается | 
| [SSL-сертификаты (расширения)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | Поддерживается | 
| [Учетная запись поставщика услуг](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | Поддерживается | 

## <a name="app-file-storage"></a>Хранилище файлов приложения

Все хранилище — через [пространства имен Windows.Storage](https://docs.microsoft.com/uwp/api/Windows.Storage). Обратитесь к следующей документации для получения дополнительных сведений. HoloLens не поддерживает хранилище синхронизации/перемещаемые приложений.

* [Файлы, папки и библиотеки](https://docs.microsoft.com/windows/uwp/files/index)
* [Хранение и извлечение параметров и прочих данных приложения](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Известные папки

См. в разделе [KnownFolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) полные сведения для приложений универсальной платформы Windows.

<table>
<tr>
<th> Свойство</th><th> Поддерживается в HoloLens</th><th> Поддерживается в иммерсивную</th><th> Описание</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Получает папку приложение регистрирует сведения.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Получает папку камеры.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">DocumentsLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает в библиотеку документов. Библиотека документов не предназначен для общего использования.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Получает библиотека музыки.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Получает папку трехмерных объектов.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Получает библиотека изображений.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Списки воспроизведения</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Получает папку списки воспроизведения.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Получает папку сохранения изображения.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Получает библиотеке видео.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">Домашней группы</a></td><td></td><td style="text-align: center;">✔️</td><td>Получает папку "Домашняя группа".</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Получает из папки сервера (Digital жил сети Требованиями) устройства.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>Получает папку записанных вызовов.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>Получает папку съемных устройств.</td>
</tr>
</table>

## <a name="app-package"></a>пакет приложения;

С Windows 10 вы больше не нацеливаться на операционную систему а [создавать приложения для одного или нескольких семейств устройств](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families). Семейство устройств определяет API-интерфейсы, характеристики системы и поведение, ожидаемые на устройствах внутри семейства. Он также определяет набор устройств, на которых приложения могут устанавливаться с [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Для рабочего стола гарнитуры и HoloLens, предназначенных для приложения, чтобы **Windows.Universal** семейства устройств.
* Чтобы ориентироваться только рабочего стола гарнитуры, предназначенных для приложения, чтобы **Windows.Desktop** семейства устройств.
* Чтобы ориентироваться только HoloLens, предназначенных для приложения, чтобы **Windows.Holographic** семейства устройств.

## <a name="see-also"></a>См. также

* [Представления приложения](app-views.md)
* [Обновление 2D uwp для смешанной реальности](building-2d-apps.md)
* [Руководство по проектированию приложения трехмерной запуска](3d-app-launcher-design-guidance.md)
* [Реализация средствах запуска приложений 3D](implementing-3d-app-launchers.md)
