---
title: "Практическое руководство. Программное скрытие текста в документах | Microsoft Docs"
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
  - "документы [разработка решений Office в Visual Studio], скрытие текста"
  - "текст [разработка решений Office в Visual Studio], скрытие в документах"
ms.assetid: f5ced4ec-22ca-463b-b963-d34ce631b486
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Практическое руководство. Программное скрытие текста в документах
  Текст в документе можно скрыть, установив свойство <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> объекта <xref:Microsoft.Office.Interop.Word.Range.Font%2A> для определенного фрагмента текста.  
  
 Например, можно временно скрыть текст в элементе <xref:Microsoft.Office.Tools.Word.Bookmark> \(в настройке на уровне документа\) или в элементе <xref:Microsoft.Office.Interop.Word.Bookmark> \(в надстройке VSTO\) перед отправкой документа в печать.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Скрытие текста в элементе управления Bookmark при печати документа  
  
1.  Создайте процедуру, которая скрывает весь текст в заданном диапазоне.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#105](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#105)]
     [!code-vb[Trin_VstcoreWordAutomation#105](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#105)]  
  
2.  Создайте процедуру, которая отменяет скрытие текста в заданном диапазоне.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#106](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#106)]
     [!code-vb[Trin_VstcoreWordAutomation#106](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#106)]  
  
3.  Передайте диапазон закладки в метод `HideText`, напечатайте документ, а затем передайте тот же диапазон в метод `UnhideText`.  
  
     Следующий пример кода можно использовать в настройке на уровне документа. Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomation#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#107)]  
  
     Приведенный ниже пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#107)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#107)]  
  
## Компиляция кода  
 В этом примере кода предполагается, что документ содержит элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> \(в настройке на уровне документа\) или элемент управления <xref:Microsoft.Office.Interop.Word.Bookmark> \(в надстройке VSTO\) с именем `bookmark1`.  
  
## См. также  
 [Практическое руководство. Программная печать документов](../vsto/how-to-programmatically-print-documents.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое руководство. Программный сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Практическое руководство. Программное обновление текста закладки](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  