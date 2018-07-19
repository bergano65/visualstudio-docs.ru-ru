---
title: Выбранный класс невозможно удалить, потому что он используется как тип возвращаемого значения одного или нескольких методов DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 21ef0f86d701c899328044a03cde8035a1e7292d
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174215"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Выбранный класс невозможно удалить, потому что он используется как тип возвращаемого значения одного или нескольких методов DataContext

Тип возврата одного или нескольких методов <xref:System.Data.Linq.DataContext> это выбранный класс сущностей. Удаление класса сущностей, который используется как тип возвращаемого значения для <xref:System.Data.Linq.DataContext> метод приводит к компиляции проекта переход на другой. Чтобы удалить выбранный класс сущностей, Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые его используют, и задайте их типам возврата другой класс сущностей.

Для возврата типов возврата из <xref:System.Data.Linq.DataContext> методы в их исходный тип создан, сначала удалите <xref:System.Data.Linq.DataContext> метода из **методы** области и затем перетащите объект из **обозревателя серверов** / **Обозреватель баз данных** на **реляционный конструктор объектов** еще раз.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Определить <xref:System.Data.Linq.DataContext> методы, которые используются класс сущностей в качестве возвращаемого типа, выбрав <xref:System.Data.Linq.DataContext> метод в **методы** области, а также проверять **тип возвращаемого значения** свойство в **Свойства** окна.

2. Задайте **тип возвращаемого значения** другой класс сущностей или сначала удалите <xref:System.Data.Linq.DataContext> метод из области методов.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)