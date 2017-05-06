---
title: "Практическое руководство. Программное скрытие листов Excel"
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
  - "скрытые листы"
  - "листы, скрытие"
ms.assetid: 3208f633-137f-47f9-9c9c-2cf8e3c72096
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Практическое руководство. Программное скрытие листов Excel
  Вы можете отображать или скрывать любой лист в книге. Чтобы скрыть лист, используйте ведущий элемент листа или получите доступ к листу с помощью коллекции листов книги.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Использование ведущего элемента листа  
 Если лист был добавлен в настройку уровня документа во время разработки, для скрытия указанного листа используйте свойство <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A>.  
  
#### Скрытие листа с помощью ведущего элемента листа  
  
1.  Установите в свойстве <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> ведущего элемента `Sheet1` значение перечисления <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#25)]  
  
## Использование коллекции листов книги Excel  
 Обращайтесь к листам с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> для Microsoft Office Excel в следующих случаях.  
  
-   Требуется скрыть лист в надстройке VSTO.  
  
-   Лист, который вы хотите скрыть, был создан во время выполнения в настройке уровня документа.  
  
#### Скрытие листа с помощью коллекции листов книги Excel  
  
1.  Установите в свойстве <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> листа значение перечисления <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#26)]  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Практическое руководство. Программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Практическое руководство. Программная защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  