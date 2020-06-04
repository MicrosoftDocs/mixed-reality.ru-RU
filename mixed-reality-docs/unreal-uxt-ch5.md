---
title: 5. Добавление кнопки и сброс расположений фигур
description: Часть 5 руководства по созданию простого приложения для игры в шахматы с помощью Unreal Engine 4 и подключаемого модуля средств разработки пользовательского интерфейса (UX) из набора средств для смешанной реальности
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, смешанная реальность, учебник, начало работы, MRTK, UXT, средства разработки пользовательского интерфейса, средства UX, документация
ms.openlocfilehash: 77fe2b59db970a2ac4b531d69efec6794478f7d5
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519996"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Добавление кнопки и сброс расположений фигур

В этом разделе мы продолжим демонстрировать возможности подключаемого модуля средств разработки пользовательского интерфейса (UX) для смешанной реальности и развивать функциональность приложения для игры в шахматы. Вы создадите новую функцию и узнаете, как создать в схеме ссылки на субъекты из уровня.

## <a name="objectives"></a>Задачи

* Добавление кнопки в проект.
* Создание функции "Сброс расположения", которая переносит фигуру в исходное расположение.
* Подключение кнопки к триггеру, чтобы ее нажатие активировало только что созданную функцию.

## <a name="create-a-function-to-reset-location"></a>Создание функции для сброса расположения

1.  Откройте элемент **WhiteKing**. На панели **My Blueprint** (Моя схема) нажмите кнопку "+" рядом с разделом **Functions** (Функции), чтобы создать новую функцию. Присвойте этой функции имя Reset Location. 

2.  В только что созданной схеме **Reset Location** (Сброс расположения) перетащите закрепление выполнения и отпустите его в любом месте на сетке схемы, чтобы вызвать узел **SetActorRelativeTransform**. Эта функция задает для субъекта преобразование (расположение, поворот и масштабирование) относительно родительского элемента. С помощью этой функции мы можем вернуть исходное расположение короля на доске, даже если сама доска перемещена из исходного положения. Создайте узел **Make Transform** (Создать преобразование) со значением X=-26, Y=4, Z=0 для параметра Location (Расположение) и подключите его к вводу New Relative Transform (Новое относительное преобразование). 

![Функция сброса расположения](images/unreal-uxt/5-function.PNG)

3.  Скомпилируйте и сохраните **WhiteKing**. Вернитесь в главное окно. 

## <a name="add-a-button"></a>Добавление кнопки

1.  В папке **Blueprints** создайте новую схему, которая является подклассом для SimpleButton. Субъект-схема SimpleButton реализует трехмерную кнопку и предоставляется в составе подключаемого модуля средств UX. Присвойте этой кнопке имя ResetButton и дважды щелкните ее, чтобы открыть соответствующую схему. 

![Создайте новую схему как подкласс SimpleButton](images/unreal-uxt/5-subclass.PNG)

2.  На панели **Components** (Компоненты) щелкните **PressableButton (Inherited)** . На панели Details (Сведения) прокрутите экран вниз до раздела **Events** (События). Нажмите зеленую кнопку со знаком "плюс" рядом с событием **On Button Pressed** (По нажатию кнопки), чтобы добавить в граф событий событие **On Button Pressed** (По нажатию кнопки), которое будет активироваться при нажатии этой кнопки. Из этого события мы будем вызывать функцию сброса расположения для элемента WhiteKing. Для этого нам нужно получить из уровня ссылку на субъект WhiteKing. 

3.  На панели **My Blueprint** (Моя схема) найдите раздел **Variables** (Переменные) и нажмите кнопку **+** , которая добавит новую переменную. Присвойте этой переменной имя WhiteKing. На панели Details (Сведения) щелкните раскрывающийся список рядом с полем **Variable Type** (Тип переменной), затем выполните поиск по слову WhiteKing и выберите **Object Reference** (Ссылка на объект). Наконец, установите флажок **Instance Editable** (Редактируемый экземпляр). Это позволит задавать значение переменной из уровня Main. 

![Создание переменной](images/unreal-uxt/5-var.PNG)

4.  Перетащите переменную WhiteKing из раздела **My Blueprint > Variables** (Моя схема > Переменные) на граф Reset Button Event Graph (Граф событий кнопки сброса). Выберите **Get WhiteKing** (Получить элемент WhiteKing). 

5.  Перетащите закрепление вывода WhiteKing и отпустите его для размещения нового узла. Выберите функцию **Reset Location** (Сброс расположения). Наконец, перетащите выходное закрепление выполнения из события **On Button Pressed** (По нажатию кнопки) к входному закреплению выполнения функции **Reset Location** (Сброс расположения). **Скомпилируйте** и **сохраните** схему ResetButton, а затем вернитесь в главное окно. 

![Вызов функции сброса расположения из события нажатия кнопки](images/unreal-uxt/5-callresetloc.PNG)

6.  Перетащите элемент **ResetButton** в окно просмотра и задайте для его расположения значение X=50, Y=-25, Z=10. В разделе **Default** (По умолчанию) задайте для переменной WhiteKing значение **WhiteKing**.

![Указание переменной](images/unreal-uxt/5-buttonlevel.PNG)

Теперь у вас есть приложение смешанной реальности с фигурой и доской, которые можно захватывать рукой, а также работающая кнопка для восстановления расположения шахматной фигуры. Версия приложения по состоянию на текущий момент размещена в репозитории [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp). Не ограничивайте себя рамками этого учебника и настройте все остальные шахматные фигуры так, чтобы при нажатии этой кнопки восстанавливалось положение всей доски.

![Готовая сцена в окне просмотра](images/unreal-uxt/5-endscene.PNG)

[Следующий раздел: 6. Упаковка и развертывание на устройстве или в эмуляторе](unreal-uxt-ch6.md)