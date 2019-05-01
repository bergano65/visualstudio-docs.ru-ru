---
title: AddToCollection&lt;T&gt; конструктора действий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4e63486ca7e057fdd1bfe0de73e44dc4951462e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977222"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt; конструктора действий
**AddToCollection\<T >** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.AddToCollection%601> действия.  
  
## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > действия  
 Действие <xref:System.Activities.Statements.AddToCollection%601> добавляет элемент в коллекцию.  
  
### <a name="using-the-addtocollectiont-activity-designer"></a>С помощью AddToCollection\<T > конструктора действий  
 **AddToCollection\<T >** конструктора действий можно найти в **коллекции** категории **элементов**, который нажав  **Панель элементов** вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **AddToCollection\<T >** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.AddToCollection%601> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из AddToCollection\<Int32 >. (По умолчанию *TypeArgument* — **Int32**. Изменяется в таблице свойств.) <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **AddToCollection\<T >** конструктора действий или в **DisplayName** поле таблицы свойств. Другие свойства следует изменять в таблице свойств.  
  
### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > Свойства  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.AddToCollection%601> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.AddToCollection%601>. Значение по умолчанию — AddToCollection\<Int32 >. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|Элемент для добавления в коллекцию\<T >. Этот элемент имеет тип *T*, который имеет тип *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection\<TypeArgument >**. Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|  
|*TypeArgument*|True|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию это *TypeArgument* установлен тип **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|  
  
## <a name="see-also"></a>См. также  
 [Коллекции](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T > конструктора действий](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)