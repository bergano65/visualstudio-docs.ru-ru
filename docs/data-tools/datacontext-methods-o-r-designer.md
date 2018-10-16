---
title: Методы DataContext (реляционный конструктор объектов)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3d8e3a39c79b5dee339c8835c78143277f3015f6
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756133"
---
# <a name="datacontext-methods-or-designer"></a>Методы DataContext (реляционный конструктор объектов)

<xref:System.Data.Linq.DataContext> методы (в контексте [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) являются методами <xref:System.Data.Linq.DataContext> класс, который будет выполнять хранимые процедуры и функции в базе данных.

Класс <xref:System.Data.Linq.DataContext> представляет собой класс [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], который действует как канал между базой данных SQL Server и классами сущностей [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], сопоставленных этой базе данных. <xref:System.Data.Linq.DataContext> Класс содержит строку подключения и методы для соединения с базой данных и работы с данными в базе данных. По умолчанию <xref:System.Data.Linq.DataContext> класс содержит несколько методов, которые можно вызывать, например <xref:System.Data.Linq.DataContext.SubmitChanges%2A> метода, который отправляет обновленные данные из [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] классы в базу данных. Вы также можете создать дополнительные <xref:System.Data.Linq.DataContext> методы, которые сопоставляются с хранимыми процедурами и функциями. Другими словами, вызов этих пользовательских методов запускает хранимую процедуру или функцию в базе данных к которому <xref:System.Data.Linq.DataContext> сопоставляется метод. Можно добавить новые методы в класс <xref:System.Data.Linq.DataContext> точно так, как добавлялись бы методы, чтобы расширить любой класс. Тем не менее, в обсуждениях <xref:System.Data.Linq.DataContext> методы в контексте **реляционный конструктор объектов**, это <xref:System.Data.Linq.DataContext> методы, которые сопоставляются с хранимыми процедурами и функциями, которые обсуждаются.

## <a name="methods-pane"></a>Область методов

<xref:System.Data.Linq.DataContext> методы, которые сопоставляются с хранимыми процедурами и функциями, отображаются в **методы** области **реляционный конструктор объектов**. **Методы** панель — панель вдоль края **сущностей** области (Главная область конструктора). **Методы** области перечислены все <xref:System.Data.Linq.DataContext> методы, которые созданы с помощью **реляционный конструктор объектов**. По умолчанию **методы** панель пуста; перетащите сохраненные процедуры или функции из **обозревателя серверов** или **обозреватель баз данных** на **реляционный конструктор объектов**  для создания <xref:System.Data.Linq.DataContext> методы и заполнить **методы** области. Дополнительные сведения см. в разделе [как: методов создания DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Откройте и закройте область методов, щелкнув правой кнопкой мыши **реляционный конструктор объектов** и выбрав **скрыть область методов** или **Показать область методов**, или используйте сочетание клавиш  **CTRL**+**1**.

## <a name="two-types-of-datacontext-methods"></a>Два типа методов DataContext

Методы DataContext сопоставляются хранимым процедурам и функциям в базе данных. Можно создать и добавить методы DataContext на **методы** области **реляционный конструктор объектов**. Существует два различных типа <xref:System.Data.Linq.DataContext> методов; возвращающие один или несколько результирующих наборов и не возвращающие:

-   Методы <xref:System.Data.Linq.DataContext>, которые возвращают один или несколько результирующих наборов.

     Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно только запускать хранимые процедуры и функции в базе данных и возвращать результаты. Дополнительные сведения см. в разделе [как: методов создания DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, и <xref:System.Data.Linq.IMultipleResults>.

-   Методы <xref:System.Data.Linq.DataContext>, которые не возвращают результирующих наборов, например операции вставки, обновления и удаления для некоторого класса сущности.

     Получения <xref:System.Data.Linq.DataContext> метод, когда у приложения есть для запуска хранимых процедур, вместо того чтобы использовать значение по умолчанию [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] поведение для сохранения измененных данных между классом сущностей и базой данных. Дополнительные сведения см. в разделе [как: назначение хранимых процедур для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Типы возвращаемого значения методов DataContext

При перетаскивании хранимые процедуры и функции из **обозревателя серверов** или **обозреватель баз данных** на **реляционный конструктор объектов**, тип возвращаемого значения создаваемого <xref:System.Data.Linq.DataContext> метод отличается в зависимости от того, где вы сбросили элемент. Сбрасываете элемент прямо на существующий класс сущностей создает <xref:System.Data.Linq.DataContext> метод с типом возвращаемого значения класса сущностей; перемещение элементов на пустую область **реляционный конструктор объектов** (в любой области) создает <xref:System.Data.Linq.DataContext> метод который возвращает автоматически сгенерированный тип. Автоматически созданный тип имеет имя, которое соответствует хранимой процедуры или имя функции и свойства, которые сопоставляются поля, возвращаемые хранимой процедурой или функцией.

> [!NOTE]
> Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы проверить или изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод, выберите его и проверьте **тип возвращаемого значения** свойство в **свойства** окна. Дополнительные сведения см. в разделе [способы: измените тип возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Объекты, перетаскиваемые из базы данных в область реляционного конструктора объектов именуются автоматически, на основе имени объектов в базе данных. Если несколько раз перетащить один объект число добавляется в конец нового имени, который различить имена экземпляров. Если имена объектов базы данных содержат пробелы или символы, которые не поддерживаются в Visual Basic или в C#, то пробел или недопустимый символ будет заменен символом подчеркивания.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Хранимые процедуры](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Практическое: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Практическое: назначение хранимых процедур для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Пошаговое руководство. Настройка поведения вставки, обновления и удаления классов сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Пошаговое руководство: Создание LINQ для классов SQL (реляционный конструктор объектов)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)