---
title: Развертывание на устройстве в Unreal
description: Рекомендации по развертыванию на устройство в нереальном режиме в HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Нереал, Нереал. 4, UE4, HoloLens, HoloLens 2, Mixed Reality, развертывание на устройстве, ПК, документация
appliesto:
- HoloLens 2
ms.openlocfilehash: 2d0cd67db79c1970695334d826fbbaf0f2f92ec0
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408182"
---
# <a name="deploy-to-device-in-unreal"></a>Развертывание на устройстве в Unreal

## <a name="overview"></a>Обзор
Существует два способа развертывания нереального приложения в HoloLens 2: 
* Непосредственно из нереального редактора
* Как пакет, отправленный через портал устройств

Для обоих вариантов требуется настроить HoloLens для использования [портала устройств](using-the-windows-device-portal.md) для разработки. 

## <a name="deploying-to-device-from-the-unreal-editor"></a>Развертывание на устройстве из нереального редактора

1. Щелкните стрелку раскрывающегося списка рядом с кнопкой **запустить** . Изначально параметр устройства HoloLens будет неактивен.

![Параметры раскрывающегося списка запуска](images/unreal/launch-dropdown.png)

2. Откройте **Device Manager**. Обратите внимание, что HoloLens не будет автоматически отображаться в списке устройств.

3. Разверните раздел **Добавление устройства, не имеющего списка** .

4. Выберите **HoloLens** в качестве **платформы**.

5. Введите IP-адрес устройства и сведения о портах, разделенные двоеточием, в качестве идентификатора устройства. Например, "127.0.0.1:10080" (при подключении через USB). Используйте учетные данные пользователя и пароля на портале устройства.

6. Нажмите кнопку **Добавить** и закройте Диспетчер устройств. 
    * В случае ошибки (например, неправильного адреса, имени пользователя или пароля) сообщение будет напечатано в выходном журнале.

![Добавление устройства, не добавленного в список](images/unreal/add-unlisted-device.png)

7. Снова щелкните стрелку раскрывающегося списка рядом с кнопкой **запустить** . на этот раз вы должны увидеть только что добавленное устройство HoloLens. Выберите устройство HoloLens для сборки и развертывания в HoloLens. 

>[!NOTE]
>Сборка для устройства может потребовать перекомпиляции шейдеров (особенно при первом запуске). это может занять некоторое время. Не позволяйте устройству переходить в спящий режим до тех пор, пока не будет запущена приложение (возможно, его придется поработать). В противном случае компиляция шейдера завершится ошибкой.

## <a name="deploying-to-device-via-device-portal"></a>Развертывание на устройстве с помощью портала устройств

Подробные инструкции по [упаковке и развертыванию приложения](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) можно найти в последнем разделе Начало работы с нереальными сериями руководств.
