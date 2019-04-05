---
title: RemoveFromCollection&lt;T&gt; конструктора действий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 45a426d4703ed2a402ee7f06341e55d65ae410ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991823"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection&lt;T&gt; конструктора действий
**RemoveFromCollection\<T >** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.RemoveFromCollection%601> действия.  
  
## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection\<T > действия  
 Действие <xref:System.Activities.Statements.RemoveFromCollection%601> удаляет указанный элемент из определенной коллекции.  
  
### <a name="using-the-removefromcollectiont-activity-designer"></a>С помощью RemoveFromCollection\<T > конструктора действий  
 **RemoveFromCollection\<T >** конструктора действий можно найти в **коллекции** категории **элементов**, который нажав **Элементов** вкладке [!INCLUDE[wfd2](../includes/wfd2-md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **RemoveFromCollection\<T >** конструктор действия можно перетащить из **элементов** и сбросить в [!INCLUDE[wfd2](../includes/wfd2-md.md)] поверхности везде, где обычно размещаются действия, такие как внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.RemoveFromCollection%601> действие по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из RemoveFromCollection\<Int32 >. <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **RemoveFromCollection\<T >** конструктора действий или в **DisplayName** поле таблицы свойств. Другие свойства следует изменять в таблице свойств.  
  
### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection\<T > Свойства  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.RemoveFromCollection%601> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Необязательное понятное имя действия <xref:System.Activities.Statements.RemoveFromCollection%601>. Значение по умолчанию — RemoveFromCollection\<Int32 >.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Элемент для добавления **коллекции\<T >**. Этот элемент имеет тип *T*, который имеет тип *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection\<TypeArgument >.** Чтобы указать коллекцию, введите выражение Visual Basic в сетке свойств.|  
|*TypeArgument*|True|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию это *TypeArgument* установлен тип **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Значение, которое указывает, удален ли из коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную в таблицу свойств.|  
  
## <a name="see-also"></a>См. также  
 [Коллекции](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)