---
title: "Практическое руководство. Программное открытие существующих документов"
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
  - "документы [разработка решений Office в Visual Studio], открытие"
  - "Word [разработка решений Office в Visual Studio], открытие документов"
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Практическое руководство. Программное открытие существующих документов
  Метод <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> открывает существующий документ Microsoft Office Word, заданный полным путем и именем файла.  Этот метод возвращает объект <xref:Microsoft.Office.Interop.Word.Document>, представляющий открытый документ.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Открытие документа  
  
-   Вызовите метод <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> коллекции <xref:Microsoft.Office.Interop.Word.Documents> и предоставьте путь к документу.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreWordAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#5)]  
  
### Открытие документа только для чтения  
  
-   Вызовите метод <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>, предоставьте путь к документу и при вызове метода установите для аргумента *ReadOnly* значение **True**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreWordAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#6)]  
  
## Компиляция кода  
 Для выполнения этого примера кода требуется следующее:  
  
-   в каталоге Test на диске C должен существовать документ с именем NewDocument.doc.  
  
## См. также  
 [Практическое руководство. Программное создание документов](../vsto/how-to-programmatically-create-new-documents.md)   
 [Практическое руководство. Программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  