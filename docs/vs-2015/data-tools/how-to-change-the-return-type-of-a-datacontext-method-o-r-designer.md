---
title: Практическое руководство. Изменить тип возвращаемого значения метода DataContext (реляционный конструктор объектов) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be57c5d8a298f37f9cffc7cc4b363651efbc9c2b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665653"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Практическое руководство. изменение типа возвращаемого значения метода DataContext (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Тип возврата метода <xref:System.Data.Linq.DataContext> (созданного на основе сохраненных процедур или функций) различен в зависимости от того, куда вы переместили сохраненную процедуру или функцию в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Если вы сбрасываете элемент прямо в существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата создаваемого класса сущностей (если схема данных, возвращенная сохраненной процедурой или функцией совпадает с формой класса сущностей). Если вы сбрасываете элемент на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип. Можно изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы проверить или изменить тип возврата метода <xref:System.Data.Linq.DataContext>, выберите его и щелкните по свойству **Тип возврата** в окне **Свойства**.  
  
> [!NOTE]
>  Нельзя восстановить методы <xref:System.Data.Linq.DataContext> (для которых в качестве типа возвращаемого значения задан класс сущности) таким образом, чтобы они возвращали автоматически созданный тип в окне **Свойства**. Для возврата метода <xref:System.Data.Linq.DataContext>, сконфигурированного на возврат автоматически сгенерированного типа необходимо снова перетащить исходный объект базы данных в реляционный конструктор объектов.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Чтобы изменить тип возвращаемого значения метода DataContext от автоматически сгенерированного типа к классу сущностей  
  
1.  Выберите метод <xref:System.Data.Linq.DataContext> в области методов.  
  
2.  Выберите **Тип возвращаемого значения** в окне **Свойства** и потом доступный класс сущностей в списке **Типов возврата**. Если нужного класса сущностей не находится в списке, добавьте или создайте его в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , добавляемый в список.  
  
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
