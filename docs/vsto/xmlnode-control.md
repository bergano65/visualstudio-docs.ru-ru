---
title: XMLNode - элемент управления
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd047814f11b5fddad868bd65b84deba369facd5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258893"
---
# <a name="xmlnode-control"></a>XMLNode - элемент управления
  **Важные** сведения, изложенные в этом разделе, касающиеся Microsoft Word, представленных исключительно для преимущество и лиц и организаций, расположенных за пределами США и их территорий или использующие или разработки программ, выполняемых на, продукты Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 г, при удалении реализация конкретной функции в Microsoft связана с пользовательским XML-из Microsoft Word. Эти сведения, касающиеся Microsoft Word может не читают или используют отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете, или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт, начиная с 10 января 2010 г. ; Эти продукты, будет вести себя так же, как продукты до этой даты или приобретенных и лицензируются для использования за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Элемент управления является сопоставленный объект узла XML, который предоставляет события и может быть привязан к данным. <xref:Microsoft.Office.Tools.Word.XMLNode> Управления создается только в том случае, когда неповторяющийся элемент схемы сопоставляется с документ Microsoft Office Word. После того как Visual Studio создаст XML-узел, можно запрограммировать напрямую, не обращаясь к объектной модели Word.  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Управления можно удалить только путем удаления сопоставления элементов в Word.  
  
## <a name="bind-data-to-the-control"></a>Привязка данных к элементу управления  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Управления простой привязкой данных. XML-узел должен быть привязан к источнику данных с помощью <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> свойство. Если данные в привязанном наборе данных обновляются, <xref:Microsoft.Office.Tools.Word.XMLNode> управления отражает изменения.  
  
## <a name="formatting"></a>Форматирование  
 Форматирование, которое может применяться к <xref:Microsoft.Office.Interop.Word.XMLNode> может быть применен к <xref:Microsoft.Office.Tools.Word.XMLNode> элемента управления. Сюда входят шрифты, подчеркивания и стили символов.  
  
## <a name="events"></a>События  
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
  
## <a name="compare-events"></a>Сравнения событий  
 Можно записать событие, когда пользователь перемещает курсор внутри контекста определенного <xref:Microsoft.Office.Tools.Word.XMLNode> элемента управления. Например, возможно, <xref:Microsoft.Office.Tools.Word.XMLNode> управления с именем `Customer` с дочерним <xref:Microsoft.Office.Tools.Word.XMLNode> управления с именем `Company`, и `Company` имеет два дочерних <xref:Microsoft.Office.Tools.Word.XMLNode> элементов управления с именем `CompanyName` и `CompanyRegion` следующим образом:  
  
```xml  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Если вы хотите отображать элемент управления в панели действий всякий раз, когда курсор перемещается в `Company` узла, он не имеет значения, ли курсор помещается в `CompanyName` или `CompanyRegion` потому, что оба они находятся в контексте `Company`. В этом случае можно написать код в <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> событие `Company`.  
  
 В большинстве случаев, когда курсор входит <xref:Microsoft.Office.Tools.Word.XMLNode> управления, оба <xref:Microsoft.Office.Tools.Word.XMLNode.Select> и <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> событий. Ниже приведены различия между этими двумя событиями.  
  
|Выберите событие|Событие ContextEnter|  
|------------------|------------------------|  
|Происходит при перемещении курсора внутрь <xref:Microsoft.Office.Tools.Word.XMLNode>.|Происходит при перемещении курсора внутрь <xref:Microsoft.Office.Tools.Word.XMLNode> или один из его дочерних узлов из области вне контекста данного узла. Другими словами она возникает только при изменении контекста.|  
  
 Например, при перемещении курсора из за пределами `Customer` в `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> событие для `Customer`, `Company`, и `CompanyName` возникает. При перемещении курсора из затем `CompanyName` для `CompanyRegion`, только <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> событие для `CompanyRegion` возникает, потому что не все еще в контексте обоих `Company` и `Customer`.  
  
 Существуют такие же отличия между <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> событий и <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> событий.  
  
## <a name="see-also"></a>См. также  
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элемент управления XMLNodes](../vsto/xmlnodes-control.md)   
 [Практическое: Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Практическое: сопоставление схем и документов Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  