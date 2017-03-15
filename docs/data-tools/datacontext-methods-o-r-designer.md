---
title: "Методы DataContext (реляционный конструктор объектов) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 5
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Методы DataContext (реляционный конструктор объектов)
Методы <xref:System.Data.Linq.DataContext> \(в контексте [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md)\) представляют собой методы класса <xref:System.Data.Linq.DataContext>, который запускает сохраненные процедуры и функции в базе данных.  
  
 Класс <xref:System.Data.Linq.DataContext> представляет собой класс [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], который действует как канал между базой данных SQL Server и классами сущностей [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], сопоставленных с этой базой данных.Класс <xref:System.Data.Linq.DataContext> содержит данные строки подключения и методы для подключения к базе данных и работы с данными в базе данных. По умолчанию класс <xref:System.Data.Linq.DataContext> содержит несколько методов, доступных для вызова, таких как метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, который отправляет обновленные данные из классов [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] в базу данных.Можно также создать дополнительные методы <xref:System.Data.Linq.DataContext>, которые сопоставляются сохраненным процедурам и функциям.Другими словами, вызов этих пользовательских методов запустит сохраненную процедуру или функцию в базе данных, которой метод <xref:System.Data.Linq.DataContext> сопоставлен.Можно добавить новые методы в класс <xref:System.Data.Linq.DataContext> точно так, как добавлялись бы методы, чтобы расширить любой класс.Однако, в дискуссиях о методах <xref:System.Data.Linq.DataContext> в контексте [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], это методы <xref:System.Data.Linq.DataContext>, которые сопоставляются с хранимыми процедурами и функциями, которые обсуждаются.  
  
> [!NOTE]
>  В [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] хранимые процедуры и функции обрабатываются аналогичным образом, то есть сопоставляются с классами сущностей при помощи того же самого атрибута <xref:System.Data.Linq.StoredProcedureAttribute>.В контексте [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] методы <xref:System.Data.Linq.DataContext>, которые сопоставляются с хранимыми процедурами такие же как методы, сопоставляемые с функциями.  
  
## Область методов  
 Методы <xref:System.Data.Linq.DataContext>, которые сопоставляются с хранимыми процедурами и функциями отображаются в области методов конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Область методов аналогична области **Сущностей** \(Главная область конструктора\).В области методов перечислены все методы <xref:System.Data.Linq.DataContext>, которые вы создали при помощи конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].По умолчанию область методов пуста; перетащите сохраненные процедуры или функции их **Обозревателя серверов**\/**Обозревателя базы данных** на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], чтобы создать методы <xref:System.Data.Linq.DataContext> и заполнить область методов.Дополнительные сведения см. в разделе [Как создать методы DataContext, сопоставленные с хранимыми процедурами и функциями \(реляционный конструктор объектов\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Область методов можно открыть и закрыть, в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] щелкнув ее правой кнопкой мыши и выбрав команду **Скрыть область методов** или **Показать область методов** либо с помощью сочетания клавиш CTRL\+1.  
  
## Два типа возврата методов DataContext  
 Методы DataContext сопоставляются хранимым процедурам и функциям в базе данных.Методы DataContext создаются и добавляются в области методов в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Существует два различных типа методов <xref:System.Data.Linq.DataContext> — возвращающие один или несколько результирующих наборов и не возвращающие результирующие наборы.  
  
-   Методы <xref:System.Data.Linq.DataContext>, которые возвращают один или несколько результирующих наборов.  
  
     Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно только запускать хранимые процедуры и функции в базе данных и возвращать результаты.Дополнительные сведения см. в разделах [Как создать методы DataContext, сопоставленные с хранимыми процедурами и функциями \(реляционный конструктор объектов\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), <xref:System.Data.Linq.ISingleResult%271> и <xref:System.Data.Linq.IMultipleResults>.  
  
-   Методы <xref:System.Data.Linq.DataContext>, которые не возвращают результирующих наборов, например операции вставки, обновления и удаления для некоторого класса сущности.  
  
     Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно запускать хранимые процедуры вместо выполнения определенных по умолчанию действий [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] для сохранения измененных данных между классом сущности и базой данных.Дополнительные сведения см. в разделе [Как назначить хранимые процедуры для выполнения обновлений, вставок и удалений \(реляционный конструктор объектов\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Типы возвращаемого значения методов DataContext  
 Когда хранимые процедуры и функции перетаскиваются из **обозревателя серверов** или **обозревателя баз данных** в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], тип возвращаемого значения для создаваемого метода <xref:System.Data.Linq.DataContext> будет различным \(в зависимости от места, в котором завершилось перетаскивание элемента\).Перемещение элементов прямо на существующий класс сущностей создает метод <xref:System.Data.Linq.DataContext> с типом возврата класса сущностей элемента; перемещение элементов на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] \(в любой области\) создает метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип возврата.Автоматически сгенерированный тип, который создается, имеет имя, которое соответствует имени сохраненной процедуры или имени функции и свойствам, которые сопоставляют полям, возвращенным сохраненной процедурой или функцией.  
  
> [!NOTE]
>  Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов.Чтобы просмотреть или изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>, выберите его и проверьте свойство **Тип возвращаемых данных** в окне **Свойства**.Дополнительные сведения см. в разделе [Как изменить тип возвращаемого значения метода DataContext \(реляционный конструктор объектов\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Объекты, перетаскиваемые из базы данных в область реляционного конструктора объектов, автоматически получают имена, основанные на имени объектов в базе данных.Если несколько раз перетащить один объект, к концу имени будет добавлен номер, чтобы различить имена экземпляров.Если имена объектов базы данных содержат пробелы или символы, которые не поддерживаются в Visual Basic или в C\#, то пробел или недопустимый символ будет заменен символом подчеркивания.  
  
## См. также  
 [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Хранимые процедуры](../Topic/Stored%20Procedures.md)   
 [Как создать методы DataContext, сопоставленные с хранимыми процедурами и функциями \(реляционный конструктор объектов\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Как назначить хранимые процедуры для выполнения обновлений, вставок и удалений \(реляционный конструктор объектов\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Пошаговое руководство. Настройка операций вставки, обновления и удаления в классах сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Пошаговое руководство. Создание классов LINQ to SQL \(реляционный конструктор объектов\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)