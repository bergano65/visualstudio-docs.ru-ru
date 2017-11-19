---
title: "XMLNodes-элемент управления | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
ms.assetid: 25ba7a21-aabb-4cce-b0d7-57b4add3b485
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2950d1c9bf2edb0715ad588180cec3b5e17da265
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="xmlnodes-control"></a>Элемент управления XMLNodes
  **Важные** сведения, изложенные в этом разделе, относящаяся к Microsoft Word, представленному исключительно для удобства и лиц и организаций, расположенных за пределами США и их территорий или с помощью или разработки программы, работающие на, продуктов Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 года, когда Microsoft удален реализация конкретной функции, относящиеся к пользовательской XML из Microsoft Word. Эта информация, относящаяся к Microsoft Word нельзя прочитать или используемых отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. ; Эти продукты будут вести себя таким же, как продукты лицензированных до указанной даты или приобретенных и лицензированных за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Управления — это коллекция сопоставленных объектов XML-узел, предоставляющий события. <xref:Microsoft.Office.Tools.Word.XMLNodes> Управления создается только при сопоставлении повторяющегося элемента схемы в документ Microsoft Office Word. Если повторяющийся элемент содержит дочерние элементы, каждый из дочерних элементов также создается в качестве <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления.  
  
 После Visual Studio создает коллекцию XML-узлов, элемент управления можно программировать непосредственно, не обращаясь к объектной модели Word. <xref:Microsoft.Office.Tools.Word.XMLNodes> Управления можно удалить только путем удаления сопоставления элементов из документа.  
  
> [!NOTE]  
>  При доступе к дочернему элементу <xref:Microsoft.Office.Tools.Word.XMLNodes> управление с помощью <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> свойство возвращает <xref:Microsoft.Office.Interop.Word.XMLNode> объекта, а не <xref:Microsoft.Office.Tools.Word.XMLNode> элемента управления. Для получения дополнительной информации см. [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="binding-data-to-the-control"></a>Привязка данных к элементу управления  
 <xref:Microsoft.Office.Tools.Word.XMLNodes> Управления не поддерживает привязку данных. Это вызвано <xref:Microsoft.Office.Tools.Word.XMLNodes> управления не имеет возможности привязки к сложным данным, а также простая привязка данных невозможно представить повторяющиеся данные.  
  
## <a name="formatting"></a>Форматирование  
 Любое форматирование, которое можно применить к тексту в документе может применяться к <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления.  
  
## <a name="events"></a>События  
 Доступные для события <xref:Microsoft.Office.Tools.Word.XMLNodes> управления являются:  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>  
  
-   <xref:System.ComponentModel.IComponent.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>  
  
-   <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>  
  
## <a name="comparing-events"></a>Сравнение событий  
 Можно записать событие, когда пользователь перемещает курсор внутрь контекста конкретного <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления. Например, может потребоваться <xref:Microsoft.Office.Tools.Word.XMLNodes> управления с именем `Customer` с дочерним <xref:Microsoft.Office.Tools.Word.XMLNodes> управления с именем `Company`, и `Company` имеет два дочерних <xref:Microsoft.Office.Tools.Word.XMLNodes> элементов управления с именем `CompanyName` и `CompanyRegion` следующим образом:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Если вы хотите отображать элемент управления в панели действий всякий раз, когда курсор перемещается в `Company` узла, он не имеет значения, является ли курсор помещается в `CompanyName` или `CompanyRegion` потому, что оба они находятся в контексте `Company`. В этом случае можно написать собственный код <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> событие `Company`.  
  
 В большинстве случаев, когда курсор попадает <xref:Microsoft.Office.Tools.Word.XMLNodes> контролировать, как <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> и <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> событий. В следующей таблице показаны различия между этими двумя событиями.  
  
|Выберите событие|Событие ContextEnter|  
|------------------|------------------------|  
|Происходит, когда курсор находится внутри одного из узлов <xref:Microsoft.Office.Tools.Word.XMLNodes> коллекции.|Происходит, когда курсор находится внутри одного из узлов или узлов-потомков <xref:Microsoft.Office.Tools.Word.XMLNodes> коллекции из области вне контекста узла. Другими словами, оно возникает только при изменении контекста и может возникать для нескольких вложенных <xref:Microsoft.Office.Tools.Word.XMLNodes> элементов управления.|  
  
 Например, при перемещении курсора из вне `Customer` в `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> событий для `Customer`, `Company`, и `CompanyName` вызываются. При перемещении курсора из затем `CompanyName` для `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> только событие `CompanyRegion` возникает, поскольку контекст является одинаковым для обоих `Company` и `Customer`. Может иметь несколько `Company` узлов в документе. При перемещении курсора из `CompanyName` узел одного `Company` для `CompanyName` узел другого `Company`, контекст не изменяется, чтобы только <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> события.  
  
 Существует же отличий между <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> событий и <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> событий.  
  
## <a name="see-also"></a>См. также  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNode-элемент управления](../vsto/xmlnode-control.md)   
 [Как: Добавление элементов управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [Как: сопоставление схем в документы Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  