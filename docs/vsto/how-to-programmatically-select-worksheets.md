---
title: "Как: программный Выбор листов Excel | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: dfd3c56ab51cc0e1d1fb1521640497f4748195cc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-select-worksheets"></a>Практическое руководство. Программный выбор листов Excel
  Метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> выбирает указанный объект, который перемещает выделенный пользователем фрагмент в новый объект. Если необходимо сфокусироваться на объекте без изменения выбранного пользователем фрагмента, используйте метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Если нужно выбрать существующий лист в надстройке VSTO или если лист был создан во время выполнения в настройке на уровне документа, для доступа к нему следует использовать коллекцию <xref:Microsoft.Office.Interop.Excel.Sheets> книги Excel; в противном случае к ведущему элементу <xref:Microsoft.Office.Tools.Excel.Worksheet> можно получить доступ напрямую.  
  
## <a name="using-the-worksheet-host-item"></a>Использование ведущего элемента листа  
 В настройке на уровне документа добавьте следующий код в **Sheet1.vb** или **Sheet1.cs**.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Выбор первого листа в книге с помощью ведущего элемента  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> типа `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Использование коллекции листов книги Excel  
 Обратитесь к таблице с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> Excel.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Выбор первого листа в книге с помощью коллекции листов книги Excel  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets>, чтобы выбрать первый лист активной книги.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: программная печать листов Excel](../vsto/how-to-programmatically-print-worksheets.md)   
 [Как: программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Как: программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Как: программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Ведущие элементы листа](../vsto/worksheet-host-item.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  