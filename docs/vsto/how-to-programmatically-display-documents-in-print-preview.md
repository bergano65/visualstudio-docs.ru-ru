---
title: "Практическое руководство. Программное отображение документов в режиме предварительного просмотра | Microsoft Docs"
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
  - "Word [разработка решений Office в Visual Studio], отображение документов в режиме предварительного просмотра"
  - "документы [разработка решений Office в Visual Studio], отображение в режиме предварительного просмотра"
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Практическое руководство. Программное отображение документов в режиме предварительного просмотра
  Если решение создает отчет, может потребоваться отображение отчета пользователю в режиме предварительного просмотра отчета.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Процедуры для настроек уровня документа  
  
#### Отображение документа в режиме предварительного просмотра путем вызова метода PrintPreview  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> класса <xref:Microsoft.Office.Tools.Word.Document>. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomation#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#13)]  
  
#### Отображение документа в режиме предварительного просмотра путем установки свойства PrintPreview  
  
1.  Присвойте свойству <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> объекта <xref:Microsoft.Office.Interop.Word.Application> значение **true**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## Процедуры для надстроек VSTO  
  
#### Отображение документа в режиме предварительного просмотра путем вызова метода PrintPreview  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> документа <xref:Microsoft.Office.Interop.Word.Document>, который требуется открыть в режиме предварительного просмотра. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
#### Отображение документа в режиме предварительного просмотра путем установки свойства PrintPreview  
  
1.  Присвойте свойству <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> объекта <xref:Microsoft.Office.Interop.Word.Application> значение **true**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreWordAutomation#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#14)]  
  
## См. также  
 [Практическое руководство. Программная печать документов](../vsto/how-to-programmatically-print-documents.md)   
 [Практическое руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Практическое руководство. Программное создание документов](../vsto/how-to-programmatically-create-new-documents.md)  
  
  