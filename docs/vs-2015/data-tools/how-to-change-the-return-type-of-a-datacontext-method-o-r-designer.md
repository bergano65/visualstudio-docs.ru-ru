---
title: 'Способы: измените тип возвращаемого значения метода DataContext (реляционный конструктор объектов) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4999c9fd273b78ff740e53c25bbe5a4b0a3017f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211748"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Способы: измените тип возвращаемого значения метода DataContext (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> (созданного на основе сохраненных процедур или функций) различен в зависимости от того, куда вы переместили сохраненную процедуру или функцию в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Если вы переместили элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата создаваемого класса сущностей (если схема данных, возвращенная сохраненной процедурой или функцией совпадает с формой класса сущностей). Если вы сбрасываете элемент на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип. Можно изменить тип возврата метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы проверить или изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод, выберите его и нажмите кнопку **тип возвращаемого значения** свойство в **свойства** окна.  
  
> [!NOTE]
>  Невозможно отменить <xref:System.Data.Linq.DataContext> методы, которые имеют тип возвращаемого значения задан класс сущности, чтобы они возвращали автоматически созданный тип с помощью **свойства** окна. Для возврата метода <xref:System.Data.Linq.DataContext>, сконфигурированного на возврат автоматически сгенерированного типа необходимо снова перетащить исходный объект базы данных в реляционный конструктор объектов.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Чтобы изменить тип возврата метода DataContext от автоматически сгенерированного типа к классу сущностей  
  
1.  Выберите метод <xref:System.Data.Linq.DataContext> в области методов.  
  
2.  Выберите **тип возвращаемого значения** в **свойства** в класс окна, а затем выберите доступные сущности **тип возвращаемого значения** списка. Если нужного класса сущностей не находится в списке, добавьте или создайте его в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , добавляемый в список.  
  
3.  Сохраните DBML-файл.  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Чтобы изменить тип возврата метода DataContext от класса сущностей обратно к автоматически созданному типу.  
  
1.  Выберите метод <xref:System.Data.Linq.DataContext> в области методов и удалите его.  
  
2.  Перетащите объект базы данных из **обозревателя серверов**/**обозреватель баз данных** на пустую область реляционного конструктора.  
  
3.  Сохраните DBML-файл.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)

