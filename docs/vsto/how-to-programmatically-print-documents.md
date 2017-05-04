---
title: "Практическое руководство. Программная печать документов | Microsoft Docs"
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
  - "Word [разработка решений Office в Visual Studio], печать документов"
  - "документы [разработка решений Office в Visual Studio], печать"
ms.assetid: 99285d98-1bb7-4ccb-83d9-e917b0a9ea42
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Практическое руководство. Программная печать документов
  Вы можете распечатать весь документ Microsoft Office Word или часть документа, на принтере по умолчанию.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Печать документа, который является частью настройки уровня документа  
  
#### Печать всего документа  
  
1.  Чтобы напечатать весь документ, вызовите в своем проекте метод <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> класса `ThisDocument`. Чтобы использовать этот пример, запустите код из класса `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomation#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#11)]  
  
#### Печать текущей страницы документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> класса `ThisDocument` в своем проекте и укажите, что необходимо напечатать одну копию текущей страницы. Чтобы использовать этот пример, запустите код из класса `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomation#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#12)]  
  
## Печать документа с помощью надстройки VSTO  
  
#### Печать всего документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> документа <xref:Microsoft.Office.Interop.Word.Document>, который требуется напечатать. В следующем примере кода печатается активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
#### Печать текущей страницы документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> класса <xref:Microsoft.Office.Interop.Word.Document> объекта, который требуется напечатать, и укажите, что необходимо напечатать одну копию текущей страницы. В следующем примере кода печатается активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## См. также  
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  