---
title: "Автоматизация Excel с помощью расширенных объектов | Microsoft Docs"
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
  - "Excel [разработка решений Office в Visual Studio], автоматизация"
  - "автоматизация [разработка решений Office в Visual Studio], Excel"
  - "элементы управления ведущего приложения, Excel"
  - "Excel [разработка решений Office в Visual Studio], элементы управления ведущего приложения"
  - "расширенные объекты [разработка решений Office в Visual Studio], Excel"
  - "элементы управления ведущего приложения [разработка решений Office в Visual Studio], Excel"
  - "автоматизация Excel"
  - "ведущие элементы [разработка решений Office в Visual Studio], Excel"
  - "элементы управления [разработка решений Office в Visual Studio], элементы управления ведущего приложения Excel"
ms.assetid: 3ed99480-234d-46b1-b91c-226018bd3faf
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Автоматизация Excel с помощью расширенных объектов
  При разработке своих решений Excel в Visual Studio можно также использовать *ведущие элементы* и *элементы управления ведущего приложения*. Это объекты, которые расширяют некоторые часто используемые объекты в объектной модели Excel \(т. е. объектной модели, которая предоставляется основной сборкой взаимодействия для Excel\), такие как объекты <xref:Microsoft.Office.Interop.Excel.Worksheet> и <xref:Microsoft.Office.Interop.Excel.Range>. Расширенные объекты ведут себя как объекты Excel, на которых они основаны, но добавляют объектам дополнительные события и возможности по привязке данных.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Ведущие элементы и элементы управления ведущего приложения доступны в надстройке VSTO и настройке на уровне документа, хотя контекст, в котором они используются, отличается для каждого типа решения. Для получения дополнительной информации см. [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).  
  
## Ведущие элементы Excel  
 Проекты Excel предоставляют доступ к нескольким ведущим элементам:  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>. Этот ведущий элемент представляет лист в проекте. Также он служит контейнером для управляемых элементов управления, в том числе элементов управления ведущего приложения и элементов управления Windows Forms, и хранит сведения об элементах управления на его поверхности. Дополнительные сведения см. в разделе [Ведущие элементы листа](../vsto/worksheet-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>. Этот ведущий элемент представляет книгу в проекте и выступает в роли контейнера для компонентов, общих для всех листов в книге. Для получения дополнительной информации см. [Ведущий элемент книги](../vsto/workbook-host-item.md).  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Этот ведущий элемент на листе Excel содержит только диаграмму и предоставляет события.  
  
     При добавлении листа диаграммы во время разработки в качестве нового листа в проект настройки уровня документа Microsoft Office Excel Visual Studio автоматически создает ведущий элемент <xref:Microsoft.Office.Tools.Excel.ChartSheet>.  
  
     Хотя ведущий элемент <xref:Microsoft.Office.Tools.Excel.ChartSheet> — это лист Excel, невозможно добавить какие\-либо элементы управления на лист с диаграммой. Если вы хотите использовать другие элементы управления на листе с диаграммой, не используйте лист диаграммы. Вместо этого можно поместить диаграмму как внедренный объект на лист с помощью элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.Chart>. Дополнительные сведения см. в разделе [Элемент управления "диаграмма"](../vsto/chart-control.md).  
  
## Элементы управления ведущего приложения Excel  
 Существует несколько элементов управления ведущего приложения для Excel, которые помогают создавать, организовывать и автоматизировать книги и листы. Они предоставляют события и возможности привязки к данным, не поддерживаемые их аналогами в управляемой объектной модели Excel.  
  
 Дополнительные сведения о ведущих элементах управления, которые можно использовать в проектах Excel, см. в следующих разделах:  
  
-   [Элемент управления "диаграмма"](../vsto/chart-control.md)  
  
-   [Элемент управления ListObject](../vsto/listobject-control.md)  
  
-   [Элемент управления NamedRange](../vsto/namedrange-control.md)  
  
-   [Элемент управления XmlMappedRange](../vsto/xmlmappedrange-control.md)  
  
## См. также  
 [Практическое руководство. Заполнение данными элементов управления ListObject](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Практическое руководство. Добавление элементов управления диаграммой на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Практическое руководство. Добавление элементов управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)   
 [Практическое руководство. Изменения размера элементов управления "NamedRange"](../vsto/how-to-resize-namedrange-controls.md)   
 [Практическое руководство. Изменение размера элементов управления ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Практическое руководство. Обработка данных при добавлении новой строки в элемент управления ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [Практическое руководство. Сопоставление столбцов элемента управления ListObject данным](../vsto/how-to-map-listobject-columns-to-data.md)   
 [Пошаговое руководство. Программирование реакции на события элементов управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  