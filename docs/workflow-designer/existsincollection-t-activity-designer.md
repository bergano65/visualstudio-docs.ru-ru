---
title: "Конструктор действия ExistsInCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ExistsInCollection`1.UI"
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Конструктор действия ExistsInCollection&lt;T&gt;
Конструктор операций **ExistsInCollection\<T\>** используется для создания и настройки операции <xref:System.Activities.Statements.ExistsInCollection%601>.  
  
## Операция ExistsInCollection\<T\>  
 Операция <xref:System.Activities.Statements.ExistsInCollection%601> определяет, существует ли указанный объект в заданной коллекции.  
  
### Использование конструктора операций ExistsInCollection\<T\>  
 Конструктор операций **ExistsInCollection\<T\>** можно найти в категории **КоллекцияОбласти элементов**, нажав на вкладку **Область элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(Иначе выберите **Область элементов** из меню **Просмотр**, или же CTRL\+ALT\+X.\)  
  
 Конструктор операций **ExistsInCollection\<T\>** можно перетащить из **Области элементов** в область [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] в любое место, куда обычно размещаются действия, например, внутри <xref:System.Activities.Statements.Sequence>.Будет создано действие <xref:System.Activities.Statements.ExistsInCollection%601> со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection\<Int32\>.\(По умолчанию *TypeArgument* имеет значение **Int32**.Изменяется в таблице свойств.\)  Значение <xref:System.Activities.Activity.DisplayName%2A> можно изменить в заголовке конструктора операций **ExistsInCollection\<T\>**, либо в поле **DisplayName** таблицы свойств.Другие свойства следует изменять в таблице свойств.  
  
### Свойства ExistsInCollection\<T\>  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.ExistsInCollection%601> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательное|Использование|  
|------------------|------------------|-------------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|Нет|Понятное имя действия <xref:System.Activities.Statements.ExistsInCollection%601>.Значение по умолчанию — ExistsInCollection\<Int32\>.Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Да|Элемент, добавляемый в коллекцию \<T\>.Этот элемент имеет тип *T*, который в свою очередь имеет тип *TypeArgument*.Чтобы указать элемент, введите в выражение Visual Basic в таблице свойств.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Да|Коллекция, в которую следует добавить элемент.Эта коллекция имеет тип **ICollection\<TypeArgument\>.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|  
|*TypeArgument*|Да|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>.По умолчанию этот тип *TypeArgument* имеет значение **Int32**.Чтобы изменить тип, измените значение аргумента *TypeArgument* в поле со списком в таблице свойств.|  
|<xref:System.Activities.Activity%601.Result%2A>|Нет|Значение, которое указывает, содержится ли в коллекции указанный объект.Чтобы указать переменную, к которой необходимо привязать результат, введите переменную Visual Basic в таблице свойств.|  
  
## См. также  
 [Коллекция](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)