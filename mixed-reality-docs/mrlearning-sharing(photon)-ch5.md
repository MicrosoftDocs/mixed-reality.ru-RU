---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327298"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure пространственных привязки и отзывов

На этом занятии будет рассказано как интегрировать Azure пространственных привязки (ASA) в наш общий интерфейс. ASA позволяет иметь общее представление, если их физической среды, чтобы привязать виртуальный таким образом, чтобы все участники см. в разделе объектов находится там же физических несколько совмещенной устройства.

Прежде чем продолжить с этого занятия, будет необходимо выполнить модуль ASA обучения, который мы рассмотрим основы ASA, учетная запись Azure и создание ресурсов и других блоков фундаментальные здания, которые необходимы, прежде чем мы можете интегрировать ASA в наш общий интерфейс.

Цели:

- Интеграция ASA в общий интерфейс для нескольких устройств выравнивания
- Изучение основ работы ASA в контексте локального общего качества

### <a name="instructions"></a>Инструкция

1. Сохраните проект на предыдущем занятии (CTRL + S) и назовите его «HLSharedProjectMainPart5.unity», так как это было легко найти, когда она понадобится снова.

2. Выберите prefab TableAnchor под «MixedRealityPlayspace» родительского объекта и удалите его.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. Так же, как некоторые из предыдущих занятий, импортировать новый пользовательский пакет, который можно получить [здесь.](placeholderlink)

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. После импорта, захватите привязки обновленного таблицы (из пакета unity, импортированные в предыдущем шаге) в папке «prefabs» в панели «проект» и поместите его в родительский объект «MixedRealityPlayspace.»

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. Разверните родительский объект «MixedRealityPlayspace», то объект «TableAnchor», а также объект «кнопки». 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. Теперь в иерархии, выберите «ShareAzureAnchorButton» и переместите вашего внимания к панели инспектора. Прокрутите вниз, чтобы в раскрывающемся меню, показанный на рисунке ниже и выберите «AnchorModuleScript» и щелкните «ShareAnchorNetework().»

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. Подобно шаг 6 выберите «GetAzureAnchorButton» и переместите вашего внимания, вернитесь к панели инспектора. Прокрутите вниз, чтобы в раскрывающемся меню, показанный на рисунке ниже и выберите «AnchorModuleScript» и щелкните «GetSharedAnchorNetwork().» Затем сохраните.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Поздравляем!

В этом уроке вы узнали, как интегрировать Azure мощные новые Пространственные привязки для выравнивания совмещенной устройств в общий интерфейс! Этого занятия также завершается работа модуля управления доступом. Мы узнали, как настроить учетную запись Photon, интегрировать Photon и СОВМЕСТНОЙ в новое приложение Unity, Настройка аватары и общих объектов и наконец выравнивание несколькими участниками, используя ASA. 

