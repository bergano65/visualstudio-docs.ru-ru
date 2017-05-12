---
title: "Элемент управления NamedRange"
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
  - "VST.Toolbox.Range"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "диапазоны, именованные"
  - "элемент управления NamedRange, события"
  - "элемент управления NamedRange, привязка данных"
  - "NamedRange - элемент управления"
ms.assetid: 07878c7c-cb5a-4f98-95c4-e828de25dae5
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Элемент управления NamedRange
  Элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> представляет собой диапазон с уникальным именем, который предоставляет события и может быть привязан к данным. Дополнительные сведения см. в разделе [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Создание элемента управления  
 Элементы управления <xref:Microsoft.Office.Tools.Excel.NamedRange> можно добавлять в лист Microsoft Office Excel во время разработки и во время выполнения в проекте на уровне документа.  
  
 Вы можете добавлять элементы управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в лист во время выполнения в надстройке VSTO. Для получения дополнительной информации см. [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
> [!NOTE]  
>  По умолчанию динамически созданные именованные диапазоны не сохраняются как ведущие элементы управления в листе при его закрытии. Для получения дополнительной информации см. [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Элементы управления <xref:Microsoft.Office.Tools.Excel.NamedRange> могут состоять только из диапазонов в определенных листах. Элементы управления <xref:Microsoft.Office.Tools.Excel.NamedRange> не могут иметь относительные имена, применимые для всех листов, и они не могут состоять из диапазонов, распространяющихся на несколько листов в книге \(трехмерных диапазонов\).  
  
## Привязка данных к элементу управления  
 Кажется, что именованный диапазон будет хорошим кандидатом для сложной привязки данных, поскольку он может иметь много ячеек. Однако диапазон — это всего лишь коллекция ячеек, которую невозможно легко сопоставить с определенным столбцом из набора данных. Таким образом, элементы управления <xref:Microsoft.Office.Tools.Excel.NamedRange> поддерживают только простую привязку данных. Элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> может использоваться для сложной привязки данных. Для получения дополнительной информации см. [Элемент управления ListObject](../vsto/listobject-control.md).  
  
 Элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> может быть привязан к источнику данных с помощью свойств <xref:System.Windows.Forms.Control.DataBindings%2A>. Свойство привязки данных по умолчанию элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> — это <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.  
  
 Если данные в привязанном наборе данных обновляются посредством какого\-либо механизма, элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> отражает изменения.  
  
## Форматирование  
 Любое форматирование, которое можно применить к <xref:Microsoft.Office.Interop.Excel.Range>, также можно применить и к элементу управления <xref:Microsoft.Office.Tools.Excel.NamedRange>. Это включает границы, шрифты, формат чисел и стили.  
  
## Переименование элемента управления  
 При добавлении в лист элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> из **панели элементов** Visual Studio автоматически создает имя для этого элемента управления. Это имя можно изменить в окне **Свойства**.  
  
## События  
 Для элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> доступны следующие события:  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>  
  
## См. также  
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Практическое руководство. Изменения размера элементов управления "NamedRange"](../vsto/how-to-resize-namedrange-controls.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Пошаговое руководство. Программирование реакции на события элементов управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  