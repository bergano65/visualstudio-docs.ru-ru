---
title: "Операция изменения возвращаемого типа метода DataContext не может быть отменена | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Операция изменения возвращаемого типа метода DataContext не может быть отменена
Операция изменения возвращаемого типа метода DataContext не может быть отменена.Чтобы возвратиться назад к автоматически сгенерированному типу, необходимо снова перетащить элемент из Обозревателя серверов\/обозревателя базы данных на область реляционного конструктора объектов.Вы уверены, что хотите изменить тип возвращения?  
  
 Тип возвращения метода <xref:System.Data.Linq.DataContext> различен в зависимости от того, куда вы сбросили элемент в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Если сбрасываете элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата класса сущностей.Если вы сбрасываете элемент на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип.Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов.Чтобы проверить или изменить тип возврата метода <xref:System.Data.Linq.DataContext>, выберите его и щелкните по свойству **Тип возврата** в окне **Свойства**.  
  
### Для изменения типа возврата метода DataContext  
  
-   Нажмите кнопку **Да**.  
  
### Для закрытия окна сообщения, оставляя тип возврата неизмененным  
  
-   Нажмите кнопку **Нет**.  
  
### Чтобы возвратиться к первоначальному типу возврата после изменения типа возврата  
  
1.  Выберите метод <xref:System.Data.Linq.DataContext> на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] и удалите его.  
  
2.  Найдите элемент в **Обозревателе серверов\/Обозревателе базы данных** и перетащите его на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Метод <xref:System.Data.Linq.DataContext> создается с первоначальным типом возврата по умолчанию.  
  
## См. также  
 [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Методы DataContext \(реляционный конструктор объектов\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Как создать методы DataContext, сопоставленные с хранимыми процедурами и функциями \(реляционный конструктор объектов\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)