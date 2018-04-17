---
title: 'Способ: измените тип возврата метода DataContext (O-R-конструктор) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b9660433b357d6ec1ddead86611387e0cb5c11a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Способ: измените тип возврата метода DataContext (O/R-конструктор)
Тип возврата метода <xref:System.Data.Linq.DataContext> (созданного на основе сохраненных процедур или функций) различен в зависимости от того, куда вы переместили сохраненную процедуру или функцию в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Если вы переместили элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата создаваемого класса сущностей (если схема данных, возвращенная сохраненной процедурой или функцией совпадает с формой класса сущностей). Если вы сбрасываете элемент на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип. Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы просмотреть или изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод, выберите его и нажмите кнопку **тип возвращаемого значения** свойство в **свойства** окна.  
  
> [!NOTE]
>  Нельзя вернуть <xref:System.Data.Linq.DataContext> методы, которые имеют тип возвращаемого значения задан класс сущности возврат автоматически сгенерированного типа с помощью **свойства** окна. Для возврата метода <xref:System.Data.Linq.DataContext>, сконфигурированного на возврат автоматически сгенерированного типа необходимо снова перетащить исходный объект базы данных в реляционный конструктор объектов.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Чтобы изменить тип возврата метода DataContext от автоматически сгенерированного типа к классу сущностей  
  
1.  Выберите метод <xref:System.Data.Linq.DataContext> в области методов.  
  
2.  Выберите **тип возвращаемого значения** в **свойства** выберите доступные сущности и класс в **тип возвращаемого значения** списка. Если нужного класса сущностей не находится в списке, добавьте или создайте его в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Чтобы добавить его в список.  
  
3.  Сохраните DBML-файл.  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Чтобы изменить тип возврата метода DataContext от класса сущностей обратно к автоматически созданному типу.  
  
1.  Выберите метод <xref:System.Data.Linq.DataContext> в области методов и удалите его.  
  
2.  Перетащите объект базы данных из **обозревателя серверов**/**обозреватель баз данных** на пустую область реляционного конструктора объектов.  
  
3.  Сохраните DBML-файл.  
  
## <a name="see-also"></a>См. также
[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Методы DataContext (O/R-конструктор)](../data-tools/datacontext-methods-o-r-designer.md)   
[Как: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (O/R-конструктор)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)