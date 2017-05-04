---
title: "Элемент управления XMLNodes | Microsoft Docs"
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
  - "XMLNodes - элемент управления"
  - "XMLNodes - элемент управления, события"
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Элемент управления XMLNodes
  **Важным** набор сведений в этом разделе, касающиеся Microsoft Word исключительно для использования преимущества и цене и организаций, найдены вне Соединенные Штаты и его территорий или используют или разработки программ, запущенных на продуктов Microsoft Word, которые были лицензированы Майкрософт до января 2010, когда выполненного реализация конкретной функциональности Майкрософт, связанное с пользовательским XML в Microsoft Word.  Данная информация, относящаяся к Microsoft Word, не предназначена для чтения и использования лицами или организациями, расположенными в США или их территориях, которые используют продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г., или разрабатывают программы для этих продуктов; поведение данных продуктов отличается от поведения продуктов, лицензированных до указанной даты или приобретенных и лицензированных за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Элемент управления <xref:Microsoft.Office.Tools.Word.XMLNodes> представляет собой коллекцию сопоставленных объектов\-узлов XML с событиями.  Элемент управления <xref:Microsoft.Office.Tools.Word.XMLNodes> создается только при сопоставлении повторяющегося элемента схемы документу Microsoft Office Word.  Если повторяющийся элемент содержит дочерние элементы, каждый из дочерних элементов также создается как элемент управления <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
 После создания средой Visual Studio коллекции узлов XML элемент управления можно программировать непосредственно, не обращаясь к объектной модели Word.  Удалить элемент управления <xref:Microsoft.Office.Tools.Word.XMLNodes> можно только путем удаления из документа сопоставления элементов.  
  
> [!NOTE]  
>  При доступе к дочернему элементу элемента управления <xref:Microsoft.Office.Tools.Word.XMLNodes> через свойство <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> это свойство возвращает объект <xref:Microsoft.Office.Interop.Word.XMLNode>, а не элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode>.  Дополнительные сведения см. в разделе [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## Привязка данных к элементу управления  
 Элемент управления <xref:Microsoft.Office.Tools.Word.XMLNodes> не поддерживает привязку данных.  Причина заключается в том, что элемент управления <xref:Microsoft.Office.Tools.Word.XMLNodes> не обладает возможностями привязки к сложным данным, а при простой привязке данных невозможно представить повторяющиеся данные.  
  
## Форматирование  
 К элементу управления <xref:Microsoft.Office.Tools.Word.XMLNodes> можно применить любые параметры форматирования, применяемые к тексту документа.  
  
## События  
 Ниже перечислены события, доступные для элемента управления <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## Сравнение событий  
 Перехватить событие можно в тот момент, когда пользователь перемещает курсор внутрь контекста конкретного элемента управления <xref:Microsoft.Office.Tools.Word.XMLNodes>.  Например, ниже приведена следующая ситуация: имеется элемент управления <xref:Microsoft.Office.Tools.Word.XMLNodes> с именем `Customer`, у которого имеется дочерний элемент управления <xref:Microsoft.Office.Tools.Word.XMLNodes> с именем `Company`, а элемент управления `Company` имеет два дочерних элемента управления <xref:Microsoft.Office.Tools.Word.XMLNodes> с именами `CompanyName` и `CompanyRegion`.  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Если необходимо отображать элемент управления в панели действий при каждом перемещении курсора в узел `Company`, не имеет значения, находится ли курсор в узле `CompanyName` или в узле `CompanyRegion`, поскольку оба они находятся в контексте узла `Company`.  В этом случае код следует писать в обработчике событий <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> элемента управления `Company`.  
  
 В большинстве случаев при перемещении курсора внутрь элемента управления <xref:Microsoft.Office.Tools.Word.XMLNodes> возникает и событие <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>, и событие <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>.  В приведенной ниже таблице показаны различия между этими двумя событиями.  
  
|Событие Select|Событие ContextEnter|  
|--------------------|--------------------------|  
|Происходит при перемещении курсора внутрь одного из узлов коллекции <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Происходит при перемещении курсора внутрь одного из узлов или узлов\-потомков коллекции <xref:Microsoft.Office.Tools.Word.XMLNodes> из области за пределами контекста узла.  Другими словами, это событие возникает только при изменении контекста и может возникать для нескольких вложенных элементов управления <xref:Microsoft.Office.Tools.Word.XMLNodes>.|  
  
 Например, при перемещении курсора извне элемента управления `Customer` внутрь элемента управления `CompanyName` события <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> возникают для элементов управления  `Customer`, `Company` и `CompanyName`.  Если после этого переместить курсор из элемента управления `CompanyName` в элемент управления `CompanyRegion`, событие <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> возникнет только для элемента управления `CompanyRegion`, поскольку для элементов управления `Company` и `Customer` контекст не изменится.  В документе может быть несколько узлов `Company`.  При перемещении курсора из узла `CompanyName` одного элемента управления `Company` в узел `CompanyName` другого элемента управления `Company` контекст не изменится, поэтому возникнет только событие <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>.  
  
 Аналогичным образом отличаются события <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> и <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>.  
  
## См. также  
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элемент управления XMLNode](../vsto/xmlnode-control.md)   
 [Практическое руководство. Добавление элементов управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Практическое руководство. Сопоставление схем и документов Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  