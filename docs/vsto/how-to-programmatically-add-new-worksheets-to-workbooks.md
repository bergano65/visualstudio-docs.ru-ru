---
title: "Практическое руководство. Программное добавление новых листов в книги Excel"
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
  - "книги, добавление листов"
  - "книги, создание листов"
  - "книги, создание"
  - "книги, добавление в книги"
ms.assetid: 19f0d815-51b2-406c-9f36-34aa0ec16b4a
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Практическое руководство. Программное добавление новых листов в книги Excel
  Можно программно создать лист и затем добавить лист в коллекцию листов в книге.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Добавление нового листа в книгу в настройке на уровне документа  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#15)]  
  
     Новый лист — это собственный объект <xref:Microsoft.Office.Interop.Excel.Worksheet>, а не ведущий элемент. Если вы хотите добавить ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet>, следует добавить лист во время разработки.  
  
### Добавление нового листа к книге в надстройке VSTO  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
     Новый лист — это собственный объект <xref:Microsoft.Office.Interop.Excel.Worksheet>, а не ведущий элемент. Также можно создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> из собственного объекта <xref:Microsoft.Office.Interop.Excel.Worksheet>. Дополнительные сведения см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Практическое руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Практическое руководство. Программный выбор листов Excel](../vsto/how-to-programmatically-select-worksheets.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  