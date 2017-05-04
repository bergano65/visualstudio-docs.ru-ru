---
title: "Практическое руководство. Программное создание книг Excel | Microsoft Docs"
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
  - "Excel [разработка решений Office в Visual Studio], создание книг Excel"
  - "книги, создание"
ms.assetid: be0196fe-7dc5-4811-b0cd-3c219731a3ff
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Практическое руководство. Программное создание книг Excel
  При создании книги программными средствами она является собственным объектом <xref:Microsoft.Office.Interop.Excel.Workbook>, а не ведущим элементом <xref:Microsoft.Office.Tools.Excel.Workbook>.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 В проекте надстройки VSTO можно создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> для объекта <xref:Microsoft.Office.Interop.Excel.Workbook>.  Дополнительные сведения см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### Создание новой книги  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Workbooks>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#1)]  
  
    > [!NOTE]  
    >  Книгу можно создать на основе шаблона, отличного от шаблона по умолчанию: для этого требуемый шаблон следует передать в качестве параметра в метод <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>.  
  
## См. также  
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Практическое руководство. Программное открытие книг Excel](../vsto/how-to-programmatically-open-workbooks.md)   
 [Практическое руководство. Программное сохранение книг Excel](../vsto/how-to-programmatically-save-workbooks.md)   
 [Практическое руководство. Программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  