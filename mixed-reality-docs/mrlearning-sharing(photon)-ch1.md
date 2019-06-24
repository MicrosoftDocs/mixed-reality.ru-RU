---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326785"
---
# <a name="setting-up-photon"></a>Настройка Photon

На этом занятии будет рассказано также Подготовка для создания общего качества, импортировав сети Photon Unity (СОВМЕСТНОЙ) в проекте Unity. Photon — один из нескольких сетевых параметров для смешанной реальности разработчикам создать публикацию. Мы будет показано, как создать учетную запись Photon и импортировать Photon создания необязательно локального сервера

Цели:

* Узнайте, как создать учетную запись с Photon

* Узнайте, как найти и импортировать сетевые подключения Unity Photon

* Настройка локального сервера Photon

  

### <a name="setting-up-photon"></a>Настройка Photon

1. Настройка [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) учетной записи. Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com/en-US/Account/SignUp). Следуйте инструкциям на странице регистрации, чтобы создать учетную запись. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. Как только вы зарегистрированы, щелкните пакеты SDK. После перехода на эту страницу, щелкните «сервер» и убедиться, он говорит: «резидентной.» Прокрутите вниз и выберите команду «сервер», как показано на втором рисунке ниже.

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. Приведет к отображается с меткой, для текстового поля «read me». Продолжим и его чтение. По завершении щелкните ссылку рядом с «downloadSDK», чтобы загрузить его.


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. Дважды щелкните папку, после завершения загрузки.  Открыв проводнике раскрытия в папку пакета SDK, скопируйте в папку пакета SDK.
   
   - Следующим шагом будет перейти на диске C: windows и создайте новую папку с именем «сервер».
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - Теперь откройте папку и вставьте в папку пакета SDK, скопированный ранее.
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. После завершения, откройте папку пакета SDK и перейдите в раздел «Развертывание» выберите «bin_Win64», затем дважды щелкните «Фотон control».


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> Примечание. Если у вас возникнут вопросы по IP-адрес или другие аналогичные вопросы, можно найти большую часть информации в панели инструментов (как показано на рисунке ниже).
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. Теперь, когда сервер настраивается и инициированный, вернитесь на веб-сайт Photon и убедитесь, что по-прежнему вы вошли (или снова войдите, если вы не являетесь). Щелкните значок профиля (упаковывается в правом верхнем углу на рисунке ниже) и выберите «вашего приложения.»
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. Создайте идентификатор приложения, нажав кнопку «Создать новое приложение».

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - Выберите «Photon СОВМЕСТНОЙ» в раскрывающемся меню в разделе «photon type». Затем присвойте ему имя, в этом примере, мы назвали «HoloLensPhotonProject.» По завершении нажмите кнопку «Создать».

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. После этого вернуться на страницу приложения, и вы увидите нечто, как показано на рисунке ниже. Щелкните идентификатор приложения и скопируйте его. Вставить находится где-нибудь, которые можно легко получить.  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. Создайте новый проект unity и назовите его «HLSharingProject.» Инструкции по созданию нового проекта Unity, обратитесь к [раздел «Создание проекта Unity» базового модуля](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 


10. После загрузки проекта, откройте вкладку «активы store», как показано на рисунке ниже. Затем в поле поиска, выделены на рисунке ниже, введите «СОВМЕСТНОЙ» и выберите «Бесплатная СОВМЕСТНОЙ 2 Photon» ресурс в результатах поиска. 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. Скачайте и импортируйте этот ресурс нажатием кнопки «Загрузить» и «Импорт».
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a>Поздравляем!

Вы успешно создали учетную запись Photon, настроить локальный сервер Photon и импортировать СОВМЕСТНОЙ в Unity. Следующий шаг — проект, а затем разрешить соединения с другими пользователями, таким образом, чтобы несколько пользователей можно увидеть результаты работы. 

[Следующий урок. Sharing(Photon) занятие 2](mrlearning-sharing(photon)-ch2.md)

