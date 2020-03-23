---
title: Руководства по многопользовательским возможностям, часть 1. Настройка Photon Unity Networking
description: В рамках этого курса вы узнаете, как реализовать многопользовательские возможности в приложении HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031329"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Настройка Photon Unity Networking

## <a name="overview"></a>Обзор

В этом руководстве вы узнаете, как подготовиться к созданию совместного взаимодействия, импортировав Photon Unity Networking (PUN) в проект Unity. Photon — это одна из нескольких сетевых платформ, на основе которых разработчики смешанной реальности могут создавать возможности для совместного взаимодействия. Здесь вы узнаете, как создать учетную запись Photon, импортировать Photon и создать (необязательно) локальный сервер.

## <a name="objectives"></a>Задачи

* Вы научитесь создавать учетную запись Photon.
* Вы узнаете, как найти и импортировать Photon Unity Networking.
* Вы настроите сервер Photon.

## <a name="prerequisites"></a>Предварительные условия

>[!TIP]
>Если вы еще не прошли учебники [по началу работы](mrlearning-base.md) или [по началу работы с Пространственными привязками Azure](mrlearning-asa-ch1.md), мы рекомендуем начать знакомство именно с этих серий.

* Компьютер с Windows 10, настроенный с помощью требуемых [установленных инструментов](install-the-tools.md).
* Пакет SDK для Windows 10 версии 10.0.18362.0 и выше.
* Базовые навыки программирования на C#.
* Устройство HoloLens 2, [настроенное для разработки](using-visual-studio.md#enabling-developer-mode).

>[!IMPORTANT]
> Рекомендуемая версия Unity для этой серии руководств — Unity 2019.2.X. Это заменяет все требования к версии Unity и рекомендации, указанные выше.

## <a name="setting-up-photon"></a>Настройка Photon

1. Создайте учетную запись [Photon](https://dashboard.photonengine.com//Account/SignUp). Перейдите на страницу регистрации Photon, щелкнув [эту ссылку](https://dashboard.photonengine.com//Account/SignUp). На странице регистрации следуйте инструкциям по созданию учетной записи.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Создайте идентификатор приложения, нажав кнопку Create a New App (Создать новое приложение).

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Выберите PUN для Photon в раскрывающемся списке Photon Type (Тип Photon). Присвойте любое имя. В нашем примере это имя HoloLensPhotonProject. Завершив эти действия, нажмите кнопку Create (Создать).

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Вернитесь на страницу приложений, и вы увидите примерно следующее изображение. Щелкните идентификатор приложения и скопируйте его. Вставьте его куда-либо, где потом сможете легко его получить.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Создайте новый проект Unity и присвойте ему имя HLSharingProject. Инструкции по созданию проекта Unity см. в разделе [Create Unity Project](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project) (Создание проекта Unity) базового модуля. 

6. После загрузки проекта перейдите на вкладку Assets Store (Хранилище активов), как показано на рисунке ниже. Затем в поле поиска, которое выделено на изображении ниже, введите значение PUN и в результатах поиска выберите актив "Photon PUN 2 - FREE".

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Скачайте и импортируйте этот актив, нажав кнопки Download (Скачивание) и Import (Импорт).

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Когда процесс импорта Photon завершится, откроется мастер PUN. Возьмите идентификатор приложения из шага 4 (он должен находиться в буфере обмена), вставьте его в поле AppID и нажмите кнопку Setup Project (Настроить проект).

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. После успешного добавления AppID перейдите в списке активов к разделу Photon >PhotonUnityNetworking ->Resources (Ресурсы)->PhotonServerSettings. Выберите вариант Use Name Server (Использовать сервер имен) и задайте фиксированный регион "США" или регион вашей службы Photon.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Поздравляем!

Вы успешно создали учетную запись Photon, настроили локальный сервер Photon и импортировали PUN в Unity. Следующим шагом будет настройка проекта и разрешение подключений для других пользователей, чтобы вашу работу могли видеть несколько пользователей.

[Следующее руководство: 2. Подготовка Unity к работе](mrlearning-sharing(photon)-ch2.md)
