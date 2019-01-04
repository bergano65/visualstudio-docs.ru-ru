---
title: XMLNodes - элемент управления
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 227c7b72e8574556cfb18635b6fa329229c4bea6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865431"
---
# <a name="xmlnodes-control"></a>XMLNodes - элемент управления
  **Важные** сведения, изложенные в этом разделе, касающиеся Microsoft Word, представленных исключительно для преимущество и лиц и организаций, расположенных за пределами США и их территорий или использующие или разработки программ, выполняемых на, продукты Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 г, при удалении реализация конкретной функции в Microsoft связана с пользовательским XML-из Microsoft Word. Эти сведения, касающиеся Microsoft Word может не читают или используют отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете, или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт, начиная с 10 января 2010 г. ; Эти продукты, будет вести себя так же, как продукты до этой даты или приобретенных и лицензируются для использования за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Элемент управления является коллекцией объектов сопоставленных XML-узел, предоставляющий события. <xref:Microsoft.Office.Tools.Word.XMLNodes> Создается элемент управления, только в том случае, при сопоставлении повторяющегося элемента схемы в документ Microsoft Office Word. Если повторяющийся элемент содержит дочерние элементы, каждый из дочерних элементов также создается как <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления.  
  
 После того как Visual Studio создаст коллекцию узлов XML, элемент управления можно запрограммировать напрямую, не обращаясь к объектной модели Word. <xref:Microsoft.Office.Tools.Word.XMLNodes> Управления можно удалить только путем удаления сопоставления элементов из документа.  
  
> [!NOTE]  
>  Если доступ к дочерним элементом элемента <xref:Microsoft.Office.Tools.Word.XMLNodes> управлять через <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> свойство возвращает <xref:Microsoft.Office.Interop.Word.XMLNode> объекта вместо <xref:Microsoft.Office.Tools.Word.XMLNode> элемента управления. Дополнительные сведения см. в разделе [программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="bind-data-to-the-control"></a>Привязка данных к элементу управления  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Управления не поддерживает привязку данных. Это обусловлено <xref:Microsoft.Office.Tools.Word.XMLNodes> управления не имеет возможности привязки сложных данных, и не может представлять простую привязку данных повторяющихся данных.  
  
## <a name="formatting"></a>Форматирование  
 Все форматирование, которое может применяться к тексту документа может применяться к <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления.  
  
## <a name="events"></a>События  
 События, доступные для <xref:Microsoft.Office.Tools.Word.XMLNodes> управления:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="compare-events"></a>Сравнения событий  
 Можно записать событие, когда пользователь перемещает курсор внутри контекста определенного <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления. Например, возможно, <xref:Microsoft.Office.Tools.Word.XMLNodes> управления с именем `Customer` с дочерним <xref:Microsoft.Office.Tools.Word.XMLNodes> управления с именем `Company`, и `Company` имеет два дочерних <xref:Microsoft.Office.Tools.Word.XMLNodes> элементов управления с именем `CompanyName` и `CompanyRegion` следующим образом:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Если вы хотите отображать элемент управления в панели действий всякий раз, когда курсор перемещается в `Company` узла, он не имеет значения, ли курсор помещается в `CompanyName` или `CompanyRegion` потому, что оба они находятся в контексте `Company`. В этом случае можно написать код в <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> событие `Company`.  
  
 В большинстве случаев, когда курсор входит <xref:Microsoft.Office.Tools.Word.XMLNodes> управления, оба <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> и <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> событий. Ниже приведены различия между этими двумя событиями.  
  
|Выберите событие|Событие ContextEnter|  
|------------------|------------------------|  
|Происходит при перемещении курсора внутрь одного из узлов <xref:Microsoft.Office.Tools.Word.XMLNodes> коллекции.|Происходит при перемещении курсора внутрь одного из узлов или узлов-потомков <xref:Microsoft.Office.Tools.Word.XMLNodes> коллекции, из области вне контекста данного узла. Другими словами, это событие возникает только при изменении контекста и может возникать для нескольких вложенных <xref:Microsoft.Office.Tools.Word.XMLNodes> элементов управления.|  
  
 Например, при перемещении курсора из за пределами `Customer` в `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> события для `Customer`, `Company`, и `CompanyName` вызываются. При перемещении курсора из затем `CompanyName` для `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> только событие `CompanyRegion` возникает, поскольку контекст является одинаковым для обоих `Company` и `Customer`. Может иметь несколько `Company` узлов в документе. При перемещении курсора из `CompanyName` узел одного `Company` для `CompanyName` узел другого `Company`, контекст остается неизменным, поэтому только <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> события.  
  
 Существуют такие же отличия между <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> событий и <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> событий.  
  
## <a name="see-also"></a>См. также  
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элемент управления XMLNode](../vsto/xmlnode-control.md)   
 [Практическое руководство. Добавление элементов управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Практическое руководство. Сопоставление схем и документов Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
