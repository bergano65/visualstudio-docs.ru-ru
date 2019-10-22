---
title: Методы DataContext (реляционный конструктор объектов)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0e81f2337931f565e0068a852bf9b8284350690c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648543"
---
# <a name="datacontext-methods-or-designer"></a>Методы DataContext (реляционный конструктор объектов)

<xref:System.Data.Linq.DataContext> методы (в контексте [средств LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) являются методами класса <xref:System.Data.Linq.DataContext>, которые выполняют хранимые процедуры и функции в базе данных.

Класс <xref:System.Data.Linq.DataContext> представляет собой класс [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], который действует как канал между базой данных SQL Server и классами сущностей [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], сопоставленных этой базе данных. Класс <xref:System.Data.Linq.DataContext> содержит сведения о строке подключения и методы для подключения к базе данных и управления данными в базе данных. По умолчанию класс <xref:System.Data.Linq.DataContext> содержит несколько методов, которые можно вызвать, например метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, который отправляет обновленные данные из классов [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] в базу данных. Можно также создать дополнительные методы <xref:System.Data.Linq.DataContext>, которые сопоставляются сохраненным процедурам и функциям. Иными словами, вызов этих пользовательских методов запускает хранимую процедуру или функцию в базе данных, с которой сопоставлен метод <xref:System.Data.Linq.DataContext>. Можно добавить новые методы в класс <xref:System.Data.Linq.DataContext> точно так, как добавлялись бы методы, чтобы расширить любой класс. Однако в обсуждениях <xref:System.Data.Linq.DataContext> методов в контексте **реляционного конструктора O/R**это <xref:System.Data.Linq.DataContext> методы, которые сопоставляются с хранимыми процедурами и функциями, которые обсуждаются.

## <a name="methods-pane"></a>Область методов

<xref:System.Data.Linq.DataContext> методы, которые сопоставляются с хранимыми процедурами и функциями, отображаются на панели **методы** **конструктора O/R**. Область **методов** аналогична области **сущностей** (главная область конструктора). На панели **методы** перечислены все методы <xref:System.Data.Linq.DataContext>, созданные с помощью **конструктора O/R**. По умолчанию панель **методы** пуста; Перетащите хранимые процедуры или функции из **Обозреватель сервера** или **Обозреватель базы данных** в **конструктор O/R** , чтобы создать <xref:System.Data.Linq.DataContext> методы и заполнить панель **методов** . Дополнительные сведения см. [в разделе инструкции. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор операций и т. д.)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Откройте и закройте панель методы, щелкнув правой кнопкой мыши **конструктор O/R** , а затем выбрав **Скрыть панель методов** или **Показать панель методов**, или воспользоваться сочетанием клавиш **CTRL** +**1**.

## <a name="two-types-of-datacontext-methods"></a>Два типа возврата методов DataContext

Методы DataContext сопоставляются хранимым процедурам и функциям в базе данных. Методы DataContext можно создавать и добавлять на панели **методы** **конструктора O/R**. Существует два различных типа методов <xref:System.Data.Linq.DataContext> — возвращающие один или несколько результирующих наборов и не возвращающие результирующие наборы:

- Методы <xref:System.Data.Linq.DataContext>, которые возвращают один или несколько результирующих наборов.

   Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно только запускать хранимые процедуры и функции в базе данных и возвращать результаты. Дополнительные сведения см. [в разделе инструкции. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. LINQ. исинглересулт \<T > и <xref:System.Data.Linq.IMultipleResults>.

- Методы <xref:System.Data.Linq.DataContext>, которые не возвращают результирующих наборов, например операции вставки, обновления и удаления для некоторого класса сущности.

   Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно запускать хранимые процедуры вместо выполнения определенных по умолчанию действий [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] для сохранения измененных данных между классом сущности и базой данных. Дополнительные сведения см. [в разделе инструкции. назначение хранимых процедур для выполнения операций обновления, вставки и удаления (реляционный конструктор R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Типы возвращаемого значения методов DataContext

При перетаскивании хранимых процедур и функций из **Обозреватель сервера** или **Обозреватель базы данных** в **конструктор O/R**тип возвращаемого значения созданного метода <xref:System.Data.Linq.DataContext> различается в зависимости от места удаления элемента. При удалении элементов непосредственно в существующий класс сущностей создается <xref:System.Data.Linq.DataContext> метод с типом возвращаемого значения класса сущности. При удалении элементов в пустую область **конструктора O/R** (на любой панели) создается метод <xref:System.Data.Linq.DataContext>, возвращающий автоматически созданный тип. Автоматически созданный тип имеет имя, совпадающее с именем хранимой процедуры или функции и свойствами, которые сопоставляются с полями, возвращаемыми хранимой процедурой или функцией.

> [!NOTE]
> Можно изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы просмотреть или изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>, выберите его и проверьте свойство **тип возвращаемого значения** в окне **Свойства**. Дополнительные сведения см. в разделе [инструкции. изменение типа возвращаемого значения метода DataContext (реляционный конструктор данных)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Объекты, перетаскиваемые из базы данных в область конструктора O/R, именуются автоматически на основе имен объектов в базе данных. При перетаскивании одного и того же объекта несколько раз в конец нового имени добавляется число, отличающее имена. Если имена объектов базы данных содержат пробелы или символы, которые не поддерживаются в Visual Basic или в C#, то пробел или недопустимый символ будет заменен символом подчеркивания.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Хранимые процедуры](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Практическое руководство. Назначение хранимых процедур для выполнения обновления, вставки и удаления (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Пошаговое руководство. Настройка поведения вставки, обновления и удаления классов сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Пошаговое руководство. Создание классов LINQ to SQL (реляционный конструктор объектов)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)