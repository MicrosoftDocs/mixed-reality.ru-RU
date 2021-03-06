---
title: Масштаб
description: Ключом к отображению содержимого, которое выглядит реалистично в виде голограммы, является как можно более точная имитация визуальных статистических данных реального мира.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, стиль, Дизайн
ms.openlocfilehash: eeec28fbf98cf4386a57cde4452cd3f8977d7780
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437504"
---
# <a name="scale"></a>Масштаб

Ключом к отображению содержимого, которое выглядит реалистично в виде голограммы, является как можно более точная имитация визуальных статистических данных реального мира. Это означает обработку как можно большего числа значимых визуальных подсказок (из реального мира), чтобы понять, где находятся объекты, насколько они велики и из его они сделаны. Масштаб объекта — одна из наиболее важных визуальных подсказок, позволяющая средству просмотра понять размер объекта, а также подсказки в его расположении (особенно для объектов, имеющих известный размер). Кроме того, просмотр объектов в реальном масштабе наблюдался как один из основных принципов работы с различными преимуществами для смешанной реальности, что не было возможно при просмотре на основе экрана ранее.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Как предложить масштаб объектов и сред

Существует множество способов предложить масштаб объекта, некоторые из которых имеют возможные последствия для других искусственного факторов. Основной целью является простое отображение объектов в реальном размере и поддержание этого реалистичного размера по мере перемещения пользователей. Это означает, что голограммы будут занимать другую часть визуального угла пользователя по мере того, как они появляются ближе или дальше, так же, как и реальные объекты.

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>Использование расстояния от объектов по мере их представления пользователю

Одним из распространенных способов является использование расстояния от объектов по мере их представления пользователю. Например, рассмотрим визуализацию крупного автомобиля в начале пользователя. Если машина находилась непосредственно перед ними, то она будет слишком большой, чтобы уместиться в поле зрения пользователя. Это потребует, чтобы пользователь переместит заголовок и текст, чтобы понять, что объект будет полностью понятен. Если машина была размещена в другом месте (в комнате), пользователь может оценить масштаб, просматривая объект в поле зрения, а затем переместив его ближе к нему, чтобы подробно изучить области.

:::row:::
    :::column:::
        **[Компания Volvo использовал этот метод для создания шоврумного](https://www.youtube.com/watch?v=DilzwF90vec)** интерфейса для нового автомобиля, используя масштаб holographic-автомобиля так, чтобы он был реалистичным и интуитивно понятным для пользователя. Опыт начинается с голограммы автомобиля на физическую таблицу, позволяя пользователю понять общий размер и форму модели. На более позднем опыте автомобиля увеличивается до большего масштаба (за пределами поля представления), но, так как пользователь уже получил рамку ссылки из модели меньшего размера, они могут адекватно перемещаться по функциям автомобиля.<br>
        <br>
        *Образ: возможности компания Volvo автомобилей для HoloLens*
    :::column-end:::
        :::column:::
       ![Компания Volvo автомобилей для HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Используйте голограммы, чтобы изменить реальное пространство пользователя

Другой способ — использовать голограммы, чтобы изменить реальное пространство пользователя, заменить существующие стены или цеилингс с окружениями или добавить "отверстия" или "Windows", что позволит объектам с избыточным размером показалось бы «разбиваться на» физическое пространство. Например, большое дерево может не уместиться в рабочих комнатах большинства пользователей, но, помещая виртуальный трансобъектный уровень на их потолк, физическое пространство расширяется до виртуального. Это позволяет пользователю пройти по базовому принципу виртуального дерева и собрать представление о том, как оно будет выглядеть в реальной жизни, а затем найти, чтобы увидеть, что он выходит далеко за пределы физического пространства комнаты.

:::row:::
    :::column:::
        **[Minecraft разработала концепцию,](https://minecraft.net/)** используя аналогичную методику. Добавив виртуальное окно в физическую поверхность комнаты, существующие объекты в комнате помещаются в контексте значительно большей среды, помимо ограничений физического масштабирования комнаты.<br>
        <br>
        *Образ: интерфейс Minecraft концепция для HoloLens*
    :::column-end:::
        :::column:::
       ![Принципы работы Minecraft для HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Эксперименты с масштабом

В некоторых случаях проектировщики экспериментируют с изменением масштаба (путем изменения отображаемого "фактического" размера объекта), сохраняя при этом одну точку объекта, чтобы приблизительно оценить объект в средстве просмотра без фактического перемещения. В некоторых случаях это было протестировано как способ имитации и закрытия просмотра элементов, сохраняя при этом возможности просмотра виртуального содержимого ближе, чем представится «зона отдыха».

Однако это может создать несколько возможных артефактов.
* Для виртуальных объектов, представляющих некоторый объект с известным размером в средстве просмотра, изменение масштаба без изменения позиции приводит к конфликту визуальных подсказок — глаза могут по-прежнему видеть объект с некоторой глубиной из-за верженце подсказок (см. [комфортное](comfort.md) Дополнительные сведения об этом см. в статье, но размер выступает в качестве монокулар подсказки, которую объект может получить ближе. Эти конфликтующие подсказки ведут к запутанным восприятиям — читатели часто видят объект как есть (из-за постоянной частоты), но быстро увеличиваются.
* В некоторых случаях изменение масштаба рассматривается как подсказка "надвигающихся", где объект может или не отображаться для изменения масштаба средством просмотра, но кажется, что он перемещается непосредственно в глаза средства просмотра (что может быть неудобной неожиданностью).
* С помощью областей сравнения в реальном мире такие изменения масштабирования иногда отображаются как изменение расположения по нескольким осям — объекты могут перетаскиваться в нижнюю часть вместо того, чтобы перемещаться ближе друг к другу (аналогично плоской проекции трехмерного перемещения в некоторых случаях).
* Наконец, для объектов без известного размера (например, произвольных фигур с произвольными размерами, элементами пользовательского интерфейса и т. д.) изменение масштаба может функционировать как способ имитировать изменения на расстоянии, то есть у зрителей не будет столько же верхних элементов, сколько уже существует. Изучите истинный размер или расположение объекта, чтобы масштаб можно было обрабатывать как важный элемент.

<br>

---

## <a name="see-also"></a>См. также
* [Цвет, свет и материалы](color,-light-and-materials.md)
* [Оформление текста](typography.md)
* [Проектирование пространственного звука](spatial-sound-design.md)
