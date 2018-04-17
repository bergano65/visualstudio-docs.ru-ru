---
title: Элемент управления диаграммы | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c473c026f5d5f9a5919626fb667994e6ffdc01f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="chart-control"></a>Chart Control
  Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> — это объект диаграммы, предоставляющий события. При добавлении диаграммы на лист Visual Studio создает объект <xref:Microsoft.Office.Tools.Excel.Chart>, который можно запрограммировать напрямую, не обращаясь к объектной модели Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Создание элемента управления  
 Элементы управления <xref:Microsoft.Office.Tools.Excel.Chart> можно добавлять на лист Microsoft Office Excel во время разработки и во время выполнения в проекте на уровне документа.  
  
 Вы можете добавить элементы управления <xref:Microsoft.Office.Tools.Excel.Chart> на лист во время выполнения надстройки VSTO. Дополнительные сведения см. в разделе [как: Добавление элементов управления диаграммы на листы](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  При закрытии листа динамически созданные объекты диаграммы не сохраняются на листе как элементы управления ведущего приложения. Для получения дополнительной информации см. [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="formatting"></a>Форматирование  
 Любое форматирование, которое можно применить к <xref:Microsoft.Office.Interop.Excel.Chart>, также можно применить к элементу управления <xref:Microsoft.Office.Tools.Excel.Chart>. Это такие элементы форматирования, как границы, шрифты, тип диаграммы, линии сетки, условные обозначения и метки данных.  
  
## <a name="events"></a>События  
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
  
## <a name="see-also"></a>См. также  
 [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Как: Добавление элементов управления диаграммой на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  