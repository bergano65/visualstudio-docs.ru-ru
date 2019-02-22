---
title: Элемент управления диаграммы
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8592bdbe08c70df96cf553ff5548a87704837a8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596338"
---
# <a name="chart-control"></a>Элемент управления диаграммы
  Элемент управления <xref:Microsoft.Office.Tools.Excel.Chart> — это объект диаграммы, предоставляющий события. При добавлении диаграммы на лист Visual Studio создает объект <xref:Microsoft.Office.Tools.Excel.Chart>, который можно запрограммировать напрямую, не обращаясь к объектной модели Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Создание элемента управления
 Вы можете добавить <xref:Microsoft.Office.Tools.Excel.Chart> элементов управления на лист Microsoft Office Excel во время разработки или во время выполнения в проекте уровня документа.

 Вы можете добавить <xref:Microsoft.Office.Tools.Excel.Chart> элементов управления на лист во время выполнения в надстройке VSTO. Дополнительные сведения см. в разделе [Как Добавление элементов управления диаграммой на листы](../vsto/how-to-add-chart-controls-to-worksheets.md).

> [!NOTE]
>  При закрытии листа динамически созданные объекты диаграммы не сохраняются на листе как элементы управления ведущего приложения. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).

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
- [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)
- [Расширение документов Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Практическое руководство. Добавление элементов управления диаграммой на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
