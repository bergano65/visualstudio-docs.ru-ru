---
title: Сопоставьте методы DataContext с sprocs и функциями
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e6926631cfd9d04992d92553a346348ea18af847
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038339"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)

В **конструктор O/R** можно добавлять хранимые процедуры и функции в качестве <xref:System.Data.Linq.DataContext> методов. Вызов метода и передача в обязательные параметры запускает сохраненную процедуру или функцию на базе данных и возвращает данные в тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>. Подробные сведения о <xref:System.Data.Linq.DataContext> методах см. в разделе [методы DataContext (реляционный конструктор R)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Можно также использовать хранимые процедуры, чтобы переопределить поведение во время выполнения по умолчанию, [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] которое выполняет операции вставки, обновления и удаления при сохранении изменений из классов сущностей в базу данных. Дополнительные сведения см. в разделе [Практическое руководство. назначить хранимые процедуры для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Создание методов DataContext

Методы можно создавать <xref:System.Data.Linq.DataContext> путем перетаскивания хранимых процедур или функций из <strong>Обозреватель сервера или * * Обозреватель базы данных</strong> в **конструктор O/R**.

> [!NOTE]
> Тип возвращаемого значения созданного <xref:System.Data.Linq.DataContext> метода зависит от места удаления хранимой процедуры или функции в **конструкторе O/R**. Если сбрасываете элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возвращаемого значения класса сущностей. При удалении элементов в пустую область **конструктора объектов (O/R** ) создается <xref:System.Data.Linq.DataContext> метод, который возвращает автоматически созданный тип. Можно изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> после его добавления в область **методов**. Чтобы просмотреть или изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>, выберите его и проверьте свойство **тип возвращаемого значения** в окне **Свойства**. Дополнительные сведения см. в разделе [инструкции. изменение типа возвращаемого значения метода DataContext (реляционный конструктор данных)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Для создания методов DataContext, которые возвращают автоматически сгенерированные типы

1. В **Обозреватель сервера** или **Обозреватель базы данных**разверните узел **хранимые процедуры** базы данных, с которой вы работаете.

2. Выделите нужную хранимую процедуру и перетащите ее на пустую область **конструктора O/R**.

     Метод <xref:System.Data.Linq.DataContext> создается с автоматически сгенерированным типом возвращаемого значения и появляется в области **Методы**.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Чтобы создать методы DataContext, которые имеют тип возврата класса сущностей

1. В **Обозреватель сервера** или **Обозреватель базы данных**разверните узел **хранимые процедуры** базы данных, с которой вы работаете.

2. Выделите нужную хранимую процедуру и перетащите ее на существующий класс сущностей в **реляционном конструкторе**объектов.

     Метод <xref:System.Data.Linq.DataContext> создается с типом возвращаемого значения выбранного класса сущностей и появляется в области **Методы**.

> [!NOTE]
> Дополнительные сведения об изменении типа возвращаемого значения существующих <xref:System.Data.Linq.DataContext> методы, см. в разделе [как: Изменение типа возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>См. также раздел

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Методы DataContext (реляционный конструктор R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Пошаговое руководство. Создание классов LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq) (Знакомство с LINQ в Visual Basic)
- [LINQ в C#](/dotnet/csharp/linq/linq-in-csharp)
