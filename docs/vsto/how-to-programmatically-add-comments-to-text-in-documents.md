---
title: "Практическое руководство. Программное добавление примечаний в текст документа | Microsoft Docs"
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
  - "комментарии, добавление к документам"
  - "документы [разработка решений Office в Visual Studio], добавление комментариев"
ms.assetid: 4e396e31-01bf-424c-be6b-9a1806bcd572
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Практическое руководство. Программное добавление примечаний в текст документа
  Свойство Comments класса Document добавляет комментарий к диапазону текста в документе Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 В следующем примере комментарий добавляется в первый абзац документа.  
  
### Добавление нового комментария в текст в настройке уровня документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> свойства <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> и укажите диапазон и текст комментария. Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomation#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#118)]  
  
### Добавление нового комментария в текст в надстройке VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> свойства <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> и укажите диапазон и текст комментария.  
  
     В следующем примере кода добавляется комментарий в активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#118)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#118)]  
  
## Отказоустойчивость  
 Для изменения инициалов пользователя, добавляемых Word в комментарии, используйте свойство <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A>.  
  
## См. также  
 [Практическое руководство. Программное удаление всех комментариев из документа](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)  
  
  