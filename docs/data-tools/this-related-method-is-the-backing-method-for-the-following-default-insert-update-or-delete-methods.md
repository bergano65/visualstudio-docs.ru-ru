---
title: Этот связанный метод является основным для следующих методов вставки, обновления и удаления по умолчанию
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 1b5579c8916e81e3c49e9d6e24bf37ed85039c03
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851827"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Этот связанный метод является основным для следующих методов вставки, обновления и удаления по умолчанию

Этот связанный метод является базовым методом для следующих по умолчанию `Insert`, `Update`, или `Delete` методы. Если он удаляется, то эти методы также удаляются. Продолжить?

Выбранный `DataContext` метод в настоящее время используется в качестве одного из `Insert`, `Update`, или `Delete` методы для одного из классов сущностей на **реляционный конструктор объектов**. Удаление выбранного метода заставляет класс сущностей, который использовал этот метод, чтобы вернуться к поведению во время выполнения по умолчанию для выполнения вставки, обновления или удаления во время обновления.

## <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Для удаления выбранного метода, вынуждая класс сущностей использовать обновления среды выполнения

- Нажмите кнопку **Да**.

    Выбранный метод удаляется, и любые классы, которые использовали этот метод для переопределения поведения обновления, возвращаются к использованию поведения LINQ to SQL по умолчанию во время выполнения.

## <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Для закрытия окна сообщения, оставляя выбранный метод неизмененным

- Нажмите кнопку **Нет**.

    Окно сообщения закрывается без сохранения изменений.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)