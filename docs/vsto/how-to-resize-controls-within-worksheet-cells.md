---
title: "Как: изменение размера элементов управления внутри ячеек листа Excel | Документы Microsoft"
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
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 01e9dfbe244d373eaa4e66c13e02c781b32b8691
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Практическое руководство. Изменение размера внутри ячеек листа Excel
  При изменении размера столбцов или строк на листе, все элементы управления ведущего приложения, содержащиеся в ячейках, автоматически размеры, чтобы высота или ширина ячейки, размер которого был изменен. Элементы управления Windows Forms не меняют размер автоматически по умолчанию.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 При добавлении элементов управления во время разработки, необходимо задать параметры расположения для каждого элемента управления.  
  
 Если добавить элемент управления Windows Forms программными средствами и указать аргумент диапазона, элемент управления автоматически изменяет размер при изменении размера ячейки диапазона. Для получения дополнительной информации см. [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="resizing-controls-at-design-time"></a>Изменение размеров элементов управления во время разработки  
  
#### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Чтобы изменить размеры во время разработки элементов управления  
  
1.  Из **элементов**, перетащите элемент управления Windows Forms на лист.  
  
2.  Щелкните правой кнопкой мыши элемент управления и нажмите кнопку **формат элемента управления**.  
  
3.  В **формат элемента управления** диалоговое окно, нажмите кнопку **свойства** вкладки.  
  
4.  В разделе **расположение объекта**выберите **перемещать и изменять размеры** , а затем щелкните **ОК**.  
  
     При изменении размера ячейки, содержащей элемент управления, элемент управления изменяет размер ячейки.  
  
## <a name="resizing-controls-at-run-time"></a>Изменение размеров элементов управления во время выполнения  
 Если добавить элемент управления Windows Forms во время выполнения и передает <xref:Microsoft.Office.Interop.Excel.Range> как расположение для элемента управления, элемент управления автоматически изменяется при изменении ячейки с диапазоном.  
  
#### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Чтобы изменить размеры во время выполнения элементов управления  
  
1.  Добавьте элемент управления в диапазон А1.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     При изменении размера ячейки, содержащей элемент управления, элемент управления изменяет размер ячейки.  
  
## <a name="resetting-control-placement"></a>Сброс размещения элементов управления  
 Можно сбросить размещение и изменение размеров элемента управления, задав `Placement` в одно из следующих <xref:Microsoft.Office.Interop.Excel.XlPlacement> значения:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Чтобы изменить поведение элемента управления, чтобы изменить размер или не перемещаются вместе с ячейки  
  
1.  Вызовите свойство размещения элемента управления и задайте значение <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>См. также  
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Как: Добавление элементов управления в документы Office Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Как: скрытие элементов управления на листах при печати](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  