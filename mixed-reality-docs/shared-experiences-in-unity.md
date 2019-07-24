---
title: Общие возможности в Unity
description: Совместное использование одних и тех же голограмм между несколькими пользователями в приложении Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Совместное использование, привязка, Ворлданчор, MR совместное использование 250, Ворлданчортрансфербатч, Спатиалперцептион, Azure, пространственные привязки Azure, ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516791"
---
# <a name="shared-experiences-in-unity"></a>Общие возможности в Unity

Совместный опыт — это один из нескольких пользователей, каждый из которых имеет собственное устройство HoloLens, iOS или Android, совместное представление и взаимодействие с одной голограммой, которая находится в фиксированном месте. Это достигается благодаря совместному использованию пространственной привязки.

## <a name="azure-spatial-anchors"></a>Пространственная привязка Azure

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно использовать для создания устойчивых облачных пространственных привязок, которые приложение может разместить на нескольких устройствах HoloLens, iOS и Android.  При совместном использовании общей пространственной привязки на нескольких устройствах каждый пользователь может видеть содержимое, отображаемое относительно этой привязки в том же физическом расположении.  Это позволяет обмениваться опытом в режиме реального времени.

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Пространственные привязки Azure</a> можно также использовать для сохранения асинхронной голограммы на устройствах HoloLens, iOS и Android.  Благодаря совместному использованию надежной облачной пространственной привязки несколько устройств могут наблюдать одну и ту же постоянную голограмму с течением времени, даже если они находятся в разное время в разных местах.

Чтобы приступить к созданию общих интерфейсов в Unity, ознакомьтесь с пошаговыми руководствами Unity по 5-минутной <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">пространственной привязке Azure</a>.

После завершения работы с пространственными привязками Azure можно <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создавать и искать привязки в Unity</a>.

## <a name="local-anchor-transfers"></a>Передача локальных привязок

В ситуациях, когда нельзя использовать пространственные привязки Azure, [Передача локальных точек](local-anchor-transfers-in-unity.md) подключения позволяет одному устройству hololens экспортировать привязку, которая будет импортирована вторым устройством hololens.  Обратите внимание, что этот подход обеспечивает менее устойчивое отзыв, чем пространственные привязки Azure, а устройства iOS и Android не поддерживаются этим подходом.

## <a name="see-also"></a>См. также
* [Общий доступ в смешанной реальности](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Пространственные привязки Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Пакет SDK для пространственных привязок Azure для Unity</a>