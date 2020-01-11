---
title: Учебники по возможностям для нескольких пользователей — 1. Настройка сети Unity Photon
description: Пройдите этот курс, чтобы узнать, как реализовать совместное использование нескольких пользователей в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: efa03c49a9a083d2b8e591e03bccbeb776bb57b2
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901474"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Настройка сети Unity Photon

## <a name="overview"></a>Обзор

В этом руководстве вы узнаете, как подготовиться к созданию общего интерфейса, импортировав Photon Unity Networking (шутка) в проект Unity. Photon — это один из нескольких сетевых возможностей, доступных разработчикам смешанной реальности для создания общих возможностей. Вы узнаете, как создать учетную запись Photon, импортировать Photon и создать необязательный локальный сервер.

## <a name="objectives"></a>Задачи

* Узнайте, как создать учетную запись Photon.
* Узнайте, как найти и импортировать сеть Unity Photon
* Настройка локального сервера Photon

## <a name="prerequisites"></a>Необходимые условия

>[!TIP]
>Если вы еще не выполнили учебники [Приступая к работе](mrlearning-base.md) и службы [пространственных привязок Azure](mrlearning-asa-ch1.md) , мы рекомендуем сначала выполнить эти учебники.

* КОМПЬЮТЕР с Windows 10 с [установленными](install-the-tools.md) правильными инструментами
* Windows 10 SDK 10.0.18362.0 или более поздней версии
* Некоторые базовые C# возможности программирования
* Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode)

>[!IMPORTANT]
>Для этой серии руководств требуется <a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019,1</a> , а рекомендуемая версия — Unity 2019.1.14. Это заменяет все требования к версии Unity или рекомендации, указанные в связанных выше условиях.

## <a name="setting-up-photon"></a>Настройка Photon

1. Настройте учетную запись [Photon](https://dashboard.photonengine.com//Account/SignUp) . Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com//Account/SignUp). Чтобы создать учетную запись, следуйте инструкциям на странице регистрации.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Создайте идентификатор приложения, нажав кнопку Создать новое приложение.

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Выберите Photon шутка в раскрывающемся меню в разделе Тип Photon. Затем присвойте ему имя. В этом примере мы назвали IT Хололенсфотонпрожект. По завершении нажмите кнопку Создать.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Вернитесь на страницу приложений, и вы увидите примерно следующее изображение. Щелкните идентификатор приложения и скопируйте его. Вставьте его в любом месте, к которому вы можете легко получить доступ.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Создайте новый проект Unity и назовите его Хлшарингпрожект. Инструкции по созданию нового проекта Unity см. в [разделе "Создание проекта Unity" базового модуля](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. После загрузки проекта перейдите на вкладку хранилище ресурсов, как показано на рисунке ниже. Затем в поле поиска, выделенном на изображении ниже, введите шутка и в результатах поиска выберите ресурс Photon шутка 2 (бесплатный).

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Скачайте и импортируйте этот ресурс, нажав кнопку Скачать и импортировать.

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. После завершения процесса импорта Photon появится мастер шутка. Возьмите идентификатор приложения (который должен находиться в буфере обмена) из шага 4, вставьте его в поле AppID и нажмите кнопку проект установки.

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. После успешного добавления AppID перейдите в раздел Photon-> Фотонунитинетворкинг-> Resources-> Фотонсерверсеттингс in Assets. Выберите параметр использовать сервер имен и задайте для параметра фиксированный регион значение US или регион службы Photon.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Поздравляем!

Вы успешно создали учетную запись Photon, настроили локальный сервер Photon и импортировали шутка в Unity. Следующим шагом является настройка проекта и разрешение подключений с другими пользователями, чтобы несколько пользователей могли видеть вашу работу.

[Следующий учебник: 2. Подготовка Unity к разработке](mrlearning-sharing(photon)-ch2.md)
