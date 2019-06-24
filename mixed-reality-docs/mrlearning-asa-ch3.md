---
title: Модуль ASA обучения MR Azure пространственных привязка в HoloLens 2
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326800"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>Отображение отзывов Azure пространственных привязки

На этом занятии вы узнаете о том, как предоставить пользователям возможность отзыв о привязки обнаружения, события и состояние, при использовании привязки пространственных Azure.

Цели:

* Узнайте, как настроить пользовательский Интерфейс панель, в которой отображаются важные сведения о текущем сеансе ASA

* Изучение отзывов элементы, которые пакет SDK ASA делает доступными пользователям вопроса

  

## <a name="instructions"></a>Инструкция

### <a name="set-up-asa-feedback-ui-panel"></a>Настроить панель пользовательского интерфейса ASA отзывов

1. На этом занятии мы не используем «SaveAnchorToDisk» и «ShareAnchor» кнопки, поэтому выберите обе кнопки и снимите этот флажок, на панели инспектора (как показано ниже), чтобы скрыть эти кнопки.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. Создайте панели «инструкции». Запустить, щелкнув правой кнопкой мыши кнопку «instructions», наведите указатель мыши «трехмерный объект» и выберите «textmeshpro-text».

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. Измените масштаб и позиционирования текста, чтобы он соответствовал с инструкциями в сцене. Кроме того убедитесь, что выравнивание для весь текст выравнивается по центру. Удалите текст из текстового редактора, как показано на рисунке ниже.


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. Измените имя объекта TextMeshPro на «FeedbackPanel.»
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. На панели «Проект» выберите «активы» и щелкните правой кнопкой мыши, а затем выберите «Показать в обозревателе».
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

Теперь щелкните [здесь](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) для загрузки файлов требуется в следующих шагах.

6. После открытия обозревателя выберите папку assets, а затем папку «ASAmodulesAssets» и скопируйте скрипт обратной связи привязки и файлы скриптов модуля привязки в папку. 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> Обратите внимание: Если появится всплывающее окно, запросом, вас, если вы хотите перезаписать старую или сохранить старую обязательно выберите перезапись.

7. Теперь вернемся к папке средств. Затем перейдите в папку «AzureSpatialAnchorsPlugin», а затем папки с примерами и, наконец, в папку scripts и скопируйте оболочки Демонстрация Azure пространственных привязки в эту папку. 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. Теперь, когда файлы передаются, убедитесь, что текст «feedbackpanel» выбран в иерархии ASA_feedback и нажмите кнопку «Добавить компонент» и добавьте скрипт обратной связи привязки, его поиск и выбрав его, как только он появится. 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. Перетащите объект текст «feedbackPanel» из иерархии ASA_Feedback в пустой слот под сценарий, как показано на рисунке ниже. 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a>Поздравляем!

В этом уроке мы узнали, как для создания области пользовательского интерфейса для отображения текущего состояния запуска привязки пространственных Azure для предоставления пользователю обратной связи в режиме реального времени.


