---
title: Г-н обучения, совместное использование модуля для HoloLens 2
description: Выполните этот курс, чтобы узнать, как реализовать публикацию нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523299"
---
#  <a name="setting-up-photon-unity-networking"></a>Настройки доступа Unity Photon

В этом руководстве мы узнаем, как для подготовки к использованию для создания общего качества, импортировав сети Photon Unity (СОВМЕСТНОЙ) в проекте Unity. Photon — один из нескольких сетевых параметров для смешанной реальности разработчикам создать публикацию. Мы будет показано, как создать учетную запись Photon и импортировать Photon создания необязательно локального сервера

Цели:

* Узнайте, как создать учетную запись Photon

* Узнайте, как найти и импортировать сетевые подключения Unity Photon

* Настройка локального сервера Photon

  

### <a name="setting-up-photon"></a>Настройка Photon

1. Настройка [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) учетной записи. Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com/en-US/Account/SignUp). Следуйте инструкциям на странице регистрации, чтобы создать учетную запись. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Создайте идентификатор приложения, нажав кнопку Создать кнопку нового приложения.

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Выберите в раскрывающемся меню в качестве типа Photon Photon СОВМЕСТНОЙ. Затем присвойте ему имя. В этом примере мы назвали его HoloLensPhotonProject. По завершении нажмите кнопку «Создать».

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. После этого вернуться на страницу приложения, и вы увидите нечто, как показано на рисунке ниже. Щелкните идентификатор приложения и скопируйте его. Вставить находится где-нибудь, которые можно легко получить.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Создайте новый проект unity и назовите его HLSharingProject. Инструкции по созданию нового проекта Unity, обратитесь к [раздел «Создание проекта Unity» базового модуля](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. После загрузки проекта, откройте вкладку Store средств, как показано на рисунке ниже. Затем в поле поиска, выделены на рисунке ниже, введите в СОВМЕСТНОЙ и выберите 2 СОВМЕСТНОЙ Photon - FRE» ресурс в результатах поиска. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Скачайте и импортируйте этот ресурс нажатием кнопки загрузки и импорта.

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. После завершения процесса импорта Photon появится мастер совместной. Использовать идентификатор приложения (который должен быть в буфер обмена) из шага 4 и вставьте его в окне "AppID" и нажмите кнопку проекта установки. 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. После успешного добавления AppID, перейдите к Photon "->" PhotonUnityNetworking "->" ресурсы "->" PhotonServerSettings в ресурсах. Выберите параметр используйте имя сервера и задайте фиксированный нам или yourPphoton службы регионе.

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Поздравляем!

Вы успешно создали учетную запись Photon, настроить локальный сервер Photon и импортировать СОВМЕСТНОЙ в Unity. Следующий шаг — проект, а затем разрешить соединения с другими пользователями, таким образом, чтобы несколько пользователей можно увидеть результаты работы. 

[Следующему руководству: Подготовка к работе, для разработки Unity](mrlearning-sharing(photon)-ch2.md)

