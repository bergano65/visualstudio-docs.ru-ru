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
ms.openlocfilehash: 76f7fcff3f05d38dff230799785e659417c6dcc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Выбранный класс невозможно удалить, потому что он используется как тип возвращаемого значения одного или нескольких методов DataContext

Тип возврата одного или нескольких методов <xref:System.Data.Linq.DataContext> это выбранный класс сущностей. Удаление класса сущностей, который используется в качестве типа возврата для метода <xref:System.Data.Linq.DataContext>, вызовет ошибку компиляции проекта. Чтобы удалить выбранный класс сущностей, Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые его используют, и задайте их типам возврата другой класс сущностей.

Для возврата типов возврата <xref:System.Data.Linq.DataContext> методов к их исходным автоматически сгенерированным типам, сначала удалите <xref:System.Data.Linq.DataContext> метод из области методов и потом перетащите объект из **обозревателя серверов** / **Обозреватель баз данных** снова в реляционный конструктор.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Определить <xref:System.Data.Linq.DataContext> методы, которые используются класс сущностей в качестве типа возврата, выбрав <xref:System.Data.Linq.DataContext> метод в методах области и проверив **тип возвращаемого значения** свойство в **свойства** окна .

2. Задать **тип возвращаемого значения** на другой класс сущностей или удалите <xref:System.Data.Linq.DataContext> метод из области методов.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)