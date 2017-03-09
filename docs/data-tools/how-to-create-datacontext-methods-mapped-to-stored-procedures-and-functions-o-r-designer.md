---
title: "Как создать методы DataContext, сопоставленные с хранимыми процедурами и функциями (реляционный конструктор объектов) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Как создать методы DataContext, сопоставленные с хранимыми процедурами и функциями (реляционный конструктор объектов)
Сохраненные процедуры и функции можно добавить в конструктор [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] как методы <xref:System.Data.Linq.DataContext>.Вызов метода и передача в обязательные параметры запускает сохраненную процедуру или функцию на базе данных и возвращает данные в тип возврата метода <xref:System.Data.Linq.DataContext>.Дополнительные сведения о методах <xref:System.Data.Linq.DataContext> см. в [Методы DataContext \(реляционный конструктор объектов\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Хранимые процедуры также используются для переопределения действий, которые [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] выполняет для операций вставки, обновления и удаления при сохранении изменений из классов сущностей в базе данных.Дополнительные сведения см. в разделе [Как назначить хранимые процедуры для выполнения обновлений, вставок и удалений \(реляционный конструктор объектов\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Создание методов DataContext  
 Можно создать методы <xref:System.Data.Linq.DataContext> путем перетаскивания сохраненных процедур или функций из **Обозревателя серверов\/Обозревателя базы данных** область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  Возвращаемый тип сформированного метода <xref:System.Data.Linq.DataContext> будет зависеть от места, в котором завершается перетаскивание хранимой процедуры или функции в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Если сбрасываете элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата класса сущностей.Если вы сбрасываете элементы на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип.Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов.Чтобы просмотреть или изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>, выберите его и проверьте свойство **Тип возвращаемых данных** в окне **Свойства**.Дополнительные сведения см. в разделе [Как изменить тип возвращаемого значения метода DataContext \(реляционный конструктор объектов\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Для создания методов DataContext, которые возвращают автоматически сгенерированные типы  
  
1.  В **Обозревателе серверов**\/**Обозревателе базы данных** разверните узел **Сохраненные процедуры** базы данных, с которой вы работаете.  
  
2.  Найдите нужную сохраненную процедуру и перетащите ее на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Метод <xref:System.Data.Linq.DataContext> создается с автоматически сгенерированным типом возврата и появляется в области **Методы**.  
  
#### Чтобы создать методы DataContext, которые имеют тип возврата класса сущностей  
  
1.  В **Обозревателе серверов**\/**Обозревателе базы данных** разверните узел **Сохраненные процедуры** базы данных, с которой вы работаете.  
  
2.  Найдите нужную сохраненную процедуру и перетащите ее на существующий класс сущностей в конструкторе [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Метод <xref:System.Data.Linq.DataContext> создается с типом возврата выбранного класса сущностей и появляется в области **Методы**.  
  
> [!NOTE]
>  Дополнительные сведения об изменении возвращаемых типов существующих методов <xref:System.Data.Linq.DataContext> см. в разделе [Как изменить тип возвращаемого значения метода DataContext \(реляционный конструктор объектов\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## См. также  
 [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Методы DataContext \(реляционный конструктор объектов\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Пошаговое руководство. Создание классов LINQ to SQL \(реляционный конструктор объектов\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Знакомство с LINQ в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Практическое руководство. Создание запросов LINQ на языке C\#](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)