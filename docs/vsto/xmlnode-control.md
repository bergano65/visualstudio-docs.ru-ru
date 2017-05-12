---
title: "Элемент управления XMLNode"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "XMLNode - элемент управления"
ms.assetid: 4f5c7f17-62aa-483c-ab0d-b04614ab065d
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Элемент управления XMLNode
  **Важным** набор сведений в этом разделе, касающиеся Microsoft Word исключительно для использования преимущества и цене и организаций, найдены вне Соединенные Штаты и его территорий или используют или разработки программ, запущенных на продуктов Microsoft Word, которые были лицензированы Майкрософт до января 2010, когда выполненного реализация конкретной функциональности Майкрософт, связанное с пользовательским XML в Microsoft Word.  Данная информация, относящаяся к Microsoft Word, не предназначена для чтения и использования лицами или организациями, расположенными в США или их территориях, которые используют продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г., или разрабатывают программы для этих продуктов; поведение данных продуктов отличается от поведения продуктов, лицензированных до указанной даты или приобретенных и лицензированных за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> представляет собой сопоставленный объект узла XML, который предоставляет события и возможности привязки к данным.  Элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> создается только при сопоставлении неповторяющегося элемента схемы документу Microsoft Office Word.  Созданный в Visual Studio узел XML можно программировать непосредственно, не обращаясь к объектной модели Word.  
  
 Удалить элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> можно только путем удаления сопоставления элементов в Word.  
  
## Привязка данных к элементу управления  
 Элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> поддерживает простую привязку данных.  узел XML связывается с источником данных с помощью свойства <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>.  Изменения данных в связанном наборе отображаются в элементе управления <xref:Microsoft.Office.Tools.Word.XMLNode>.  
  
## Форматирование  
 Форматирование, которое может применяться к объекту <xref:Microsoft.Office.Interop.Word.XMLNode>, также может применяться к элементу управления <xref:Microsoft.Office.Tools.Word.XMLNode>.  К таким функциям форматирования относятся шрифты, а также стили подчеркивания и знаков.  
  
## События  
 Для элемента управления <xref:Microsoft.Office.Tools.Word.XMLNode> доступны следующие события:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>  
  
## Сравнение событий  
 Перехватить событие можно в тот момент, когда пользователь перемещает курсор внутрь контекста конкретного элемента управления <xref:Microsoft.Office.Tools.Word.XMLNode>.  Например, ниже приведена следующая ситуация: существует элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> с именем `Customer` с дочерним элементом управления <xref:Microsoft.Office.Tools.Word.XMLNode> с именем `Company`, а также элемент управления `Company` с двумя дочерними элементами управления <xref:Microsoft.Office.Tools.Word.XMLNode> с именами `CompanyName` и `CompanyRegion`.  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Если необходимо отображать элемент управления в панели действий при каждом перемещении курсора в узел `Company`, не имеет значения, находится ли курсор в узле `CompanyName` или в узле `CompanyRegion`, поскольку оба они находятся в контексте узла `Company`.  В этом случае код следует писать в обработчике событий <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> элемента управления `Company`.  
  
 В большинстве случаев при перемещении курсора в элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> одновременно вызываются события <xref:Microsoft.Office.Tools.Word.XMLNode.Select> и <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>.  В приведенной ниже таблице показаны различия между этими двумя событиями.  
  
|Событие Select|Событие ContextEnter|  
|--------------------|--------------------------|  
|Вызывается при перемещении курсора в элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode>.|Вызывается при перемещении курсора в элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> или один из его дочерних узлов из области вне контекста данного узла.  Другими словами, это событие вызывается только при изменении контекста.|  
  
 Например, при перемещении курсора из области вне элемента управления `Customer` в элемент управления `CompanyName`, событие <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> одновременно вызывается для элементов управления `Customer`, `Company` и `CompanyName`.  При последующем перемещении курсора из элемента управления `CompanyName` в `CompanyRegion` событие <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> вызывается только для элемента управления `CompanyRegion`, поскольку курсор по\-прежнему находится в контексте событий `Company` и `Customer`.  
  
 Аналогичным образом различаются события <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> и <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>.  
  
## См. также  
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элемент управления XMLNodes](../vsto/xmlnodes-control.md)   
 [Практическое руководство. Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Практическое руководство. Сопоставление схем и документов Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  