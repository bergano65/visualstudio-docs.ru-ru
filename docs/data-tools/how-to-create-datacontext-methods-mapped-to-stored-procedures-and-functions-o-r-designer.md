---
title: 'Практическое: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 53829ffaeab44eb758b1850f5619de43db31e589
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089689"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Практическое: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)
Можно добавить хранимые процедуры и функции для **реляционный конструктор объектов** как <xref:System.Data.Linq.DataContext> методы. Вызов метода и передача в обязательные параметры запускает хранимую процедуру или функцию в базе данных и возвращает данные в тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод. Подробные сведения о <xref:System.Data.Linq.DataContext> методы, см. в разделе [методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
>  Также можно использовать хранимые процедуры, чтобы переопределить значение по умолчанию [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] поведение во время выполнения, которая выполняет вставки, обновления и удаления, когда изменения сохраняются из классов сущностей в базу данных. Дополнительные сведения см. в разделе [как: назначение хранимых процедур для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Создание методов DataContext
 Можно создать <xref:System.Data.Linq.DataContext> методов путем перетаскивания сохраненных процедур или функций из ** обозреватель серверов или **обозреватель баз данных** на **реляционный конструктор объектов**.

> [!NOTE]
>  Тип возвращаемого значения создаваемого <xref:System.Data.Linq.DataContext> метод отличается в зависимости от того, где завершается перетаскивание хранимой процедуры или функции в **реляционный конструктор объектов**. Если сбрасываете элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата класса сущностей. Перетаскивая элементы на пустую область **реляционный конструктор объектов** создает <xref:System.Data.Linq.DataContext> метод, который возвращает автоматически сгенерированный тип. Можно изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод после его добавления **методы** области. Чтобы проверить или изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод, выберите его и проверьте **тип возвращаемого значения** свойство в **свойства** окна. Дополнительные сведения см. в разделе [способы: измените тип возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Для создания методов DataContext, которые возвращают автоматически сгенерированные типы

1.  В **обозревателя серверов** или **обозреватель баз данных**, разверните **хранимые процедуры** узел базы данных, с которым вы работаете.

2.  Найдите нужную сохраненную процедуру и перетащите его на пустую область **реляционный конструктор объектов**.

     <xref:System.Data.Linq.DataContext> Метод создается с автоматически сгенерированным типом возвращаемого значения и появляется в **методы** области.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Чтобы создать методы DataContext, которые имеют тип возвращаемого значения класса сущностей

1.  В **обозревателя серверов** или **обозреватель баз данных**, разверните **хранимые процедуры** узел базы данных, с которым вы работаете.

2.  Найдите нужную сохраненную процедуру и перетащите его на существующий класс сущностей в **реляционный конструктор объектов**.

     <xref:System.Data.Linq.DataContext> Метод создается с типом возвращаемого значения выбранного класса сущностей и появляется в **методы** области.

> [!NOTE]
>  Сведения об изменении типа возвращаемого значения существующих <xref:System.Data.Linq.DataContext> методы, см. в разделе [способы: измените тип возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)
- [Пошаговое руководство: Создание LINQ для классов SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq) (Знакомство с LINQ в Visual Basic)
- [LINQ в C#](/dotnet/csharp/linq/linq-in-csharp)