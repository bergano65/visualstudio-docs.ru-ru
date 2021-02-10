---
title: XMLNode - элемент управления
description: Сведения о том, что элемент управления XMLNode является сопоставленным объектом XML-узла, который предоставляет события и может быть привязан к данным.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9e86bfbe7af122e2557178f5d70256903d0cc740
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949718"
---
# <a name="xmlnode-control"></a>XMLNode - элемент управления
  **Важно!** Сведения, приведенные в этом разделе о Microsoft Word, предоставляются исключительно для использования в качестве преимуществ и применения частных лиц и организаций, которые находятся за пределами США и его территорий, а также для разработки программ, работающих на платформе Microsoft Word, которые были лицензированы корпорацией Майкрософт до января 2010, когда корпорация Майкрософт удалила реализацию определенных функций, связанных с пользовательским XML-кодом из Microsoft Word Эти сведения, касающиеся Microsoft Word, могут быть не прочитаны или использованы людьми или организациями в США или на ее территориях, которые используют или разрабатывают программные продукты Microsoft Word, лицензированные корпорацией Майкрософт после 10 января 2010 г. Эти продукты не будут работать так же, как продукты, лицензированные до этой даты или приобретенные и лицензированные для использования за пределами США.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNode>Элемент управления — это сопоставленный объект узла XML, который предоставляет события и может быть привязан к данным. <xref:Microsoft.Office.Tools.Word.XMLNode>Элемент управления создается только в том случае, если неповторяющийся элемент схемы сопоставляется с Microsoft Officeным документом Word. После того как Visual Studio создаст узел XML, вы можете программировать его напрямую, не обращаясь к объектной модели Word.

 <xref:Microsoft.Office.Tools.Word.XMLNode>Элемент управления можно удалить только путем удаления сопоставления элементов в Word.

## <a name="bind-data-to-the-control"></a>Привязка данных к элементу управления
 <xref:Microsoft.Office.Tools.Word.XMLNode>Элемент управления поддерживает простую привязку данных. Узел XML должен быть привязан к источнику данных с помощью <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> Свойства. Если данные в привязанном наборе данных обновляются, элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> отражает эти изменения.

## <a name="formatting"></a>Форматирование
 Форматирование, которое можно применить к <xref:Microsoft.Office.Interop.Word.XMLNode> объекту, может быть применено к <xref:Microsoft.Office.Tools.Word.XMLNode> элементу управления. К ним относятся шрифты, стили подчеркивания и стили символов.

## <a name="events"></a>События
 Для элемента управления <xref:Microsoft.Office.Tools.Word.XMLNode> доступны следующие события:

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Сравнение событий
 Событие можно записать, когда пользователь перемещает свой курсор внутрь контекста определенного <xref:Microsoft.Office.Tools.Word.XMLNode> элемента управления. Например, у вас может быть <xref:Microsoft.Office.Tools.Word.XMLNode> элемент управления с именем, `Customer` имеющий дочерний <xref:Microsoft.Office.Tools.Word.XMLNode> элемент управления с именем `Company` и `Company` имеющий два дочерних элемента <xref:Microsoft.Office.Tools.Word.XMLNode> управления с именем `CompanyName` и `CompanyRegion` следующим образом:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Если требуется отображать элемент управления на панели «действия» при каждом перемещении курсора в `Company` узел, не имеет значения, будет ли курсор помещен в или из-за того, что он находится в `CompanyName` `CompanyRegion` контексте `Company` . В этом случае можно написать код в <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> случае `Company` .

 В большинстве случаев, когда курсор входит в <xref:Microsoft.Office.Tools.Word.XMLNode> элемент управления, <xref:Microsoft.Office.Tools.Word.XMLNode.Select> <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> вызываются события и. В следующей таблице показаны различия между этими событиями.

|Выбор события|Событие Контекстентер|
|------------------|------------------------|
|Происходит при помещении курсора внутрь объекта <xref:Microsoft.Office.Tools.Word.XMLNode> .|Вызывается при перемещении курсора в элемент управления <xref:Microsoft.Office.Tools.Word.XMLNode> или один из его дочерних узлов из области вне контекста данного узла. Иными словами, он вызывается только при изменении контекста.|

 Например, при перемещении курсора за пределы `Customer` INTO `CompanyName` , <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> вызывается событие для `Customer` , `Company` и `CompanyName` . Если затем переместить курсор из `CompanyName` в, то будет `CompanyRegion` <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> вызвано только событие для, `CompanyRegion` так как все еще находятся в контексте `Company` и `Customer` .

 Между <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> событием и событием существуют те же различия <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> .

## <a name="see-also"></a>См. также раздел
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)
- [Элемент управления XMLNodes](../vsto/xmlnodes-control.md)
- [Как добавить элементы управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Как сопоставлять схемы с документами Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
