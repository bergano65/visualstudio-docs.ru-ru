---
title: ExistsInCollection&lt;T&gt; конструктора действий | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5c8fec33a7233960f1b90d5d4a644c8887b0f2b0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568745"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection&lt;T&gt; конструктора действий
**ExistsInCollection\<T >** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.ExistsInCollection%601> действия.  
  
## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > действия  
 Операция <xref:System.Activities.Statements.ExistsInCollection%601> определяет, существует ли указанный объект в заданной коллекции.  
  
### <a name="using-the-existsincollectiont-activity-designer"></a>С помощью ExistsInCollection\<T > конструктора действий  
 **ExistsInCollection\<T >** конструктора действий можно найти в **коллекции** категории **элементов**, который нажав  **Панель элементов** вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **ExistsInCollection\<T >** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, такие как внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.ExistsInCollection%601> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из ExistsInCollection\<Int32 >. (По умолчанию *TypeArgument* — **Int32**. Изменяется в таблице свойств.)  <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **ExistsInCollection\<T >** конструктора действий или в **DisplayName** поле таблицы свойств. Другие свойства следует изменять в таблице свойств.  
  
### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > Свойства  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.ExistsInCollection%601> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Понятное имя действия <xref:System.Activities.Statements.ExistsInCollection%601>. Значение по умолчанию — ExistsInCollection\<Int32 >. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Да|Элемент для добавления в коллекцию\<T >. Этот элемент имеет тип *T* имеет тип *TypeArgument*. Чтобы указать элемент, введите в выражение Visual Basic в таблице свойств.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection\<TypeArgument >.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|  
|*TypeArgument*|Да|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию это *TypeArgument* установлен тип **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Значение, которое указывает, содержится ли в коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную Visual Basic в таблице свойств.|  
  
## <a name="see-also"></a>См. также  
 [Коллекции](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)