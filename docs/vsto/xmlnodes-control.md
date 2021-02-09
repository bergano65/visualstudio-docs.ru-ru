---
title: XMLNodes - элемент управления
description: Сведения о том, что элемент управления XMLNodes создается только в том случае, если повторяющийся элемент схемы сопоставляется с документом Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d920df609c8172b6329cac537d10868e5795be12
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894391"
---
# <a name="xmlnodes-control"></a>XMLNodes - элемент управления
  **Важно!** Сведения, приведенные в этом разделе о Microsoft Word, предоставляются исключительно для использования в качестве преимуществ и применения частных лиц и организаций, которые находятся за пределами США и его территорий, а также для разработки программ, работающих на платформе Microsoft Word, которые были лицензированы корпорацией Майкрософт до января 2010, когда корпорация Майкрософт удалила реализацию определенных функций, связанных с пользовательским XML-кодом из Microsoft Word Эти сведения, касающиеся Microsoft Word, могут быть не прочитаны или использованы людьми или организациями в США или на ее территориях, которые используют или разрабатывают программные продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. Эти продукты не будут работать так же, как продукты, лицензированные до этой даты или приобретенные и лицензированные для использования за пределами США.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNodes>Элемент управления представляет собой коллекцию сопоставленных объектов узла XML, которые предоставляют события. <xref:Microsoft.Office.Tools.Word.XMLNodes>Элемент управления создается только в том случае, если повторяющийся элемент схемы сопоставляется с Microsoft Officeным документом Word. Если повторяющийся элемент содержит дочерние элементы, каждый из дочерних элементов также создается как <xref:Microsoft.Office.Tools.Word.XMLNodes> элемент управления.

 После того как Visual Studio создаст коллекцию узлов XML, можно программировать элемент управления напрямую, не обращаясь к объектной модели Word. <xref:Microsoft.Office.Tools.Word.XMLNodes>Элемент управления можно удалить только путем удаления сопоставления элемента из документа.

> [!NOTE]
> При доступе к дочернему элементу <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления через <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> свойство он возвращает <xref:Microsoft.Office.Interop.Word.XMLNode> объект, а не <xref:Microsoft.Office.Tools.Word.XMLNode> элемент управления. Дополнительные сведения см. в разделе [программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Привязка данных к элементу управления
 <xref:Microsoft.Office.Tools.Word.XMLNodes>Элемент управления не поддерживает привязку данных. Это обусловлено тем <xref:Microsoft.Office.Tools.Word.XMLNodes> , что элемент управления не имеет сложных возможностей привязки данных, а простая привязка данных не может представлять повторяющиеся данные.

## <a name="formatting"></a>Форматирование
 Любое форматирование, которое можно применить к тексту в документе, может быть применено к <xref:Microsoft.Office.Tools.Word.XMLNodes> элементу управления.

## <a name="events"></a>События
 Для <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления доступны следующие события:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Сравнение событий
 Событие можно записать, когда пользователь перемещает свой курсор внутрь контекста определенного <xref:Microsoft.Office.Tools.Word.XMLNodes> элемента управления. Например, у вас может быть <xref:Microsoft.Office.Tools.Word.XMLNodes> элемент управления с именем, `Customer` имеющий дочерний <xref:Microsoft.Office.Tools.Word.XMLNodes> элемент управления с именем `Company` и `Company` имеющий два дочерних элемента <xref:Microsoft.Office.Tools.Word.XMLNodes> управления с именем `CompanyName` и `CompanyRegion` следующим образом:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Если требуется отображать элемент управления на панели «действия» при каждом перемещении курсора в `Company` узел, не имеет значения, будет ли курсор помещен в или из-за того, что он находится в `CompanyName` `CompanyRegion` контексте `Company` . В этом случае можно написать код в <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> случае `Company` .

 В большинстве случаев, когда курсор входит в <xref:Microsoft.Office.Tools.Word.XMLNodes> элемент управления, <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> вызываются события и. В следующей таблице показаны различия между этими событиями.

|Выбор события|Событие Контекстентер|
|------------------|------------------------|
|Происходит при перемещении курсора внутрь одного из узлов коллекции <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Происходит при перемещении курсора внутрь одного из узлов или узлов-потомков коллекции <xref:Microsoft.Office.Tools.Word.XMLNodes> из области за пределами контекста узла. Иными словами, он вызывается только при изменении контекста и может быть вызван для нескольких вложенных <xref:Microsoft.Office.Tools.Word.XMLNodes> элементов управления.|

 Например, при перемещении курсора за пределы `Customer` INTO `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> вызываются события для `Customer` , `Company` и `CompanyName` . Если затем переместить курсор из `CompanyName` в, то `CompanyRegion` <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> `CompanyRegion` будет вызвано событие только для, так как контекст одинаков для `Company` и `Customer` . В документе может быть несколько `Company` узлов. Если переместить курсор с `CompanyName` узла одного узла `Company` на `CompanyName` другой `Company` , контекст будет таким же, поэтому <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> будет вызвано только событие.

 Между <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> событием и событием существуют те же различия <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> .

## <a name="see-also"></a>См. также раздел
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Элемент управления XMLNode](../vsto/xmlnode-control.md)
- [Как добавить элементы управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Как сопоставлять схемы с документами Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
