---
title: Методы DataContext (O-R-конструктор)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b7c689ca374fe767c3db4ce8546b5bdcd560a19
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="datacontext-methods-or-designer"></a>Методы DataContext (реляционный конструктор объектов)

<xref:System.Data.Linq.DataContext> методы (в контексте [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) являются методами <xref:System.Data.Linq.DataContext> класс, выполнения хранимых процедур и функций в базе данных.

Класс <xref:System.Data.Linq.DataContext> представляет собой класс [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], который действует как канал между базой данных SQL Server и классами сущностей [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], сопоставленных этой базе данных. <xref:System.Data.Linq.DataContext> Класс содержит строку подключения, а также методы для соединения с базой данных и работы с данными в базе данных. По умолчанию <xref:System.Data.Linq.DataContext> класс содержит несколько методов, которые могут быть вызваны, таких как <xref:System.Data.Linq.DataContext.SubmitChanges%2A> метода, который отправляет обновленные данные из [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] классы в базу данных. Можно также создать дополнительные <xref:System.Data.Linq.DataContext> методы, которые сопоставляются с хранимыми процедурами и функциями. Другими словами, вызов этих пользовательских методов запустит сохраненную процедуру или функцию в базе данных, которой метод <xref:System.Data.Linq.DataContext> сопоставлен. Можно добавить новые методы в класс <xref:System.Data.Linq.DataContext> точно так, как добавлялись бы методы, чтобы расширить любой класс. Тем не менее, в обсуждениях <xref:System.Data.Linq.DataContext> методы в контексте [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], это <xref:System.Data.Linq.DataContext> методы, сопоставляемые хранимых процедур и функций, которые обсуждаются.

## <a name="methods-pane"></a>Область методов

Методы <xref:System.Data.Linq.DataContext>, которые сопоставляются сохраненным процедурам и функциям отображаются в области методов конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Область методов — панель в боковой части **сущностей** области (Главная область конструктора). В области методов перечислены все <xref:System.Data.Linq.DataContext> методы, созданные с помощью [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. По умолчанию область методов пуста; Перетащите хранимых процедур или функций из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] для создания <xref:System.Data.Linq.DataContext> методы и заполнить область методов. Дополнительные сведения см. в разделе [как: DataContext создания методов, сопоставленных с хранимыми процедурами и функциями (O/R-конструктор)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Открывать и закрывать область методов, щелкнув правой кнопкой мыши [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] и выбрав **скрыть область методов** или **Показать область методов**, или используйте сочетание клавиш CTRL + 1.

## <a name="two-types-of-datacontext-methods"></a>Два типа возврата методов DataContext

Методы DataContext сопоставляются хранимым процедурам и функциям в базе данных. Методы DataContext создаются и добавляются в области методов в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Существует два различных типа <xref:System.Data.Linq.DataContext> методов; возвращающие один или несколько результирующих наборов и не возвращающие:

-   Методы <xref:System.Data.Linq.DataContext>, которые возвращают один или несколько результирующих наборов.

     Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно только запускать хранимые процедуры и функции в базе данных и возвращать результаты. Дополнительные сведения см. в разделе [как: DataContext создания методов, сопоставленных с хранимыми процедурами и функциями (O/R-конструктор)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, и <xref:System.Data.Linq.IMultipleResults>.

-   Методы <xref:System.Data.Linq.DataContext>, которые не возвращают результирующих наборов, например операции вставки, обновления и удаления для некоторого класса сущности.

     Создания данного вида <xref:System.Data.Linq.DataContext> метод, если ваше приложение должно запускать хранимые процедуры, вместо того чтобы использовать значение по умолчанию [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] поведение для сохранения измененных данных между классом сущностей и базой данных. Дополнительные сведения см. в разделе [как: назначение хранимых процедур для выполнения обновления, вставки и удаления (конструктор O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Типы возвращаемого значения методов DataContext

Когда хранимые процедуры и функции перетаскиваются из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], тип возвращаемого значения для создаваемого <xref:System.Data.Linq.DataContext> метод отличается в зависимости от того, куда вы сбросили элемент. Если сбрасываете элемент прямо на существующий класс сущностей создает <xref:System.Data.Linq.DataContext> метода с типом возврата класса сущностей; перемещение элементов на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] (в любой области) создает <xref:System.Data.Linq.DataContext> метод, возвращающий автоматически сгенерированный тип. Автоматически сгенерированный тип, который создается, имеет имя, которое соответствует имени сохраненной процедуры или имени функции и свойствам, которые сопоставляют полям, возвращенным сохраненной процедурой или функцией.

> [!NOTE]
> Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы просмотреть или изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод, выберите его и проверьте **тип возвращаемого значения** свойство в **свойства** окна. Дополнительные сведения см. в разделе [способ: измените тип возврата метода DataContext (O/R-конструктор)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Объекты, перетаскиваемые из базы данных в область реляционного конструктора объектов, автоматически получают имена, основанные на имени объектов в базе данных. Если несколько раз перетащить один объект, к концу имени будет добавлен номер, чтобы различить имена экземпляров. Если имена объектов базы данных содержат пробелы или символы, которые не поддерживаются в Visual Basic или в C#, то пробел или недопустимый символ будет заменен символом подчеркивания.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Хранимые процедуры](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Как: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (O/R-конструктор)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Как: назначение хранимых процедур для выполнения обновления, вставки и удаления (конструктор O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Пошаговое руководство. Настройка поведения вставки, обновления и удаления классов сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Пошаговое руководство: Создание классов LINQ to SQL (конструктор O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)