---
title: "Конструктор действия RemoveFromCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.RemoveFromCollection`1.UI"
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Конструктор действия RemoveFromCollection&lt;T&gt;
Конструктор операций **RemoveFromCollection\<T\>** используется для создания и настройки действия <xref:System.Activities.Statements.RemoveFromCollection%601>.  
  
## Действие RemoveFromCollection\<T\>  
 Действие <xref:System.Activities.Statements.RemoveFromCollection%601> удаляет указанный элемент из определенной коллекции.  
  
### Использование конструктора операций RemoveFromCollection\<T\>  
 Конструктор операций **RemoveFromCollection\<T\>** можно найти в категории **КоллекцияОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или нажмите CTRL\+ALT\+X\).  
  
 Конструктор операций **RemoveFromCollection\<T\>** можно перетащить из **Области элементов** в любое место области [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], куда обычно размещаются действия, например, внутри <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.RemoveFromCollection%601> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> для RemoveFromCollection\<Int32\>.Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **RemoveFromCollection\<T\>**, либо в поле **DisplayName** таблицы свойств.Другие свойства следует изменять в таблице свойств.  
  
### Свойства RemoveFromCollection\<T\>  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.RemoveFromCollection%601> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Необязательное понятное имя действия <xref:System.Activities.Statements.RemoveFromCollection%601>.Значение по умолчанию — RemoveFromCollection\<Int32\>.<br /><br /> Несмотря на то, что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Да|Элемент, добавляемый в **Collection\<T\>**.Этот элемент имеет тип *T*, который в свою очередь имеет тип *TypeArgument*.Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Да|Коллекция, в которую следует добавить элемент.Эта коллекция имеет тип **ICollection\<TypeArgument\>.**.Чтобы указать коллекцию, введите выражение Visual Basic в таблицу свойств.|  
|*TypeArgument*|Да|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>.По умолчанию этот тип *TypeArgument* имеет значение **Int32**.Чтобы изменить тип, измените значение аргумента *TypeArgument* в поле со списком в таблице свойств.|  
|<xref:System.Activities.Activity%601.Result%2A>|Нет|Значение, которое указывает, удален ли из коллекции указанный объект.Чтобы указать переменную, к которой необходимо привязать результат, введите переменную в таблицу свойств.|  
  
## См. также  
 [Коллекция](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)