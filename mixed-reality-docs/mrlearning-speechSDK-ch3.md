---
title: Учебники по службам речи Azure — 3. Добавление компонента перевода речи Azure Cognitive Services
description: В этом курсе вы узнаете, как реализовать пакет SDK для распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143235"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Добавление компонента перевода речи Azure Cognitive Services

В этом руководстве вы узнаете о компоненте перевода речи Azure Cognitive Services в проекте, а также о том, как выполнить перевод на три разных языка.

## <a name="instructions"></a>Инструкция

1. Выберите объект Lunarcom_Base в иерархии и нажмите кнопку Добавить компонент на панели Инспектор. Найдите и выберите распознаватель Лунарком Translation.

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    Отключите симулятор автономного режима.

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >Перед переходом убедитесь, что симулятор автономного режима отключен (как показано на рисунке выше) перед тестированием транслятора Speech-SDK. Для преобразования необходимо подключение к Интернету.

2. Щелкните раскрывающийся список раскрывающегося списка Лунарком Translation и выберите язык, на который вы хотите перевести.

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Запустите приложение и протестируйте переводчик, нажав кнопку вспомогательная кнопка, и начните говорить. Нажмите вспомогательную кнопку еще раз, чтобы прерывать распознавание. Ниже приведен пример того, как будет выглядеть сцена. Вы можете изменить язык в раскрывающемся списке "целевой язык" (см. рисунок выше), чтобы просмотреть перевод на другие языки.

    Ниже приведен пример того, как должна выглядеть сцена:

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Поздравляем!

Теперь ваш проект может успешно переводить слова на несколько разных языков. Вы можете поэкспериментировать с языками и проверить точность перевода.

[Следующее руководство: 4. Настройка намерения и естественного понимания языка](mrlearning-speechSDK-ch4.md)
