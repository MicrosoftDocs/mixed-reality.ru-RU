---
title: Публикацию в Unity
description: Совместное использование одной голограммы между несколькими пользователями в приложении Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Совместное использование, привязки, WorldAnchor, MR, совместное использование 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure пространственных привязки, ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605073"
---
# <a name="shared-experiences-in-unity"></a>Публикацию в Unity

Общий интерфейс, где несколько пользователей, каждый из которых собственные HoloLens, устройстве iOS или Android, вместе просматривать и взаимодействовать с тем же голограмма, который расположен в фиксированной точки в пространстве. Это достигается через предоставление совместного доступа пространственных привязки.

## <a name="azure-spatial-anchors"></a>Пространственная привязка Azure

Можно использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для создания устойчивых облачных резервных пространственных привязки, что приложение можно найти в нескольких HoloLens, iOS и устройств Android.  Совместное использование общих пространственных привязки на нескольких устройствах, каждый пользователь может видеть содержимое отображается относительно эту привязку, в том же физическом расположении.  Это позволяет выполнять публикацию в режиме реального времени.

Можно также использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для асинхронной голограмма сохраняемости на устройствах Android, iOS и HoloLens.  По электронной почте на привязку пространственных надежные облачные, несколько устройств можно наблюдать за же материализованных голограмма со временем, даже если эти устройства не существуют друг с другом в то же время.

Чтобы приступить к работе, создания общих возможностей в Unity, изучите 5-минутные <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">краткие руководства по Azure пространственных привязки Unity</a>.

После того, как приступить к работе с пространственными привязки Azure, вы можете затем <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">создать и найдите привязки в Unity</a>.

## <a name="local-anchor-transfers"></a>Передача локального привязки

В ситуациях, когда невозможно использовать Azure пространственных привязки [передачи локального привязки](local-anchor-transfers-in-unity.md) включить одно устройство HoloLens Экспорт привязки импортируемой второе устройство HoloLens.  Обратите внимание, что такой подход обеспечивает менее надежны, отзыв привязки, чем пространственных привязки Azure устройств iOS и Android, этот подход не поддерживаются.

## <a name="see-also"></a>См. также
* [Общие возможности в смешанной реальности](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure пространственных привязки</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure пространственных привязки пакета SDK для Unity</a>