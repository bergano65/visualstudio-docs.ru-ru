---
title: "Практическое руководство. Программная проверка правописания в документах | Microsoft Docs"
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
  - "документы [разработка решений Office в Visual Studio], проверка орфографии"
  - "средство проверки орфографии, документы"
ms.assetid: 5bbe3a8d-fc65-4f57-bd63-5bb549dbc4bd
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Практическое руководство. Программная проверка правописания в документах
  Чтобы выполнить проверку правописания в документе, воспользуйтесь методом <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>.  Этот метод возвращает логическое значение, указывающее на правильность написания данного параметра.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Проверка правописания и отображение результатов в окне сообщения  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> и передайте ему фрагмент текста, в котором необходимо выполнить проверку правописания.  Чтобы воспользоваться следующим примером кода, выполните его из класса `ThisDocument` или `ThisAddIn` своего проекта.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#113](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#113)]
     [!code-vb[Trin_VstcoreWordAutomation#113](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#113)]  
  
## См. также  
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  