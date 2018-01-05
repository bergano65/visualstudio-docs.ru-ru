---
title: "Как: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (конструктор O-R) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: a56bacfd2d726e2ec7bedf69f6c79ce347e3556e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Как: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (O/R-конструктор)
Хранимые процедуры и функции могут добавляться в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] как <xref:System.Data.Linq.DataContext> методы. Вызов метода и передача в обязательные параметры запускает хранимую процедуру или функцию в базе данных и возвращает данные в тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод. Дополнительные сведения о <xref:System.Data.Linq.DataContext> методов, см. [методы DataContext (O/R-конструктор)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Хранимые процедуры также используются для переопределения действий, которые [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] выполняет для операций вставки, обновления и удаления при сохранении изменений из классов сущностей в базе данных. Дополнительные сведения см. в разделе [как: назначение хранимых процедур для выполнения обновления, вставки и удаления (конструктор O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Создание методов DataContext  
 Можно создать <xref:System.Data.Linq.DataContext> методов путем перетаскивания сохраненных процедур или функций из **обозревателя базы данных обозревателя серверов** на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  Возвращаемый тип сформированного метода <xref:System.Data.Linq.DataContext> будет зависеть от места, в котором завершается перетаскивание хранимой процедуры или функции в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Если сбрасываете элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата класса сущностей. Если вы сбрасываете элементы на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип. Можно изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метода после его добавления в область методов. Чтобы просмотреть или изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод, выберите его и проверьте **тип возвращаемого значения** свойство в **свойства** окна. Дополнительные сведения см. в разделе [способ: измените тип возврата метода DataContext (O/R-конструктор)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Для создания методов DataContext, которые возвращают автоматически сгенерированные типы  
  
1.  В **обозревателя серверов**/**обозреватель баз данных**, разверните **хранимых процедур** узел базы данных, вы работаете.  
  
2.  Найдите нужную сохраненную процедуру и перетащите ее на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     <xref:System.Data.Linq.DataContext> Метода создается с автоматически сгенерированным типом возврата и появляется в **методы** области.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Чтобы создать методы DataContext, которые имеют тип возвращаемого значения класса сущностей  
  
1.  В **обозревателя серверов**/**обозреватель баз данных**, разверните **хранимых процедур** узел базы данных, вы работаете.  
  
2.  Найдите нужную сохраненную процедуру и перетащите ее на существующий класс сущностей в конструкторе [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     <xref:System.Data.Linq.DataContext> Метода создается с типом возвращаемого значения выбранного класса сущностей и появляется в **методы** области.  
  
> [!NOTE]
>  Дополнительные сведения об изменении типа возвращаемого значения существующих <xref:System.Data.Linq.DataContext> методов, см. [как: изменить тип возврата метода DataContext (O/R-конструктор)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Методы DataContext (O/R-конструктор)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ в C#](/dotnet/csharp/linq/linq-in-csharp)