---
title: "Практическое руководство. Программное отображение примечаний на листе | Microsoft Docs"
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
  - "листы, комментарии"
  - "комментарии, листы"
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Практическое руководство. Программное отображение примечаний на листе
  Вы можете отображать и скрывать комментарии в листах Microsoft Office Excel программными средствами.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Отображение всех комментариев на листе в настройке уровня документа  
  
1.  Присвойте свойству <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> значение **true**, если нужно отображать комментарии; в противном случае присвойте ему значение **false**. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#31)]  
  
### Отображение всех комментариев на листе в надстройке VSTO уровня приложения  
  
1.  Присвойте свойству <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> значение **true**, если нужно отображать комментарии; в противном случае присвойте ему значение **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Программное добавление и удаление примечаний на листе](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  