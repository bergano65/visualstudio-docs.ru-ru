---
title: "Практическое руководство. Программное форматирование текста в документах"
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
  - "форматирование [разработка решений Office в Visual Studio]"
  - "документы [разработка решений Office в Visual Studio], форматирование текста"
  - "текст [разработка решений Office в Visual Studio], форматирование в документах"
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Практическое руководство. Программное форматирование текста в документах
  Вы можете использовать объект <xref:Microsoft.Office.Interop.Word.Range> для форматирования текста в документе Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Следующий пример выделяет первый абзац в документе и изменяет размер шрифта, имя шрифта и тип выравнивания. Затем он выбирает диапазон и отображает окно сообщения о приостановке перед выполнением следующего раздела кода. Следующий раздел три раза вызывает метод Undo ведущего элемента <xref:Microsoft.Office.Tools.Word.Document> \(для настройки уровня документа\) или класса <xref:Microsoft.Office.Interop.Word.Document> \(для надстройки VSTO\). Применяется стиль «Обычный отступ» и отображается окно сообщения о приостановке выполнения кода. Затем код вызывает метод <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> один раз и показывает окно сообщения.  
  
## Пример настройки на уровне документа  
  
#### Форматирование текста с помощью настройки на уровне документа  
  
1.  Следующий пример можно использовать в настройке на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomation#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#62)]  
  
## Примеры надстройки VSTO  
  
#### Форматирование текста с использованием надстройки VSTO  
  
1.  Следующий пример можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#62)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#62)]  
  
## См. также  
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое руководство. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Практическое руководство. Программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  