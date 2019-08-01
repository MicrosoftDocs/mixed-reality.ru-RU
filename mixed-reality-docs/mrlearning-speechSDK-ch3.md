---
title: Учебники по службам речи Azure — 3. Добавление компонента перевода речи Azure Cognitive Services
description: Пройдите этот курс, чтобы узнать, как реализовать пакет SDK для службы распознавания речи Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 27742702f7a274b3212cdf12c77d8acfa0a29834
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701828"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Добавление компонента перевода речи Azure Cognitive Services

В этом учебнике мы рассмотрим аабаут в нашем проекте компонент перевода речи Azure Cognitive Services, а также на трех разных языках. 

## <a name="instructions"></a>Инструкция

1. Выберите объект Lunarcom_Base в иерархии и нажмите кнопку Добавить компонент на панели инспектора. Найдите и выберите Лунаркомтранслатионрекогнизер.

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> Примечание. Перед тестированием транслятора речи-SDK убедитесь, что симулятор автономного режима отключен. Для преобразования необходимо подключение к Интернету. Чтобы найти этот параметр, см. изображение ниже. 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. Щелкните раскрывающийся список в Лунаркомтранслатионрекогнизер и выберите язык, на который вы хотите перевести.

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Теперь запустите приложение и протестируйте переводчик, нажав кнопку спутника и начинайте говорить. Нажмите вспомогательную кнопку еще раз, чтобы прерывать распознавание. Ниже приведен пример того, как будет выглядеть сцена. Вы можете изменить язык в раскрывающемся списке "целевой язык" (см. рисунок выше), чтобы просмотреть перевод на другие языки.

> Примечание. Перед тестированием убедитесь, что автономный симулятор отключен, как показано на рисунке ниже.
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

Ниже приведен пример того, как должна выглядеть сцена:

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Поздравляем!

Теперь ваш проект может переводить слова на несколько разных языков. Вы можете поэкспериментировать с языками и проверить точность перевода. 

[Следующий учебник: 4.  Настройка намерения и распознавание естественного языка](mrlearning-speechSDK-ch4.md)

