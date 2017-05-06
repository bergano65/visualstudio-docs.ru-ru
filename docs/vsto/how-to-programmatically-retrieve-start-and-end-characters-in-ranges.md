---
title: "Практическое руководство. Программное извлечение символов начала и завершения в диапазонах"
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
  - "диапазоны, извлечение знаков начала и завершения"
  - "знаки завершения"
  - "знаки начала"
  - "документы [разработка решений Office в Visual Studio], получение диапазонов"
ms.assetid: 734c630c-abc9-491d-94b6-429d1fc7a4cc
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Практическое руководство. Программное извлечение символов начала и завершения в диапазонах
  В этом примере показано, как получить позиции символов начала и конца диапазона.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Получение начального и конечного знаков диапазона в настройке уровня документа  
  
1.  Получите значения свойств <xref:Microsoft.Office.Interop.Word.Range.Start%2A> и <xref:Microsoft.Office.Interop.Word.Range.End%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>. В следующем примере кода возвращается позиция начала и конца второго предложения в документе. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomation#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#25)]  
  
### Получение начального и конечного знаков диапазона с помощью надстройки VSTO  
  
1.  Получите значения свойств <xref:Microsoft.Office.Interop.Word.Range.Start%2A> и <xref:Microsoft.Office.Interop.Word.Range.End%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>. В следующем примере кода возвращается позиция начала и конца второго предложения в активном документе. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
## См. также  
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Практическое руководство. Программный сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Практическое руководство. Программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Практическое руководство. Программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Практическое руководство. Программный подсчет символов в документах](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  