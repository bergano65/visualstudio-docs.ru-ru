---
title: "Практическое руководство. Программное перечисление всех листов в книге | Microsoft Docs"
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
  - "книги, список листов"
  - "листы, список"
ms.assetid: 38b63d1d-6047-44e8-b089-c576c6179e4a
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Практическое руководство. Программное перечисление всех листов в книге
  Класс <xref:Microsoft.Office.Interop.Excel.Workbook> предоставляет объект <xref:Microsoft.Office.Interop.Excel.Worksheets>.  Этот объект содержит коллекцию всех объектов <xref:Microsoft.Office.Interop.Excel.Worksheet> в книге.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Составление списка существующих в книге листов в настройке уровня документа  
  
1.  Следует выполнить итерацию коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets> и отправить имя каждого листа в смещение ячейки из элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#21)]  
  
### Составление списка существующих в книге листов в надстройке VSTO  
  
1.  Следует выполнить итерацию коллекции <xref:Microsoft.Office.Interop.Excel.Worksheets> и отправить имя каждого листа в смещение ячейки из объекта <xref:Microsoft.Office.Interop.Excel.Range>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Программное добавление новых листов в книги Excel](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Практическое руководство. Программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  