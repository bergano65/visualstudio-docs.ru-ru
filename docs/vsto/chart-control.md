---
title: "Элемент управления &quot;диаграмма&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.ExcelChart"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Chart - элемент управления [разработка решений Office в Visual Studio]"
  - "Chart - элемент управления [разработка решений Office в Visual Studio], привязка данных"
  - "Chart - элемент управления [разработка решений Office в Visual Studio], события"
ms.assetid: 64f1a7cc-cc66-47da-aaeb-44a62ae53909
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Элемент управления &quot;диаграмма&quot;
  Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> — это объект диаграммы, предоставляющий события.  При добавлении диаграммы на лист Visual Studio создает объект <xref:Microsoft.Office.Tools.Excel.Chart>, который можно запрограммировать напрямую, не обращаясь к объектной модели Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Создание элемента управления  
 Элементы управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавлять на лист Microsoft Office Excel во время разработки и во время выполнения в проекте на уровне документа.  
  
 Вы можете добавить элементы управления <xref:Microsoft.Office.Tools.Excel.Chart> на лист во время выполнения надстройки VSTO.  Дополнительные сведения см. в разделе [Практическое руководство. Добавление элементов управления диаграммой на листы](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  При закрытии листа динамически созданные объекты диаграммы не сохраняются на листе как элементы управления ведущего приложения.  Дополнительные сведения см. в разделе [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Форматирование  
 Любое форматирование, которое можно применить к <xref:Microsoft.Office.Interop.Excel.Chart>, также можно применить к элементу управления <xref:Microsoft.Office.Tools.Excel.Chart>.  Это такие элементы форматирования, как границы, шрифты, тип диаграммы, линии сетки, условные обозначения и метки данных.  
  
## События  
 Для элемента управления <xref:Microsoft.Office.Tools.Excel.Chart> доступны следующие события:  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## См. также  
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Практическое руководство. Добавление элементов управления диаграммой на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  