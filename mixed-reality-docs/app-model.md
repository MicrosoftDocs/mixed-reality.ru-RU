---
title: Модель приложения
description: Windows Mixed Reality использует модель приложений, предоставляемую универсальная платформа Windows, модель и среду для современных приложений Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP, модель приложения, жизненный цикл, приостановка, возобновление, плитка, представления, контракты
ms.openlocfilehash: 5dc84122e591e7d91657b6f8eadf6eb947f2d706
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63517393"
---
# <a name="app-model"></a>Модель приложения

Windows Mixed Reality использует модель приложений, предоставляемую [универсальная платформа Windows](https://docs.microsoft.com/windows/uwp/get-started/) (UWP), модель и среду для современных приложений Windows. Модель приложения UWP определяет, как приложения устанавливаются, обновляются, изменяются и изменяются версиями и полностью удаляются. Он управляет жизненным циклом приложения: выполнение приложений, спящий режим и завершение работы, а также способ сохранения состояния. В нем также рассматривается интеграция и взаимодействие с операционной системой, файлами и другими приложениями.

![Двумерные приложения, расположенные на домашней странице Windows Mixed Reality в за завтраком области](images/20160112-055908-hololens-500px.jpg)<br>
*Приложения с плоским представлением, расположенным на домашней странице Windows Mixed Reality*

## <a name="app-lifecycle"></a>Жизненный цикл приложения

Жизненный цикл приложения смешанной реальности включает в себя стандартные концепции приложений, такие как размещение, запуск, завершение и удаление.

### <a name="placement-is-launch"></a>Размещение — запуск

Каждое приложение запускается в смешанной реальности путем размещения плитки приложения (только [вторичная плитка Windows](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)) на [домашней странице Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md). На этих плитках приложений при размещении будет запущено выполнение приложения. Эти плитки приложений сохраняются и остаются в расположении, где они размещены, так как запускаются в любое время, когда требуется вернуться к приложению.

![Размещение помещает вспомогательную плитку в мир](images/slide1-600px.png)<br>
*Размещение помещает вспомогательную плитку в мир*

Как только размещение завершается (если размещение не было запущено приложением при запуске [приложения](app-model.md#protocols) ), запускается запуск приложения. Windows Mixed Reality может одновременно запускать ограниченное количество приложений. После размещения и запуска приложения другие активные приложения могут приостановиться, при этом снимок экрана последнего состояния приложения помещается на плитку приложения в то место, куда вы поместили. Дополнительные сведения об обработке событий возобновления и других событиях жизненного цикла приложений см. в статье [жизненный цикл приложений UWP в Windows 10](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) .

![После размещения плитки приложение запускает](images/slide2-500px.png) ![схему состояния "запущено", "приостановлено" или "не запущено"](images/ic576232-500px.png)<br>
*Left: после размещения плитки приложение начинает работать. Справа: Схема состояний для приложения работает, приостановлена или не запущена.*

### <a name="remove-is-closeterminate-process"></a>Удаление является процессом закрытия или завершения

При удалении плитки размещенного приложения из мира закрывает базовые процессы. Это может быть полезно для того, чтобы гарантировать завершение работы приложения или перезапустить его.

### <a name="app-suspensiontermination"></a>Приостановка и завершение работы приложения

На [домашней странице Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)пользователь может создать несколько точек входа для приложения. Для этого нужно запустить приложение из меню "Пуск" и поместить плитку приложения в мир. Каждая плитка приложения ведет себя как другая точка входа и имеет отдельный экземпляр плитки в системе. Запрос для [секондаритиле. финдалласинк](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync) приведет к созданию **секондаритиле** для каждого экземпляра приложения.

При приостановке приложения UWP из текущего состояния берется снимок экрана.

![Отображаются снимки экрана для приостановленных приложений](images/slide9-800px.png)<br>
*Отображаются снимки экрана для приостановленных приложений*

Одним из ключевых отличий от других оболочек Windows 10 является то, как приложение сообщает об активации экземпляра приложения через события [CoreApplication. возобновляет](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) работу и [CoreWindow. Activated](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) .

|  Сценарий |  Возобновление  |  Активировано | 
|----------|----------|----------|
|  Запуск нового экземпляра приложения из меню "Пуск"  |   |  **Активировано** с помощью нового [тилеид](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId) | 
|  Запуск второго экземпляра приложения из меню "Пуск"  |   |  **Активировано** с помощью нового **тилеид** | 
|  Выберите экземпляр приложения, который сейчас не активен  |   |  **Активируется** с **тилеид** , связанным с экземпляром | 
|  Выберите другое приложение, а затем выберите ранее активный экземпляр  |  **Возобновление** вызвано  |  | 
|  Выберите другое приложение, а затем выберите экземпляр, который ранее был неактивен  |  **Возобновление** вызвано  |  Затем **активируется** с **тилеид** , связанным с экземпляром | 

### <a name="extended-execution"></a>Расширенное выполнение

Иногда приложению необходимо продолжить работу в фоновом или воспроизводимом аудио. [Фоновые задачи](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest) доступны в HoloLens.

![Приложения могут выполняться в фоновом режиме](images/slide10-800px.png)<br>
*Приложения могут выполняться в фоновом режиме*

## <a name="app-views"></a>Представления приложения

После активации приложения можно выбрать тип представления, которое вы хотите отобразить. Для **CoreApplication**приложения всегда существует основное [представление приложения](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) и любое количество дополнительных представлений приложений, которые вы хотите создать. На рабочем столе представление приложения можно представить как окно. Шаблоны приложений смешанной реальности создают проект Unity, в котором основное представление приложения является [иммерсивное](app-views.md). 

Приложение может создать дополнительное представление 2D-приложения с помощью таких технологий, как XAML, для использования таких функций Windows 10, как покупка в приложении. Если ваше приложение запущено как приложение UWP для других устройств Windows 10, основное представление является 2D-, но в смешанной реальности можно «поработать», добавив дополнительное представление приложения, которое покажет волуметрикалли. Представьте себе создание приложения для просмотра фотографий на языке XAML, в котором кнопка "показ слайдов" переключена на представление иммерсивного приложения, флев фотографии из приложения по всему миру и на поверхностях.

![Выполняющееся приложение может иметь 2D-представление или иммерсивное представление](images/slide3-800px.png)<br>
*Выполняющееся приложение может иметь 2D-представление или иммерсивное представление*

### <a name="creating-an-immersive-view"></a>Создание иммерсивного представления

Приложения смешанной реальности — это те, которые создают иммерсивное представление, которое достигается с помощью типа [холографикспаце](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) .

Приложение, которое является исключительно увлекательным, должно всегда создавать иммерсивное представление при запуске, даже если оно запускается с рабочего стола. Иммерсивное представление всегда отображается в гарнитуре, независимо от того, где они были созданы. При активации иммерсивного представления отобразится портал Mixed Reality и пошаговое указание пользователя на его гарнитуру.

Приложение, которое запускается с плоским представлением на настольном мониторе, может создать дополнительное иммерсивное представление для отображения содержимого на гарнитуре. Примером этого является окно с плоским ребром на мониторе, в котором отображается видео 360-градуса на гарнитуре.

![Приложения, выполняющиеся в режиме погружения, видимы только один](images/slide4-800px.png)<br>
*Приложение, работающее в режиме погружения, является единственным видимым*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>2D-представление на домашней странице Windows Mixed Reality

Все, что не является иммерсивное представление, подготавливается к просмотру как 2D-представление в мире.

Приложение может иметь 2D-представления как на настольном мониторе, так и на гарнитуре. Обратите внимание, что новое 2D-представление будет помещено в ту же оболочку, что и созданное им представление, либо на мониторе, либо на гарнитуре. В настоящее время приложение или пользователь не могут перемещать 2D-представление между домашней средой и монитором смешанной реальности.

![Приложения, работающие в двухмерном представлении, совместно используют пространство в смешанном мире с другими приложениями](images/slide5-800px.png)<br>
*Приложения, работающие в двухмерном представлении, совместно используют пространство с другими приложениями*

### <a name="placement-of-additional-app-tiles"></a>Размещение плиток дополнительных приложений

С помощью [вспомогательных API плиток](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)можно разместить любое количество приложений с плоским представлением в мире. Эти закрепленные плитки отображаются в виде экранов-заставок, которые пользователи должны располагать, а затем могут использоваться для запуска приложения. В настоящее время Windows Mixed Reality не поддерживает отрисовку содержимого 2D мозаики в виде динамических плиток.

![Приложения могут иметь несколько размещений с помощью дополнительных плиток](images/slide6-800px.png)<br>
*Приложения могут иметь несколько размещений с помощью дополнительных плиток*

### <a name="switching-views"></a>Переключение представлений

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>Переключение из 2D-представления XAML в иммерсивное представление

Если приложение использует XAML, [IFRAMEWORKVIEWSOURCE](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) XAML будет управлять первым представлением приложения. Приложению потребуется перейти в иммерсивное представление перед активацией **CoreWindow**, чтобы приложение запускалось непосредственно в режиме погружения.

Используйте [CoreApplication. креатеневвиев](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_) и [аппликатионвиевсвитчер. свитчасинк](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_) , чтобы сделать его активным представлением.

> [!NOTE]
>* Не указывайте флаг [аппликатионвиевсвитчингоптионс. консолидатевиевс](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) для **свитчасинк** при переключении из представления XAML в иммерсивное представление, или планшет, в котором было запущено приложение, будет удален из мира.
>* **Свитчасинк** следует вызывать с помощью [диспетчера](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) , связанного с представлением, в которое вы переключаете.
>* Если необходимо запустить виртуальную клавиатуру или активировать другое приложение, необходимо будет **свитчасинк** обратно в представление XAML.

![Приложения могут переключаться между 2D-представлениями](images/slide7-600px.png) и иммерсивного представлениями ![, когда приложение переходит в иммерсивное представление, смешанный мир и другие приложения исчезают](images/slide8-600px.png)<br>
*Left: приложения могут переключаться между плоским представлением и иммерсивное представлением. Right: когда приложение переходит в иммерсивное представление, происходит исчезновение домашней и других приложений Windows Mixed Reality.*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>Переключение из иммерсивного представления обратно в представление XAML на клавиатуре

Одной из распространенных причин переключения между представлениями является отображение клавиатуры в приложении смешанной реальности. Оболочка может отображать системную клавиатуру только в том случае, если приложение отображает 2D-представление. Если приложению необходимо получить ввод текста, оно может предоставить пользовательское представление XAML с полем ввода текста, перейти на него, а затем переключиться обратно после завершения ввода.

Как и в предыдущем разделе, можно использовать **аппликатионвиевсвитчер. свитчасинк** для обратного перехода к представлению XAML из иммерсивного представления.

## <a name="app-size"></a>Размер приложения

представления 2D приложения всегда отображаются в фиксированном виртуальном планшете. Благодаря этому все 2D-представления отображают одинаковый объем содержимого. Ниже приведены некоторые дополнительные сведения о размере 2D-представления приложения.
* Пропорции приложения сохраняются при изменении размера.
* [Разрешение приложения и коэффициент масштабирования](building-2d-apps.md#2d-app-view-resolution-and-scale-factor) не изменяются путем изменения размера.
* Приложения не могут запрашивать фактический размер в мире.

![2D-приложения отображаются с фиксированными размерами окон](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*Приложения с плоским представлением отображаются с фиксированными размерами окон*

## <a name="app-tiles"></a>Плитки приложения

В меню «Пуск» используется стандартная небольшая плитка и средняя плитка для ПИН-кодов и список **все приложения** в смешанной реальности. 

![Меню "Пуск" для Windows Mixed Reality](images/start-500px.png)<br>
*Меню "Пуск" для Windows Mixed Reality*

## <a name="app-to-app-interactions"></a>Взаимодействие между приложениями

При создании приложений у вас есть доступ к многофункциональным механизмам взаимодействия приложений, доступным в Windows 10. Многие новые API протокола и регистрации файлов прекрасно работают в HoloLens, чтобы обеспечить запуск приложения и обмен данными. 

Обратите внимание, что для гарнитур рабочего стола приложение, связанное с заданным расширением или протоколом файла, может быть приложением Win32, которое может отображаться только на настольном мониторе или на рабочем столе.

### <a name="protocols"></a>Протоколы

HoloLens поддерживает запуск приложений с помощью API- [интерфейсов Windows. System. Launcher](https://docs.microsoft.com/uwp/api/Windows.System.Launcher).

При запуске другого приложения необходимо учитывать некоторые моменты.

* При выполнении не модального запуска, например [лаунчуриасинк](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_), пользователь должен поместить приложение перед взаимодействием с ним.

* При выполнении модального запуска, например с помощью [лаунчурифорресултсасинк](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_), модальное приложение помещается поверх окна.

* Windows Mixed Reality не может накладывать приложения поверх монопольных представлений. Чтобы показать запущенное приложение, Windows переводит пользователя в мир для отображения приложения.

### <a name="file-pickers"></a>Выбор файлов

HoloLens поддерживает контракты [филеопенпиккер](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) и [филесавепиккер](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) . Однако приложение не устанавливается заранее, выполняющее контракты средства выбора файлов. Такие приложения, например OneDrive, можно установить из Microsoft Store.

Если установлено несколько приложений для выбора файлов, Пользовательский интерфейс устранения неоднозначности для выбора запускаемого приложения не отображается. Вместо этого будет выбрано первое установленное средство выбора файлов. При сохранении файла создается имя файла, включающее метку времени. Он не может быть изменен пользователем.

По умолчанию локально поддерживаются следующие расширения:

|  Приложение  |  Расширения | 
|----------|----------|
|  Фотографии  |  BMP, GIF, JPG, PNG, AVI, MOV, MP4, WMV | 
|  Microsoft Edge  |  htm, HTML, PDF, SVG, XML | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>Контракты приложений и расширения Windows Mixed Reality

Контракты приложений и точки расширения позволяют зарегистрировать приложение, чтобы воспользоваться преимуществами более глубоких функций операционной системы, таких как обработка расширения файла или использование фоновых задач. Это список поддерживаемых и неподдерживаемых контрактов и точек расширения в HoloLens.

|  Контракт или расширение  |  Поддерживается? | 
|----------|----------|
| [Поставщик аватара учетной записи (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | Не поддерживается | 
| [Уведомления](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | Не поддерживается | 
| [Служба приложений](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | Поддерживается, но не полностью функциональным | 
| [Поставщик встреч](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | Не поддерживается | 
| [Автозапуск (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | Не поддерживается | 
| [Фоновые задачи (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | Частично поддерживается (не все триггеры) | 
| [Задача обновления (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | Поддерживается | 
| [Контракт обновления кэшированных файлов](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | Поддерживается | 
| [Параметры камеры (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | Не поддерживается | 
| [Протокол набора](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | Не поддерживается | 
| [Активация файла (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | Поддерживается | 
| [Контракт средства выбора файлов для открытия](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | Поддерживается | 
| [Контракт средства выбора файлов для сохранения](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | Поддерживается | 
| [Вызов экрана блокировки](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | Не поддерживается | 
| [Воспроизведение мультимедиа](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | Не поддерживается | 
| [Воспроизвести по контракту](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | Не поддерживается | 
| [Задача предварительно установленной конфигурации](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | Не поддерживается | 
| [Объемный рабочий процесс печати](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | Поддерживается | 
| [Параметры задачи печати (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | Не поддерживается | 
| [Активация URI (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | Поддерживается | 
| [Ограниченный запуск](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | Не поддерживается | 
| [Поиск по контракту](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | Не поддерживается | 
| [Контракт параметров](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | Не поддерживается | 
| [Поделиться контрактом](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | Не поддерживается | 
| [SSL/сертификаты (расширение)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | Поддерживается | 
| [Поставщик учетных записей веб-служб](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | Поддерживается | 

## <a name="app-file-storage"></a>Хранилище файлов приложений

Все хранилище осуществляется через [пространство имен Windows. Storage](https://docs.microsoft.com/uwp/api/Windows.Storage). Дополнительные сведения см. в следующей документации. HoloLens не поддерживает синхронизацию и роуминг хранилища приложений.

* [Файлы, папки и библиотеки](https://docs.microsoft.com/windows/uwp/files/index)
* [Хранение и извлечение параметров и прочих данных приложения](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>Известные папки

Полные сведения о приложениях UWP см. в разделе [кновнфолдерс](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) .

<table>
<tr>
<th> Свойство</th><th> Поддерживается в HoloLens</th><th> Поддерживается на впечатляющих гарнитурах</th><th> Описание</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">аппкаптурес</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает папку "записи приложения".</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">камераролл</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает папку рулона камеры.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">документслибрари</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает библиотеку документов. Библиотека документов не предназначена для общего использования.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">мусиклибрари</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает музыкальную библиотеку.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает объемные папки объектов.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">пиктуреслибрари</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает библиотеку изображений.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">Списки воспроизведения</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает папку "списки воспроизведения".</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">саведпиктурес</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает папку сохраненных изображений.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">видеослибрари</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Возвращает библиотеку видео.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">Соединяющ</a></td><td></td><td style="text-align: center;">✔️</td><td>Возвращает папку домашней группы.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">медиасервердевицес</a></td><td></td><td style="text-align: center;">✔️</td><td>Возвращает папку для устройств Media Server (Digital живая Network Alliance (DLNA)).</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">рекордедкаллс</a></td><td></td><td style="text-align: center;">✔️</td><td>Возвращает папку записанных вызовов.</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">ремовабледевицес</a></td><td></td><td style="text-align: center;">✔️</td><td>Возвращает папку "съемные устройства".</td>
</tr>
</table>

## <a name="app-package"></a>пакет приложения;

В Windows 10 вы больше не нацелены на операционную систему, а вместо этого нацеливанием [на приложение для одного или нескольких семейств устройств](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families). Семейство устройств определяет API-интерфейсы, характеристики системы и поведение, ожидаемые на устройствах внутри семейства. Он также определяет набор устройств, на которых можно установить приложение из [Microsoft Store](submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families).

* Чтобы выбрать гарнитуры рабочего стола и HoloLens, нацеливание на приложение на семейство устройств **Windows. Universal** .
* Чтобы выбрать только гарнитуры рабочего стола, нацеливание на ваше приложение на семейство устройств **Windows. Desktop** .
* Чтобы выбрать только HoloLens, нацеливание на приложение на семейство устройств **Windows. holographic** .

## <a name="see-also"></a>См. также

* [Представления приложений](app-views.md)
* [Обновление двухмерных приложений UWP для смешанной реальности](building-2d-apps.md)
* [Руководство по проектированию средств запуска трехмерных приложений](3d-app-launcher-design-guidance.md)
* [Реализация запусков трехмерных приложений](implementing-3d-app-launchers.md)
