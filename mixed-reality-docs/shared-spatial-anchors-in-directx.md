---
title: Общие пространственных привязки в DirectX
description: Описаны способы синхронизации двух устройств HoloLens, предоставив пространственных привязки.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, синхронизировать, пространственных привязки, перемещение, многопользовательскую, представление, сценарий, в пошаговом руководстве, пример кода, Azure, Azure пространственных привязки, ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605063"
---
# <a name="shared-experiences-in-directx"></a>Публикацию в DirectX

Общий интерфейс, где несколько пользователей, каждый из которых собственные HoloLens, устройстве iOS или Android, вместе просматривать и взаимодействовать с тем же голограмма, который расположен в фиксированной точки в пространстве. Это достигается через предоставление совместного доступа пространственных привязки.

## <a name="azure-spatial-anchors"></a>Пространственная привязка Azure

Можно использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для создания устойчивых облачных резервных пространственных привязки, что приложение можно найти в нескольких HoloLens, iOS и устройств Android.  Совместное использование общих пространственных привязки на нескольких устройствах, каждый пользователь может видеть содержимое отображается относительно эту привязку, в том же физическом расположении.  Это позволяет выполнять публикацию в режиме реального времени.

Можно также использовать <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">привязки пространственных Azure</a> для асинхронной голограмма сохраняемости на устройствах Android, iOS и HoloLens.  По электронной почте на привязку пространственных надежные облачные, несколько устройств можно наблюдать за же материализованных голограмма со временем, даже если эти устройства не существуют друг с другом в то же время.

Чтобы приступить к работе, создания общих возможностей в приложении HoloLens, изучите 5-минутные <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">быстрого запуска Azure пространственных привязки HoloLens</a>.

После того, как приступить к работе с пространственными привязки Azure, вы можете затем <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">создать и найдите привязки на HoloLens</a>.  Доступны пошаговые руководства для <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android и iOS</a> также, что позволяет совместно использовать же привязки на всех устройствах.

## <a name="local-anchor-transfers"></a>Передача локального привязки

В ситуациях, когда невозможно использовать Azure пространственных привязки [передачи локального привязки](local-anchor-transfers-in-directx.md) включить одно устройство HoloLens Экспорт привязки импортируемой второе устройство HoloLens.  Обратите внимание, что такой подход обеспечивает менее надежны, отзыв привязки, чем пространственных привязки Azure устройств iOS и Android, этот подход не поддерживаются.

## <a name="see-also"></a>См. также
* [Общие возможности в смешанной реальности](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure пространственных привязки</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure пространственных привязки пакета SDK для HoloLens</a>