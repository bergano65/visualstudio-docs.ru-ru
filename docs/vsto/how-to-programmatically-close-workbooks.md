---
title: Как выполнить Программное закрытие книг Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01f188af2ae96cf8622f3614da493891e3dbabe4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093149"
---
# <a name="how-to-programmatically-close-workbooks"></a>Как выполнить Программное закрытие книг Excel
  Можно закрыть активную книгу или указать, какую книгу следует закрыть.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="close-the-active-workbook"></a>Закрытие активной книги  
 Для закрытия активной книги можно использовать две процедуры: одну для настроек на уровне документа и одну для надстроек VSTO.  
  
### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Закрытие активной книги в настройке на уровне документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> , чтобы закрыть книгу, связанную с настройкой. Чтобы использовать следующий пример кода, запустите его в классе `Sheet1` в проекте уровня документа для Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]  
  
### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Закрытие активной книги в надстройке VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> , чтобы закрыть активную книгу. Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="close-a-workbook-that-you-specify-by-name"></a>Закрытие книги с заданным именем  
 Процедура закрытия книги с заданным именем идентична процедуре для надстройки VSTO и настроек на уровне документа.  
  
### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Закрытие книги, указанной по имени  
  
1.  Укажите имя книги в качестве аргумента коллекции <xref:Microsoft.Office.Interop.Excel.Workbooks> . В следующем примере кода предполагается, что в Excel открыта книга с именем **NewWorkbook** .  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="see-also"></a>См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Практическое руководство. Программное Сохранение книг Excel](../vsto/how-to-programmatically-save-workbooks.md)   
 [Практическое руководство. Программное открытие книг Excel](../vsto/how-to-programmatically-open-workbooks.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)  
