---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465202"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure пространственных привязки и отзывов

В этом уроке мы узнаем, как интегрировать Azure пространственных привязки (ASA) в наш общий интерфейс. ASA позволяет иметь Справочник по общим, если их физической среды виртуальные компоненты для работы привязки таким образом, чтобы все участники см. в разделе объектов находится там же физических несколько совмещенной устройства.

Прежде чем продолжить с этого занятия, нам потребуется для выполнения модуля обучения ASA, который мы рассмотрим основы ASA, учетная запись Azure и создание ресурсов и других блоков фундаментальные здания, которые необходимы, прежде чем мы можете интегрировать ASA в наш общий интерфейс.

Цели:

- Интеграция ASA в общий интерфейс для нескольких устройств выравнивания
- Изучение основ работы ASA в контексте локального общего качества

### <a name="instructions"></a>Инструкция

1. Сохраните проект на предыдущем занятии (CTRL + S) и назовите его «HLSharedProjectMainPart5.unity», так как это было легко найти, когда она понадобится снова.

2. Выберите prefab TableAnchor под MixedRealityPlayspace родительского объекта и удалите его.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  В представлении проекта перейти к ресурсам, "->" ресурсы "->" Prefabs, а затем перетащите prefab TableAnchor поверх SharedPlayground объект в качестве дочернего.
4.  Разверните MixedRealityPlayspace родительский объект, объект TableAnchor, а также объект кнопки. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Теперь в иерархии, выберите ShareAzureAnchorButton и переместите вашего внимания Inaspector панели. Прокрутите вниз до раскрывающееся меню, показанный на рисунке ниже, выберите AnchorModuleScript и нажмите кнопку ShareAnchorNetework().

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Выберите GetAzureAnchorButton (см. шаг 4), и переместите вашего внимания, вернитесь к панели инспектора. Прокрутите вниз до раскрывающееся меню, показанный на рисунке ниже и выберите AnchorModuleScript и нажмите кнопку GetSharedAnchorNetwork() и сохраните.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Поздравляем!

В этом уроке вы узнали, как интегрировать Azure мощные новые Пространственные привязки для выравнивания совмещенной устройств в общий интерфейс! Этого занятия также завершается работа модуля управления доступом. Мы узнали, как настроить учетную запись Photon, интегрировать Photon и СОВМЕСТНОЙ в новое приложение Unity, Настройка аватары и общих объектов и наконец выравнивание несколькими участниками, используя ASA. 

