---
title: "Как изменить тип возвращаемого значения метода DataContext (реляционный конструктор объектов) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Как изменить тип возвращаемого значения метода DataContext (реляционный конструктор объектов)
Тип возврата метода <xref:System.Data.Linq.DataContext> \(созданного на основе сохраненных процедур или функций\) различен в зависимости от того, куда вы переместили сохраненную процедуру или функцию в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Если вы переместили элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата создаваемого класса сущностей \(если схема данных, возвращенная сохраненной процедурой или функцией совпадает с формой класса сущностей\).Если вы сбрасываете элемент на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип.Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов.Чтобы проверить или изменить тип возврата метода <xref:System.Data.Linq.DataContext>, выберите его и щелкните по свойству **Тип возврата** в окне **Свойства**.  
  
> [!NOTE]
>  Нельзя восстановить методы <xref:System.Data.Linq.DataContext> \(для которых в качестве типа возвращаемого значения задан класс сущности\) таким образом, чтобы они возвращали автоматически созданный тип в окне **Свойства**.Для возврата метода <xref:System.Data.Linq.DataContext>, сконфигурированного на возврат автоматически сгенерированного типа необходимо снова перетащить исходный объект базы данных в реляционный конструктор объектов.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Чтобы изменить тип возврата метода DataContext от автоматически сгенерированного типа к классу сущностей  
  
1.  Выберите метод <xref:System.Data.Linq.DataContext> в области методов.  
  
2.  Выберите **Тип возврата** в окне **Свойства** и потом выберите доступный класс сущностей в списке **Типов возврата**.Если нужного класса сущностей нет в списке, добавьте или создайте его в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], чтобы добавить его в список.  
  
3.  Сохраните DBML\-файл.  
  
### Чтобы изменить тип возврата метода DataContext от класса сущностей обратно к автоматически сгенерированному типу  
  
1.  Выберите метод <xref:System.Data.Linq.DataContext> в области методов и удалите его.  
  
2.  Перетащите объект базы данных из **Обозревателя серверов**\/**Обозревателя базы данных** на пустую область реляционного конструктора объектов.  
  
3.  Сохраните DBML\-файл.  
  
## См. также  
 [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Методы DataContext \(реляционный конструктор объектов\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Как создать методы DataContext, сопоставленные с хранимыми процедурами и функциями \(реляционный конструктор объектов\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)