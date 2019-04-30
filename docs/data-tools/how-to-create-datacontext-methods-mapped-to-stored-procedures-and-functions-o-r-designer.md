---
title: Практическое руководство. создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: dc2b1c25f9b4cf9bc777eefd0c95985a534799b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566512"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)

Можно добавить хранимые процедуры и функции для **реляционный конструктор объектов** как <xref:System.Data.Linq.DataContext> методы. Вызов метода и передача в обязательные параметры запускает сохраненную процедуру или функцию на базе данных и возвращает данные в тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>. Подробные сведения о <xref:System.Data.Linq.DataContext> методы, см. в разделе [методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Также можно использовать хранимые процедуры, чтобы переопределить значение по умолчанию [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] поведение во время выполнения, которая выполняет вставки, обновления и удаления, когда изменения сохраняются из классов сущностей в базу данных. Дополнительные сведения см. в разделе [Как назначить хранимые процедуры для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Создание методов DataContext

Можно создать <xref:System.Data.Linq.DataContext> методов путем перетаскивания сохраненных процедур или функций из <strong>обозреватель серверов или ** обозреватель баз данных</strong> на **реляционный конструктор объектов**.

> [!NOTE]
> Тип возвращаемого значения создаваемого <xref:System.Data.Linq.DataContext> метод отличается в зависимости от того, где завершается перетаскивание хранимой процедуры или функции в **реляционный конструктор объектов**. Если сбрасываете элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возвращаемого значения класса сущностей. Перетаскивая элементы на пустую область **реляционный конструктор объектов** создает <xref:System.Data.Linq.DataContext> метод, который возвращает автоматически сгенерированный тип. Можно изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> после его добавления в область **методов**. Чтобы просмотреть или изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>, выберите его и проверьте свойство **тип возвращаемого значения** в окне **Свойства**. Дополнительные сведения см. в разделе [Как изменить тип возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Для создания методов DataContext, которые возвращают автоматически сгенерированные типы

1. В **обозревателя серверов** или **обозреватель баз данных**, разверните **хранимые процедуры** узел базы данных, с которым вы работаете.

2. Найдите нужную сохраненную процедуру и перетащите его на пустую область **реляционный конструктор объектов**.

     Метод <xref:System.Data.Linq.DataContext> создается с автоматически сгенерированным типом возвращаемого значения и появляется в области **Методы**.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Чтобы создать методы DataContext, которые имеют тип возврата класса сущностей

1. В **обозревателя серверов** или **обозреватель баз данных**, разверните **хранимые процедуры** узел базы данных, с которым вы работаете.

2. Найдите нужную сохраненную процедуру и перетащите его на существующий класс сущностей в **реляционный конструктор объектов**.

     Метод <xref:System.Data.Linq.DataContext> создается с типом возвращаемого значения выбранного класса сущностей и появляется в области **Методы**.

> [!NOTE]
> Дополнительные сведения об изменении типа возвращаемого значения существующих <xref:System.Data.Linq.DataContext> методы, см. в разделе [как: изменить тип возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)
- [Пошаговое руководство: Создание LINQ для классов SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq) (Знакомство с LINQ в Visual Basic)
- [LINQ в C#](/dotnet/csharp/linq/linq-in-csharp)