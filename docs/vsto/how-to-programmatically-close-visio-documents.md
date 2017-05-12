---
title: "Практическое руководство. Программное закрытие документов Visio"
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
  - "документы [разработка решений Office в Visual Studio], закрытие документов Visio"
  - "Visio [разработка решений Office в Visual Studio], закрытие документов Visio"
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Практическое руководство. Программное закрытие документов Visio
  Вы можете закрыть активный документ Microsoft Office Visio с помощью метода Microsoft.Office.Interop.Visio.Document.Close.  
  
 Сведения об этом методе см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Add](HV10070225).  
  
## Закрытие активного документа  
  
#### Закрытие активного документа  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Document.Close, чтобы закрыть активный документ.  
  
     Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#7)]  
  
## См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Практическое руководство. Программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Практическое руководство. Программное открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Практическое руководство. Программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  