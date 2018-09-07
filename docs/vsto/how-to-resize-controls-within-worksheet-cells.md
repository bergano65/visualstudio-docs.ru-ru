---
title: 'Практическое: изменение размера элементов управления внутри ячеек листа Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 91a7e66e085408b35f0ce1d8f7d4783e0c4715a8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674883"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Практическое: изменение размера элементов управления внутри ячеек листа Excel
  При изменении размера столбцов или строк на листе, все элементы управления ведущего приложения в ячейках автоматическое изменение размера высоты или ширины ячейки, который был изменен. Элементы управления Windows Forms не меняют размер автоматически по умолчанию.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 При добавлении элементов управления во время разработки, необходимо задать параметры расположения для каждого элемента управления.  
  
 Если добавить элемент управления Windows Forms программными средствами и указанием диапазона, элемент управления автоматически изменяет свои размеры при изменении размера ячейки диапазона. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="resize-controls-at-design-time"></a>Изменение размера элементов управления во время разработки  
  
### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Чтобы изменить размеры во время разработки элементов управления  
  
1.  Из **элементов**, перетащите элемент управления Windows Forms на лист.  
  
2.  Щелкните правой кнопкой мыши элемент управления, а затем нажмите кнопку **формат элемента управления**.  
  
3.  В **формат элемента управления** диалоговом окне щелкните **свойства** вкладки.  
  
4.  В разделе **расположение объекта**выберите **перемещение и размер ячеек** , а затем щелкните **ОК**.  
  
     При изменении размера ячейку, содержащую элемент управления, элемент управления изменяет размер ячейки.  
  
## <a name="resize-controls-at-runtime"></a>Изменение размера элементов управления во время выполнения  
 Если добавить элемент управления Windows Forms во время выполнения и передайте <xref:Microsoft.Office.Interop.Excel.Range> как расположение для элемента управления, элемент управления автоматически изменяется при изменении ячейки, содержащий диапазон.  
  
### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Чтобы изменить размеры во время выполнения элементов управления  
  
1.  Добавление элемента управления диапазона A1.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     При изменении размера ячейку, содержащую элемент управления, элемент управления изменяет размер ячейки.  
  
## <a name="reset-control-placement"></a>Сброс размещения элементов управления  
 Вы можете сбросить размещение и изменение размера элемента управления, задав `Placement` задается одно из следующих <xref:Microsoft.Office.Interop.Excel.XlPlacement> значения:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Чтобы изменить поведение элемента управления, чтобы изменить размер или не перемещаются вместе с ячейки  
  
1.  Вызовите свойство размещения элемента управления и задайте значение <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>См. также  
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Практическое: Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Практическое: скрытие элементов управления на листах при печати](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Ограничения элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  