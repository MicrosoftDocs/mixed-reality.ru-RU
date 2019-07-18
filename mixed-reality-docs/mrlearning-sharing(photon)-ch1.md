---
title: Модуль совместного использования MR для HoloLens 2
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: e40cd50f75ca509c601d215cb865161ea3596565
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293647"
---
#  <a name="setting-up-photon-unity-networking"></a>Настройка сети Unity Photon

Из этого руководства вы узнаете, как подготовиться к созданию общего интерфейса, импортировав Photon Unity Networking (шутка) в проект Unity. Photon — это один из нескольких сетевых возможностей, доступных разработчикам смешанной реальности для создания общих возможностей. Мы научитесь создавать учетную запись Photon, импортировать Photon и создавать необязательный локальный сервер.

Служит

* Узнайте, как создать учетную запись Photon.

* Узнайте, как найти и импортировать сеть Unity Photon

* Настройка локального сервера Photon

  

### <a name="setting-up-photon"></a>Настройка Photon

1. Настройте учетную запись [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) . Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com/en-US/Account/SignUp). Чтобы создать учетную запись, следуйте инструкциям на странице регистрации. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Создайте идентификатор приложения, нажав кнопку Создать новое приложение.

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Выберите Photon шутка в раскрывающемся меню в разделе Тип Photon. Затем присвойте ему имя. В этом примере мы назвали IT Хололенсфотонпрожект. По завершении нажмите кнопку Создать.

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. После этого вернитесь на страницу приложения, и вы увидите примерно следующее изображение. Щелкните идентификатор приложения и скопируйте его. Вставьте его в любом месте, к которому вы можете легко получить доступ.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Создайте новый проект Unity и назовите его Хлшарингпрожект. Инструкции по созданию нового проекта Unity см. в [разделе "Создание проекта Unity" базового модуля](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. После загрузки проекта перейдите на вкладку Asset Store (ресурсы магазина), как показано на рисунке ниже. Затем в поле поиска, выделенном на изображении ниже, введите шутка и в результатах поиска выберите ресурс Photon шутка 2 (бесплатный). 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Скачайте и импортируйте этот ресурс, нажав кнопку Скачать и импортировать.

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. После завершения процесса импорта Photon появится мастер шутка. Возьмите идентификатор приложения (который должен находиться в буфере обмена) из шага 4, вставьте его в поле AppID и нажмите кнопку проект установки. 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. После успешного добавления AppID перейдите в раздел Photon-> Фотонунитинетворкинг-> Resources-> Фотонсерверсеттингс in Assets. Выберите параметр использовать сервер имен и задайте для параметра фиксированный регион значение US или регион службы Photon.

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Поздравляем!

Вы успешно создали учетную запись Photon, настроили локальный сервер Photon и импортировали шутка в Unity. Следующим шагом является настройка проекта и последующее разрешение подключения с другими пользователями, чтобы несколько пользователей могли видеть вашу работу. 

[Следующий учебник: Подготовка Unity к работе](mrlearning-sharing(photon)-ch2.md)

