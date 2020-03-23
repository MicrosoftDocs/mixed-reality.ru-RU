---
title: Руководства по Пространственным привязкам Azure — часть 3. Отображение отзывов по пространственной привязке Azure
description: В рамках этого курса вы узнаете, как реализовать функцию распознавания лиц Azure в приложении смешанной реальности.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 11342bada65e963db6393d35c99e2c2fbffe8ff1
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031255"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Отображение отзывов по пространственной привязке Azure

В третьем учебнике серии вы узнаете, как предоставить пользователям информацию о событиях обнаружения и состояниях привязки при использовании Пространственных привязок Azure.

## <a name="objectives"></a>Задачи

* Сведения о том, как настроить панель пользовательского интерфейса для отображения важных сведений о текущем сеансе Пространственных привязок Azure.
* Понимание и изучение элементов обратной связи, которые пакет SDK для Пространственных привязок Azure предоставляет пользователям

## <a name="set-up-asa-feedback-ui-panel"></a>Настройка панели пользовательского интерфейса для обратной связи Пространственных привязок Azure

В окне Hierarchy (Иерархия) щелкните правой кнопкой мыши объект **Instructions** (Инструкции) > **TextContent** и выберите действие **3D Object** (Трехмерный объект) > **Text - TextMeshPro** (Текст — TextMeshPro), чтобы создать текстовый объект TextMeshPro в качестве дочернего для объекта Instructions (Инструкции) > TextContent, и присвойте ему произвольное имя, например **Feedback**:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> Чтобы со сценой было проще работать, отключите параметр <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Видимость сцены) для объекта ParentAnchor, щелкнув значок с изображением глаза слева от этого объекта. Так вы спрячете объект в окне сцены, не изменяя его внутриигровой видимости.

Сохраняя выделение объекта **Feedback**, измените его положение и размер в окне Inspector (Инспектор) так, чтобы он был расположен прямо под текстом инструкций, например так:

* для Rect Transform укажите значение **Pos Y** = -0,24;
* для Rect Transform укажите значение **Width** = 0,555;
* для Rect Transform укажите значение **Height** = 0,1.

Теперь выберите свойства шрифта так, чтобы этот текст хорошо размещался в текстовой зоне, например так:

* в разделе Text Mesh Pro (Script) укажите для **Font Style** (Стиль шрифта) значение Bold (Полужирный);
* в разделе Text Mesh Pro (Script) укажите для **Font Size** (Размер шрифта) значение 0,17;
* в разделе Text Mesh Pro (Script) укажите для **Alignment** (Выравнивание) значения Center (по центру) и Middle (посередине).

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

Сохраняя выделение объекта **Feedback**, в окне Inspector (Инспектор) нажмите кнопку **Add Component** (Добавить компонент), чтобы добавить к этому объекту компонент **Anchor Feedback Script (Script)** (Скрипт обратной связи по привязке — скрипт).

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

Присвойте сам объект **Feedback** полю **Feedback Text** (Текст обратной связи) компонента **Anchor Feedback Script (Script)** (Скрипт обратной связи по привязке — скрипт).

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>Поздравляем!

В этом учебнике вы узнали, как создать панель пользовательского интерфейса для отображения текущего состояния взаимодействия с Пространственной привязкой Azure, чтобы предоставлять пользователю обратную связь в режиме реального времени.
