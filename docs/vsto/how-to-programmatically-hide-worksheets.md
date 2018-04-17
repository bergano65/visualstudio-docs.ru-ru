---
title: 'Как: программное скрытие листов Excel | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c66e787d8e1e660f320ab390787c7ebf13d3ef7f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-hide-worksheets"></a>Практическое руководство. Программное скрытие листов Excel
  Вы можете отображать или скрывать любой лист в книге. Чтобы скрыть лист, используйте ведущий элемент листа или получите доступ к листу с помощью коллекции листов книги.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-the-worksheet-host-item"></a>Использование ведущего элемента листа  
 Если лист был добавлен в настройку уровня документа во время разработки, для скрытия указанного листа используйте свойство <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> .  
  
#### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Скрытие листа с помощью ведущего элемента листа  
  
1.  Установите в свойстве <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> ведущего элемента `Sheet1` значение перечисления <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Использование коллекции листов книги Excel  
 Обращайтесь к листам с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> для Microsoft Office Excel в следующих случаях.  
  
-   Требуется скрыть лист в надстройке VSTO.  
  
-   Лист, который вы хотите скрыть, был создан во время выполнения в настройке уровня документа.  
  
#### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Скрытие листа с помощью коллекции листов книги Excel  
  
1.  Установите в свойстве <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> листа значение перечисления <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Как: программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Как: программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)  
  