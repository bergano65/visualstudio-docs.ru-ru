---
title: "XMLNode-элемент управления | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: f89c80850c5f91cdc6d147d733d2626f8641dab6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="xmlnode-control"></a>Элемент управления XMLNode
  **Важные** сведения, изложенные в этом разделе, относящаяся к Microsoft Word, представленному исключительно для удобства и лиц и организаций, расположенных за пределами США и их территорий или с помощью или разработки программы, работающие на, продуктов Microsoft Word, лицензированные корпорацией Майкрософт до января 2010 года, когда Microsoft удален реализация конкретной функции, относящиеся к пользовательской XML из Microsoft Word. Эта информация, относящаяся к Microsoft Word нельзя прочитать или используемых отдельным лицам или организациям в Соединенных Штатах Америки или их территориях, которые используете или разработке программ, выполняемых на продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. ; Эти продукты будут вести себя таким же, как продукты лицензированных до указанной даты или приобретенных и лицензированных за пределами США.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Элемент управления является сопоставленный объект узла XML, который предоставляет события и может быть связан с данными. <xref:Microsoft.Office.Tools.Word.XMLNode> Управления создается только при сопоставлении неповторяющегося элемента схемы документа Microsoft Office Word. Созданный в Visual Studio узел XML можно программировать непосредственно, не обращаясь к объектной модели Word.  
  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Управления можно удалить только путем удаления сопоставления элементов в Word.  
  
## <a name="binding-data-to-the-control"></a>Привязка данных к элементу управления  
 <xref:Microsoft.Office.Tools.Word.XMLNode> Элемент управления поддерживает простую привязку данных. XML-узел должен быть привязан к источнику данных с помощью <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> свойство. Если данные в привязанном наборе данных обновляются, <xref:Microsoft.Office.Tools.Word.XMLNode> управления отражает изменения.  
  
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
  
## <a name="comparing-events"></a>Сравнение событий  
 Можно записать событие, когда пользователь перемещает курсор внутрь контекста конкретного <xref:Microsoft.Office.Tools.Word.XMLNode> элемента управления. Например, может потребоваться <xref:Microsoft.Office.Tools.Word.XMLNode> управления с именем `Customer` с дочерним <xref:Microsoft.Office.Tools.Word.XMLNode> управления с именем `Company`, и `Company` имеет два дочерних <xref:Microsoft.Office.Tools.Word.XMLNode> элементов управления с именем `CompanyName` и `CompanyRegion` следующим образом:  
  
```  
<Customer>  
    <Company>  
        <CompanyName>  
        <CompanyRegion>  
```  
  
 Если вы хотите отображать элемент управления в панели действий всякий раз, когда курсор перемещается в `Company` узла, он не имеет значения, является ли курсор помещается в `CompanyName` или `CompanyRegion` потому, что оба они находятся в контексте `Company`. В этом случае можно написать собственный код <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> событие `Company`.  
  
 В большинстве случаев, когда курсор попадает <xref:Microsoft.Office.Tools.Word.XMLNode> контролировать, как <xref:Microsoft.Office.Tools.Word.XMLNode.Select> и <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> событий. В следующей таблице показаны различия между этими двумя событиями.  
  
|Выберите событие|Событие ContextEnter|  
|------------------|------------------------|  
|Происходит, когда курсор находится внутри <xref:Microsoft.Office.Tools.Word.XMLNode>.|Происходит, когда курсор находится внутри <xref:Microsoft.Office.Tools.Word.XMLNode> или один из его дочерних узлов из области вне контекста узла. Другими словами оно возникает только при изменении контекста.|  
  
 Например, при перемещении курсора из вне `Customer` в `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> событий для `Customer`, `Company`, и `CompanyName` возникает. При перемещении курсора из затем `CompanyName` для `CompanyRegion`только <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> событий для `CompanyRegion` возникает, поскольку все еще в контексте обоих `Company` и `Customer`.  
  
 Существует же отличий между <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> событий и <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> событий.  
  
## <a name="see-also"></a>См. также  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [XMLNodes-элемент управления](../vsto/xmlnodes-control.md)   
 [Как: Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [Как: сопоставление схем в документы Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  