---
title: "Практическое руководство. Программное открытие книг Excel"
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
  - "Excel [разработка решений Office в Visual Studio], открытие книг Excel"
  - "книги, открытие"
ms.assetid: 06c0ac87-a2c6-4cc1-87be-39be0cb81c71
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Практическое руководство. Программное открытие книг Excel
  Коллекция <xref:Microsoft.Office.Interop.Excel.Workbooks> в Microsoft Office Excel дает возможность работать со всеми открытыми книгами и открывать книги.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Открытие существующей книги  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Workbooks>, передав ему путь к книге.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#2)]  
  
## Компиляция кода  
 Для выполнения этого примера кода требуется следующее:  
  
-   Книга с именем `YourWorkbook.xls`, должна существовать в каталоге с именем `Test` на диске C.  
  
## См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Практическое руководство. Программное открытие текстовых файлов как книг Excel](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Практическое руководство. Программное создание книг Excel](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Практическое руководство. Программное сохранение книг Excel](../vsto/how-to-programmatically-save-workbooks.md)   
 [Практическое руководство. Программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  