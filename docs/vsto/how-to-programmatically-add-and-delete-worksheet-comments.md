---
title: "Практическое руководство. Программное добавление и удаление примечаний на листе | Microsoft Docs"
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
  - "диапазоны, комментарии"
  - "листы, комментарии"
  - "комментарии, листы"
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Практическое руководство. Программное добавление и удаление примечаний на листе
  Вы можете добавлять и удалять комментарии в листах Microsoft Office Excel программными средствами. Комментарии можно добавлять только в отдельные ячейки, а не в диапазоны из нескольких ячеек.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Добавление и удаление комментария в проекте уровня документа  
 В следующих примерах предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `dateComment` в одной ячейке в листе с именем `Sheet1`.  
  
#### Добавление нового комментария в именованный диапазон  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> и укажите текст примечания. Этот код следует разместить в классе `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#30)]  
  
#### Удаление комментария из именованного диапазона  
  
1.  Проверьте наличие комментария в диапазоне и удалите его. Этот код следует разместить в классе `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#29)]  
  
## Добавление и удаление комментария в проекте надстройки VSTO  
 В следующих примерах предполагается, что имеется элемент управления <xref:Microsoft.Office.Interop.Excel.Range> с именем `dateComment` в одной ячейке в активном листе.  
  
#### Добавление нового комментария в диапазон Excel  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> элемента управления <xref:Microsoft.Office.Interop.Excel.Range> и укажите текст примечания.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
#### Удаление нового комментария из диапазона Excel  
  
1.  Проверьте наличие комментария в диапазоне и удалите его.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Программное отображение примечаний на листе](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)  
  
  