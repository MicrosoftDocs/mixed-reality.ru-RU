---
title: Учебники по службам речи Azure — 3. Добавление компонента перевода речи Azure Cognitive Services
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913198"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Добавление компонента перевода речи Azure Cognitive Services

В этом учебнике мы рассмотрим компонент перевода речи Azure Cognitive Services в нашем проекте, а также на трех разных языках.

## <a name="instructions"></a>Инструкция

1. Выберите объект Lunarcom_Base в иерархии и нажмите кнопку Добавить компонент на панели Инспектор. Найдите и выберите распознаватель Лунарком Translation.

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    Отключите симулятор автономного режима.

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >Перед переходом убедитесь, что симулятор автономного режима отключен, как показано на рисунке выше, перед тестированием транслятора Speech-SDK. Для преобразования необходимо подключение к Интернету.

2. Щелкните раскрывающийся список раскрывающегося списка Лунарком Translation и выберите язык, на который вы хотите перевести.

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Теперь запустите приложение и протестируйте переводчик, нажав кнопку спутника и начинайте говорить. Нажмите вспомогательную кнопку еще раз, чтобы прерывать распознавание. Ниже приведен пример того, как будет выглядеть сцена. Вы можете изменить язык в раскрывающемся списке "целевой язык" (см. рисунок выше), чтобы просмотреть перевод на другие языки.

    Ниже приведен пример того, как должна выглядеть сцена:

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Поздравляем!

Теперь ваш проект может переводить слова на несколько разных языков. Вы можете поэкспериментировать с языками и проверить точность перевода.

[Следующее руководство: 4. Настройка намерения и естественного понимания языка](mrlearning-speechSDK-ch4.md)
