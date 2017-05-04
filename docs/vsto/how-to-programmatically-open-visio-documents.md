---
title: "Практическое руководство. Программное открытие документов Visio | Microsoft Docs"
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
  - "документы [разработка решений Office в Visual Studio], открытие документов Visio"
  - "Visio [разработка решений Office в Visual Studio], открытие документов Visio"
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Практическое руководство. Программное открытие документов Visio
  Существует два метода для открытия существующих документов Microsoft Office Visio: Open и OpenEx. Метод OpenEx аналогичен методу Open за исключением того, что он содержит аргументы, в которых вызывающий объект может указать параметры открытия документа.  
  
 Подробные сведения об объектной модели см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Open](HV10070351) и метода [Microsoft.Office.Interop.Visio.Documents.OpenEx](HV10071456).  
  
## Открытие документа Visio  
  
#### Открытие документа Visio  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.Open и укажите полный путь к документу Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#5)]  
  
## Открытие документа Visio с заданными аргументами  
  
#### Открытие документа Visio как закрепленного и доступного только для чтения  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Documents.OpenEx, укажите полный путь к документу Visio и включите аргументы, которые вы хотите использовать — в данном случае Docked и Read\-only.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#6)]  
  
## Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Документ Visio с именем `myDrawing.vsd` должен быть расположен в каталоге с именем `Test` в папке "Мои документы" \(для Windows XP и более ранних версий\) или в папке "Документы" \(для Windows Vista\).  
  
## См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Практическое руководство. Программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Практическое руководство. Программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Практическое руководство. Программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  