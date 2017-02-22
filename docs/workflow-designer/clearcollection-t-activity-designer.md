---
title: "Конструктор действия ClearCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ClearCollection`1.UI"
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия ClearCollection&lt;T&gt;
Конструктор действия **ClearCollection\<T\>** служит для создания и настройки действия <xref:System.Activities.Statements.ClearCollection%601>.  
  
## Действие ClearCollection\<T\>  
 Действие <xref:System.Activities.Statements.ClearCollection%601> очищает указанную коллекцию, удаляя из нее все элементы.  
  
### Использование конструктора действия ClearCollection\<T\>  
 Конструктор действия **ClearCollection\<T\>** можно найти в категории **КоллекцияОбласти элементов**, открыв вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(либо выберите **Область элементов** в меню **Вид** или нажмите CTRL\+ALT\+X\).  
  
 Конструктор действия **ClearCollection\<T\>** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], где обычно размещаются действия, например внутрь <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.ClearCollection%601>, где значение <xref:System.Activities.Activity.DisplayName%2A> по умолчанию равно ClearCollection\<Int32\>.\(По умолчанию *TypeArgument* имеет значение **Int32**.Изменяется в таблице свойств.\) Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора действия **ClearCollection\<T\>** либо в поле **DisplayName** таблицы свойств.Другие свойства следует изменять в таблице свойств.  
  
### Свойства ClearCollection\<T\>  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.ClearCollection%601> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Указывает дополнительное понятное имя действия <xref:System.Activities.Statements.ClearCollection%601>.Значение по умолчанию — ClearCollection\<Int32\>.Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Да|Задает коллекцию для очистки от элементов.Эта коллекция имеет тип **ICollection\<TypeArgument\>.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|  
|*TypeArgument*|Да|Задает тип T для элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>.По умолчанию этот тип *TypeArgument* имеет значение **Int32**.Чтобы изменить тип, измените значение аргумента *TypeArgument* в поле со списком в таблице свойств.|  
  
## См. также  
 [Коллекция](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)