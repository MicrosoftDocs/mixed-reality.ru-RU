---
title: Руководства по многопользовательским возможностям, часть 2. Подготовка Unity к разработке
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031242"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Подготовка Unity к разработке

Из этого руководства вы узнаете, как подготовить и настроить Unity для разработки приложений, включая импорт Набора средств для смешанной реальности, настройку параметров сборки и подготовку сцены.

## <a name="objectives"></a>Задачи

* Настройка Unity для разработки приложений
* Импорт набора средств для смешанной реальности
* Подготовка сцены проекта

## <a name="instructions"></a>Инструкции

1. Скачайте и сохраните Набор средств Unity для смешанной реальности, щелкнув [здесь](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage).

2. В Unity откройте меню Assets (Активы) и выберите Import Package (Импорт пакета), а затем щелкните Custom Package (Пользовательский пакет).

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Выберите пакет Unity, который вы скачали по ссылке на шаге 1. Когда в Unity откроется всплывающее окно импорта, нажмите кнопку Import (Импорт), чтобы начать импорт МRТК. Это может занять несколько минут.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >Скачанный пакет будет размещен в локальной папке, в которой вы сохранили файл. Приведенный выше рисунок не соответствует реальному расположению пакета на вашем компьютере.

    После импорта пакета должно отобразиться окно конфигуратора проекта MRTK. В противном случае откройте это окно, щелкнув Mixed Reality Toolkit > Utilities > Configure Unity Project (Набор средств для смешанной реальности > Служебные программы > Настроить проект Unity) в меню Unity.

    В окне конфигуратора проектов MRTK разверните раздел Modify Configurations (Изменение конфигураций), снимите флажок Enable MSBuild for Unity (Включить MSBuild для Unity), убедитесь, что настроены остальные параметры, и нажмите кнопку Apply (Применить), чтобы применить эти параметры.

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > Так как MSBuild для Unity может поддерживать не все пакеты SDK, которые будут использоваться, с отключением могут быть проблемы. Поэтому настоятельно рекомендуется не включать MSBuild для Unity.
    
4. Создайте новую сцену. Это можно сделать, щелкнув меню File (Файл) и выбрав New Scene (Создать сцену). Сохраните ее с именем HLSharedProjectMain.

5. В разделе Mixed Reality Toolkit (Набор средств для смешанной реальности) щелкните Add to Scene (Добавить в сцену) и Configure (Настроить).

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Завершив этот процесс, выберите Набор средств для смешанной реальности (MRTK) в иерархии. На панели инспектора измените профиль конфигурации MRTK на DefaultHoloLens2ConfigurationProfile.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. Выберите Набор средств для смешанной реальности (MRTK) в иерархии. На панели инспектора найдите Mixed Reality Toolkit Script (Скрипт Набора средств для смешанной реальности) и нажмите кнопку Copy & Customize (Скопировать и настроить), как показано на рисунке ниже.  Откроется всплывающее меню, в котором нужно выбрать действие Clone (Клонировать).

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. Прокрутите вниз и снимите флажок Enable Diagnostics system (Включить систему диагностики), если вам не нужно это окно диагностики. Мы рекомендуем держать окно диагностики открытым во время разработки приложения для мониторинга производительности, а затем отключать его в рабочей среде или при демонстрации приложения. 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Откройте окно параметров сборки, нажав сочетание клавиш CTRL+SHIFT+B или выбрав пункт меню File (Файл) > Build Settings (Параметры сборки). Обратите внимание, что программа сейчас настроена для автономной платформы ПК, Mac и Linux. При разработке для HoloLens 2 выберите универсальную платформу Windows. Выберите этот вариант и щелкните Switch Platform (Сменить платформу).

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. Завершив процесс, щелкните флажок Add Open Scenes (Добавить открытые сцены). Теперь перейдите на панель Inspector (Инспектор) и убедитесь, что здесь установлен флажок справа от элемента Virtual Reality Supported (Поддержка виртуальной реальности), как показано на рисунке ниже. Также убедитесь, что установлен флажок рядом с элементом scenes/HLSharedProjectMain, как показано на рисунке ниже.

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. В разделе Publishing Settings (Параметры публикации) на панели Inspector (Инспектор) прокрутите содержимое вниз до элемента Capabilities (Возможности) и убедитесь, что установлены следующие флажки.

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. Импортируйте указанные здесь пользовательские пакеты.

    * [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (версия 2.1.1);
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage);
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage);
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage).

    >[!TIP]
    >Остальные процессы настройки проекта Unity для Пространственных привязок Azure вы можете найти в руководстве по [началу работы с Пространственными привязками Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) из серии, посвященной [Пространственным привязкам Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1).


13. На панели Project (Проект) откройте папку Prefabs (Заготовки). На следующих шагах вы добавите в сцену несколько заготовок. В папке Prefabs щелкните заготовку Debug Window (Окно отладки) и перетащите ее в иерархию. Завершив этот процесс, сохраните проект, выбрав пункты меню File > Save (Файл > Сохранить) или нажав сочетание клавиш Ctrl+S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Возможно, при щелчке по заготовке появится всплывающее окно с запросом о компоненте TMP Essentials. Щелкните кнопку импорта TMP Essentials, так как это обязательный компонент. Если появится это всплывающее окно, вам лучше удалить заготовку из иерархии и повторно перетащить ее в эту иерархию, чтобы избежать потенциальных проблем с текстами.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Поздравляем!

Теперь проект Unity готов к работе с Photon. В следующих руководствах мы будем дальше развивать эту сцену и проект Unity в целом, чтобы создать полноценное взаимодействие для совместного использования.

[Следующее руководство: 3. Подключение нескольких пользователей](mrlearning-sharing(photon)-ch3.md)
