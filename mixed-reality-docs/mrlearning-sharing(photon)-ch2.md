---
title: Учебники по возможностям для нескольких пользователей — 2. Подготовка Unity к разработке
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 750161ff4c52a7ab71869b3cb0f97197d4ad09f2
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2019
ms.locfileid: "74106051"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Подготовка Unity к разработке 


В этом руководстве вы узнаете, как подготовить и настроить Unity для разработки приложений, включая импорт набора средств для смешанной реальности, настройку параметров сборки и подготовку сцены.

## <a name="objectives"></a>Задачи

- Настройка Unity для разработки приложений

- Импорт набора средств для смешанной реальности

- Подготовка сцены проекта

## <a name="instructions"></a>Инструкция

1. Скачайте и сохраните пакет Unity для набора средств Mixed Reality, щелкнув [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)

2. В Unity откройте меню активы и выберите Импорт пакета, а затем щелкните пользовательский пакет.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Выберите пакет Unity, который вы только что скачали, по ссылке, предоставленной на шаге 1. После появления всплывающего окна Импорт в Unity нажмите кнопку Импорт, чтобы начать импорт МРТК. Это может занять несколько минут.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Примечание. загруженный пакет находится в локальной папке, в которой сохранен файл. На приведенном выше рисунке не отображать, где находится пакет.

4. Создайте новую сцену. Это можно сделать, щелкнув файл и выбрав создать сцену. Сохраните его как Хлшаредпрожектмаин.

> Примечание. Вы можете получить всплывающее окно, похожее на изображение ниже. Пока нажмите кнопку нет.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. В разделе набор средств для смешанной реальности щелкните Добавить в сцену и настроить.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. После завершения работы появится новый файл конфигурации, в котором можно настроить профиль. 

![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. Выберите набор средств смешанной реальности (МРТК) из иерархии. На панели инспектора Найдите сценарий набора средств Mixed Reality и нажмите кнопку "Копировать & настроить", как показано на рисунке ниже.  После этого появится POP и выбрать параметр клонировать во всплывающем меню.

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

7. Прокрутите вниз и снимите флажок Включить систему диагностики, если необходимо скрыть окно Диагностика. Рекомендуется поддерживать Окно диагностики во время разработки приложения для мониторинга производительности, а затем отключать его во время демонстрации рабочей среды или приложения. 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Откройте параметры сборки, нажав клавиши CTRL + SHIFT + B или перейдя в файловые > параметры сборки. Обратите внимание, что программа в настоящее время задается в автономной платформе PC, Mac и Linux. Для разработки HoloLens 2 Задайте универсальная платформа Windows платформы. Выберите его и щелкните Сменить платформу.

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. После завершения щелкните рамку Add Open сцен (Добавить открытые сцены). Теперь перейдите на панель инспектора и убедитесь, что установлен флажок справа от параметра Virtual Reality Supported (как показано на рисунке ниже). Также убедитесь, что флажок рядом с параметром сцена/Хлшаредпрожектмаин также установлен, как показано на рисунке ниже.

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. В разделе "Параметры публикации" на панели инспектора прокрутите вниз до пункта возможности и убедитесь, что установлены следующие флажки:

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Импортируйте указанные пользовательские пакеты:

    а) [Unity. HoloLens2. GettingStarted. Tutorial. Asset. 2.1.0.0. пакет unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    б. [Unity. HoloLens2. Мултиусеркапабилитиес. Tutorial. Asset. 2.1.0.0. пакет unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    >Если вы выполнили [учебники по началу работы](mrlearning-base-ch1.md), у вас по-прежнему может быть пакет Unity с именем _Unity. HoloLens2. GettingStarted. Tutorial. Asset. 2.1.0.0. пакет unitypackage_ , хранящийся на компьютере. Если это так, можно пропустить загрузку ресурса, указанного на шаге a выше.

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. На панели проект перейдите в папку Prefabs. В следующих шагах в сцену будет реализовано несколько Prefabs. В папке Prefabs щелкните и перетащите окно prefab, отладку в иерархию. По завершении сохраните проект, щелкнув файл, а затем сохранить или нажмите клавиши CTRL + S.

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Примечание. Вы можете заметить, что всплывающее окно отображается при щелчке prefab, предлагающем о параметрах TMP Essentials. Щелкните Импортировать TMP Essentials по мере необходимости. При появлении этого всплывающего окна может потребоваться удалить prefab из иерархии и повторно перетащить его в иерархию, чтобы избежать потенциальных ошибок, связанных с текстом.
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Поздравляем!

Теперь проект Unity готов для Photon. В следующих учебных курсах мы создадим эту сцену и наш проект Unity в полном объеме для совместной работы.

[Следующее руководство: 3. Подключение нескольких пользователей](mrlearning-sharing(photon)-ch3.md)

