---
title: "Практическое руководство. Программный подсчет символов в документах | Microsoft Docs"
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
  - "знаки, подсчет в документах"
  - "подсчет знаков в документах"
  - "документы [разработка решений Office в Visual Studio], подсчет знаков"
ms.assetid: ab64fe87-896a-4b56-bdf8-91c4326b540e
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 36
---
# Практическое руководство. Программный подсчет символов в документах
  Первый знак в документ находится в позиции 0, которая представляет точку вставки. Позиция последнего знака равна общему количеству знаков в документе. Число знаков в документе можно определить с помощью свойства <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> коллекции <xref:Microsoft.Office.Interop.Word.Characters>.  
  
 Учитываются все знаки в документе, включая пробелы, знаки абзацев и другие знаки, которые обычно скрыты. Даже новый пустой документ возвращает значение 1, так как он содержит знак абзаца.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Отображение числа знаков в настройке уровня документа  
  
1.  Выделите весь документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomation#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#98)]  
  
2.  Отобразите количество знаков в документе в окне сообщения.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomation#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#99)]  
  
### Отображение числа знаков в надстройке VSTO  
  
1.  Выделите весь документ. В следующем примере кода выбирается активный документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#98)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#98)]  
  
2.  Отобразите количество знаков в документе в окне сообщения.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#99)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#99)]  
  
## См. также  
 [Практическое руководство. Программное извлечение символов начала и завершения в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  