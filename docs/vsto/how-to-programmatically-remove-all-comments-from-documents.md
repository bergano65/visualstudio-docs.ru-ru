---
title: "Практическое руководство. Программное удаление всех комментариев из документа | Microsoft Docs"
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
  - "документы [разработка решений Office в Visual Studio], удаление комментариев"
  - "комментарии, удаление из документов"
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Практическое руководство. Программное удаление всех комментариев из документа
  Используйте метод DeleteAllComments для удаления всех комментариев из документа Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Удаление всех комментариев из документа в рамках настройки на уровне документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> класса `ThisDocument` в проекте. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomation#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#119)]  
  
### Удаление всех комментариев из документа с помощью надстройки VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> документа <xref:Microsoft.Office.Interop.Word.Document>, из которого нужно удалить комментарии.  
  
     В приведенном ниже примере кода из активного документа удаляются все комментарии. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#119)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#119)]  
  
## См. также  
 [Практическое руководство. Программное добавление примечаний в текст документа](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)  
  
  