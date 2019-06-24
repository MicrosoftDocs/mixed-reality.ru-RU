---
title: Модуль ASA обучения MR Azure пространственных привязка в HoloLens 2
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326868"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (исправить мне, если я не так)

На этом занятии 

Цели:

* Узнайте, как ___

* Узнайте, как ___

  

## <a name="instructions"></a>Инструкция

### <a name="setting-up-photon"></a>Настройка Photon

1. Настройка [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) учетной записи. Таким образом будет состоять из ввода ваш адрес электронной почты и проход через несколько шагов проверки.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. Как только вы зарегистрированы, щелкните пакеты SDK. После перехода на эту страницу, щелкните «сервер» и убедиться, он говорит: «резидентной.» Прокрутите вниз и выберите команду «сервер», как показано на втором рисунке ниже.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. Приведет к отображается с меткой, для текстового поля «read me». Продолжим и его чтение. По завершении щелкните ссылку рядом с «downloadSDK», чтобы загрузить его.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. Дважды щелкните папку, после завершения загрузки.  Открыв проводнике раскрытия в папку пакета SDK, скопируйте в папку пакета SDK.
   
   - Следующим шагом будет перейти на диске C: windows и создайте новую папку с именем «сервер».
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - Теперь откройте папку и вставьте в папку пакета SDK, скопированный ранее.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. После завершения, откройте папку пакета SDK и перейдите в раздел «Развертывание» выберите «bin_Win64», затем дважды щелкните «Фотон control».


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> Примечание. Если у вас возникнут вопросы по IP-адрес или другие аналогичные вопросы, можно найти большую часть информации в панели инструментов (как показано на рисунке ниже).
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. Теперь, когда сервер настраивается и инициированный, вернитесь на веб-сайт Photon и щелкнуть значок «профиль» (boxed на рисунке ниже) и выберите «вашего приложения.»
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. Создайте идентификатор приложения, нажав кнопку «Создать новое приложение».

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - Выберите команду «Запустить Photon» в раскрывающемся меню в разделе «photon type». Затем присвойте ему имя, (то, что должен был бы запоминать). В этом примере мы назвали ее «HoloLensPhotonProject.» По завершении нажмите кнопку «Создать».

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. После этого вернуться на страницу приложения, и вы увидите нечто, как показано на рисунке ниже. Щелкните идентификатор приложения и скопируйте его. Вставить находится где-нибудь, которые можно легко получить.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. Создайте новый проект unity. Откройте центр Unity и выберите команду «new». Назовите его «HLSharingProject.» Нажмите кнопку Создать. 

   > Примечание. Это может занять до 2 минут, чтобы загрузить, в зависимости от быстродействия компьютера.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> Примечание: выберите место для сохранения проекта на своем компьютере, изменив параметр «расположение». Сохраните его в место будет запомнить и иметь быстрый доступ к.

10. После загрузки проекта, щелкните «ресурсы хранилища». Затем в поле поиска, показано на рисунке ниже, введите «СОВМЕСТНОЙ» и выберите «Бесплатная СОВМЕСТНОЙ 2 Photon» ресурс. 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. Загрузите и импортируйте!
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Настройка проекта Unity** 

11. Загрузите новые средства, необходимые для настройки Photon в Unity, нажав кнопку [здесь.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. В Unity щелкните в меню "средства" и выберите «Импорт ресурсов», а затем щелкните «пользовательские ресурсы».

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. Выберите пакет Unity, который вы загрузили по ссылке, указанный на шаге 1. Как только «импорт» появится в Unity, щелкните его.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> Примечание: везде, где загруженный пакет будет где его найти. На рисунке выше не представляют, где вы найдете пакета.

14. Создание новой сцены (это может быть реализована с помощью элемента управления / command + N или щелкнув «file» и выбрав команду «Создать сцену.»). Сохранить сцену как «HLSharedProjectMain.»

> Примечание: может появиться всплывающее окно, похожее на рисунке ниже. Сейчас просто нажмите кнопку «Нет».
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. В разделе «Смешанной реальности Toolkit» щелкните «Добавить сцену и настройка».

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. После ее завершения, новый файл конфигурации будет отображаться, предоставляя выбор для его настройки. Нажмите кнопку «Копировать и настройка».

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. Прокрутите список вниз и снимите флажок «Включить систему диагностики». Это облегчит настроили этот проект.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. Откройте параметры сборки (элемент управления + shift + B). Обратите внимание, что в настоящее время программа указана в разделе «отдельно ПК, Mac и Linux» платформы. Для этого проекта задайте платформы, чтобы быть «универсальная платформа windows.» Выберите его и нажмите кнопку «коммутатор платформы».

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. После завершения щелкните поле с текстом «добавить откройте сцены». Теперь перейдите к панели инспектора и убедитесь, что флажок справа от «поддерживается виртуальной реальности» (как показано на рисунке ниже) установлен. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> Примечание. Также убедитесь, что также установлен флажок рядом с «сцены/HLSharedProjectMain».

20. В разделе «Параметры публикации» на панели Инспектора прокрутите вниз до «возможности» и пометить только следующие флажки:

- Интернет-клиент
- клиент-сервер Интернета
- клиент-сервер частной сети
- камера/веб-камеры
- микрофон

21. Так же, как и шаг 12 следующим шагом было бы импортировать другой пользовательский пакет называется занятие «2», который можно скачать [здесь]. [здесь отображается ссылка lesson2.unitypackage] Импорт этого пакета.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. Теперь в панели «проект» перейдите к папке «prefabs» так, как в следующих шагах будет реализовано несколько prefabs на сцене. В папке «prefabs» щелкните и перетащите готового блока, «DebugWindow» в иерархии. По завершении сохраните проект (щелкните файл, затем сохраните или control + S)

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> Примечание. Вы можете заметить всплывающее окно отображается при выборе готового блока, запрашивающее о TMP Essentials. Нажмите кнопку «Импорт TMP Essentials», как они потребуются.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**Подключение нескольких пользователей**

23. Шаг 22, в папке «prefabs» в панели «проект», как следующий шаг — путем перетаскивания prefab «NetworkLobby» иерархии. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. При разворачивании родительского готового блока, «NetworkLobby», должна появиться prefab, дочерний «NetworkRoom.» С его включенным перейдите в панель инспектора и нажмите кнопку «Добавить компонент». Поиск «PhotonView» и добавить компонент.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. Создайте новый пустой объект игр в иерархии (правой кнопкой мыши в иерархии и выберите «empty»). Настройте расположение x = 0, y = 0, z = 0 и имя объекта «PhotonUser.»

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>Поздравляем!



