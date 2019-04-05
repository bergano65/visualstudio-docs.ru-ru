---
title: Методы DataContext (реляционный конструктор объектов) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 05acf62d30a1ac272003c0883b4a8c927e13e659
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992743"
---
# <a name="datacontext-methods-or-designer"></a>Методы DataContext (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
DataContext] (assetId:///T:System.Data.Linq.DataContext?qualifyHint=False & autoUpgrade = True) методов (в контексте [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) являются методами <xref:System.Data.Linq.DataContext> класс, запустите хранимую процедуры и функции в базе данных.  
  
 Класс <xref:System.Data.Linq.DataContext> представляет собой класс [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)], который действует как канал между базой данных SQL Server и классами сущностей [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)], сопоставленных этой базе данных. <xref:System.Data.Linq.DataContext> Класс содержит строку подключения и методы для соединения с базой данных и работы с данными в базе данных. По умолчанию <xref:System.Data.Linq.DataContext> класс содержит несколько методов, которые можно вызывать, например <xref:System.Data.Linq.DataContext.SubmitChanges%2A> метода, который отправляет обновленные данные из [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] классы в базу данных. Можно также создать дополнительные методы <xref:System.Data.Linq.DataContext>, которые сопоставляются сохраненным процедурам и функциям. Другими словами, вызов этих пользовательских методов запустит сохраненную процедуру или функцию в базе данных, которой метод <xref:System.Data.Linq.DataContext> сопоставлен. Можно добавить новые методы в класс <xref:System.Data.Linq.DataContext> точно так, как добавлялись бы методы, чтобы расширить любой класс. Тем не менее, в обсуждениях <xref:System.Data.Linq.DataContext> методы в контексте [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], это <xref:System.Data.Linq.DataContext> методы, которые сопоставляются с хранимыми процедурами и функциями, которые обсуждаются.  
  
## <a name="methods-pane"></a>Область методов  
 Методы <xref:System.Data.Linq.DataContext>, которые сопоставляются сохраненным процедурам и функциям отображаются в области методов конструктора [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Является область методов аналогична **сущностей** области (Главная область конструктора). В области методов перечислены все <xref:System.Data.Linq.DataContext> методы, которые вы создали с помощью [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. По умолчанию область методов пуста; Перетащите хранимых процедур или функций из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] для создания <xref:System.Data.Linq.DataContext> методы и заполнить область методов. Дополнительные сведения см. в разделе [Как создать методы DataContext, сопоставленные с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Откройте и закройте область методов, щелкнув правой кнопкой мыши [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] и выбрав **скрыть область методов** или **Показать область методов**, или используйте сочетание клавиш CTRL + 1.  
  
## <a name="two-types-of-datacontext-methods"></a>Два типа возврата методов DataContext  
 Методы DataContext сопоставляются хранимым процедурам и функциям в базе данных. Методы DataContext создаются и добавляются в области методов в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Существует два различных типа методов <xref:System.Data.Linq.DataContext> — возвращающие один или несколько результирующих наборов и не возвращающие результирующие наборы:  
  
-   Методы <xref:System.Data.Linq.DataContext>, которые возвращают один или несколько результирующих наборов.  
  
     Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно только запускать хранимые процедуры и функции в базе данных и возвращать результаты. Дополнительные сведения см. в разделе [Как Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, и <xref:System.Data.Linq.IMultipleResults>.  
  
-   Методы <xref:System.Data.Linq.DataContext>, которые не возвращают результирующих наборов, например операции вставки, обновления и удаления для некоторого класса сущности.  
  
     Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно запускать хранимые процедуры вместо выполнения определенных по умолчанию действий [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] для сохранения измененных данных между классом сущности и базой данных. Дополнительные сведения см. в разделе [Как назначить хранимые процедуры для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>Типы возвращаемого значения методов DataContext  
 При перетаскивании хранимые процедуры и функции из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], тип возвращаемого значения создаваемого <xref:System.Data.Linq.DataContext> метод отличается в зависимости от того, где вы сбросили элемент. Сбрасываете элемент прямо на существующий класс сущностей создает <xref:System.Data.Linq.DataContext> метод с типом возвращаемого значения класса сущностей; перемещение элементов на пустую область [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (в любой области) создает <xref:System.Data.Linq.DataContext> метод, возвращающий автоматически сгенерированный тип. Автоматически сгенерированный тип, который создается, имеет имя, которое соответствует имени сохраненной процедуры или имени функции и свойствам, которые сопоставляют полям, возвращенным сохраненной процедурой или функцией.  
  
> [!NOTE]
>  Можно изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы просмотреть или изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>, выберите его и проверьте свойство **тип возвращаемого значения** в окне **Свойства**. Дополнительные сведения см. в разделе [Как изменить тип возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Объекты, перетаскиваемые из базы данных в область реляционного конструктора объектов, автоматически получают имена, основанные на имени объектов в базе данных. Если несколько раз перетащить один объект, к концу имени будет добавлен номер, чтобы различить имена экземпляров. Если имена объектов базы данных содержат пробелы или символы, которые не поддерживаются в Visual Basic или в C#, то пробел или недопустимый символ будет заменен символом подчеркивания.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Хранимые процедуры](http://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)   
 [Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Практическое руководство. Назначение хранимых процедур для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Пошаговое руководство: Настройка вставки, обновления и удаления в классах сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
