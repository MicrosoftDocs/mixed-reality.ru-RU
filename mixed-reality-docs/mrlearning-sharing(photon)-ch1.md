---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416125"
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



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Создайте идентификатор приложения, нажав кнопку «Создать новое приложение».

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Выберите «Photon СОВМЕСТНОЙ» в раскрывающемся меню в разделе «photon type». Затем присвойте ему имя, в этом примере, мы назвали «HoloLensPhotonProject.» По завершении нажмите кнопку «Создать».

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. После этого вернуться на страницу приложения, и вы увидите нечто, как показано на рисунке ниже. Щелкните идентификатор приложения и скопируйте его. Вставить находится где-нибудь, которые можно легко получить.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Создайте новый проект unity и назовите его «HLSharingProject.» Инструкции по созданию нового проекта Unity, обратитесь к [раздел «Создание проекта Unity» базового модуля](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. После загрузки проекта, откройте вкладку «активы store», как показано на рисунке ниже. Затем в поле поиска, выделены на рисунке ниже, введите «СОВМЕСТНОЙ» и выберите ресурс «Photon СОВМЕСТНОЙ 2 — бесплатный» в результатах поиска. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Скачайте и импортируйте этот ресурс нажатием кнопки «Загрузить» и «Импорт».

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. После завершения процесса импорта Photon совместной мастера будут отображаться. Использовать идентификатор приложения (который должен быть в буфер обмена) из шага 4 и вставьте его в окне "AppID" и нажмите кнопку «Настройка проект». 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. После успешного добавления AppID, перейдите к «Фотон «->» PhotonUnityNetworking» -> «Ресурсы» -> «PhotonServerSettings» в средствах. Выберите параметр «Использовать имя сервера» и задайте фиксированную область «США» или вашего региона photon службы.

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Поздравляем!

Вы успешно создали учетную запись Photon, настроить локальный сервер Photon и импортировать СОВМЕСТНОЙ в Unity. Следующий шаг — проект, а затем разрешить соединения с другими пользователями, таким образом, чтобы несколько пользователей можно увидеть результаты работы. 

[Следующий урок. Sharing(Photon) занятие 2](mrlearning-sharing(photon)-ch2.md)

