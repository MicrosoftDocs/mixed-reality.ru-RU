---
title: Общие пространственные привязки в DirectX
description: Объясняется, как синхронизировать два устройства HoloLens путем совместного использования пространственных привязок.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, синхронизация, пространственный якорь, перемещение, многопрограммный, просмотр, сценарий, пошаговое руководство, пример кода, Azure, пространственные привязки Azure, ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516889"
---
# <a name="shared-experiences-in-directx"></a>Общие возможности DirectX

Совместный опыт — это один из нескольких пользователей, каждый из которых имеет собственное устройство HoloLens, iOS или Android, совместное представление и взаимодействие с одной голограммой, которая находится в фиксированном месте. Это достигается благодаря совместному использованию пространственной привязки.

## <a name="azure-spatial-anchors"></a>Пространственная привязка Azure

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания устойчивых облачных пространственных привязок, которые приложение может разместить на нескольких устройствах HoloLens, iOS и Android.  При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.  Это позволяет обмениваться опытом в режиме реального времени.

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно также использовать для сохранения асинхронной голограммы на устройствах HoloLens, iOS и Android.  Благодаря совместному использованию надежной облачной пространственной привязки несколько устройств могут наблюдать одну и ту же постоянную голограмму с течением времени, даже если они находятся в разное время в разных местах.

Чтобы приступить к созданию общих интерфейсов в приложении HoloLens, ознакомьтесь с кратким руководством по HoloLens в течение 5 минут для <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">пространственных привязок Azure</a>.

После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">создавать и размещать привязки на HoloLens</a>.  Также доступны пошаговые руководства для <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android и iOS</a> , что позволяет использовать одни и те же привязки на всех устройствах.

## <a name="local-anchor-transfers"></a>Передача локальных привязок

В ситуациях, когда нельзя использовать пространственные привязки Azure, [Передача локальных точек](local-anchor-transfers-in-directx.md) подключения позволяет одному устройству hololens экспортировать привязку, которая будет импортирована вторым устройством hololens.  Обратите внимание, что этот подход обеспечивает менее устойчивое отзыв, чем пространственные привязки Azure, а устройства iOS и Android не поддерживаются этим подходом.

## <a name="see-also"></a>См. также
* [Общий доступ в смешанной реальности](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Пакет SDK для пространственных привязок Azure для HoloLens</a>