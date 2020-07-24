---
title: Руководства по Пространственным привязкам Azure, часть 4 Отображение отзывов по Пространственным привязкам Azure
description: Пройдите этот курс и узнайте, как реализовать Пространственные привязки Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d221a7e64bda7a6dabf76b60c7bff7c6333666ef
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305980"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4. Отображение отзывов по Пространственным привязкам Azure

В этом руководстве показано, как предоставить пользователям обратную связь о событиях обнаружения и состояниях привязки при использовании Пространственных привязок Azure.

## <a name="objectives"></a>Задачи

* Узнать, как настроить панель пользовательского интерфейса для отображения важных сведений о текущем сеансе Пространственных привязок Azure.
* Узнать об элементах обратной связи, которые пакет SDK для Пространственных привязок Azure предоставляет пользователям.

## <a name="setting-up-asa-feedback-panel"></a>Настройка панели пользовательского интерфейса для предоставления обратной связи о Пространственных привязках Azure

В окне иерархии щелкните правой кнопкой мыши объект **Instructions** > **TextContent** (Инструкции > TextContent). Выберите **3D Object** > **Text - TextMeshPro** (Трехмерный объект > Текст — TextMeshPro), чтобы создать текстовый объект TextMeshPro как дочерний объект объекта TextContent.

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> Чтобы со сценой было проще работать, отключите параметр <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Видимость сцены) для объекта ParentAnchor, щелкнув значок с изображением глаза слева от этого объекта. Так вы спрячете объект в окне сцены, не изменяя его внутриигровой видимости.

Переименуйте созданный текстовый объект (TMP) в **Feedback** (Обратная связь), а затем в окне инспектора измените его расположение и размер, чтобы он размещался под текстом инструкции, например:

* измените значение **Pos Y** (Позиция Y) компонента Rect Transform на -0,24;
* измените значение **Width** (Ширина) компонента Rect Transform на 0,555;
* измените значение **Height** (Высота) компонента Rect Transform на 0,1.

Теперь выберите свойства шрифта так, чтобы текст размещался в текстовой зоне, например:

* измените значение **Font Style** (Стиль шрифта) текстового компонента TextMeshPro на Bold;
* измените значение **Font Size** (Размер шрифта) текстового компонента TextMeshPro на 0.17;
* измените значение **Alignment** (Выравнивание) текстового компонента TextMeshPro на Center (По центру) и Middle (Посередине).

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

В окне иерархии выберите объект **Feedback** (Обратная связь), а затем в окне инспектора используйте кнопку **Add Component** (Добавить компонент), чтобы добавить компонент **Anchor Feedback Script (Script)** (Скрипт обратной связи по привязке — скрипт) и настроить его следующим образом.

* В поле **Feedback Text** (Текст обратной связи) компонента **Anchor Feedback Script (Script)** (Скрипт обратной связи по привязке — скрипт) укажите сам объект **Feedback** (Обратная связь).

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>Поздравляем!

В этом руководстве показано, как создать панель пользовательского интерфейса. На ней отображается текущее состояние взаимодействия с Пространственными привязками Azure для предоставления пользователям обратной связи в реальном времени.

[Следующее руководство: 5. Пространственные привязки Azure для Android и iOS](mr-learning-asa-05.md)