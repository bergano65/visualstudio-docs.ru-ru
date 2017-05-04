---
title: "Практическое руководство. Программное добавление текста и форматирования в ячейки таблиц Word | Microsoft Docs"
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
  - "ячейки, добавление текста и форматирование"
  - "форматирование [разработка решений Office в Visual Studio]"
  - "таблицы [разработка решений Office в Visual Studio], добавление текста и форматирование"
  - "текст [разработка решений Office в Visual Studio], добавление к таблицам Word"
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Практическое руководство. Программное добавление текста и форматирования в ячейки таблиц Word
  Каждая таблица представляет собой набор ячеек.  Каждый отдельный объект <xref:Microsoft.Office.Interop.Word.Cell> представляет одну ячейку в таблице.  Обращайтесь к каждой ячейке по ее расположению в таблице.  Этот пример ссылается на ячейку, расположенную в первой строке и первом столбце таблицы, добавляет в ячейку текст и применяет форматирование.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Добавление текста и форматирования в ячейки  
  
1.  Обратитесь к ячейке по ее расположению в таблице, добавьте текст в ячейку и примените форматирование.  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomation#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#97)]  
  
     Следующий пример кода можно использовать в надстройке VSTO.  В этом примере используется активный документ.  Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#97)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#97)]  
  
## См. также  
 [Практическое руководство. Программное таблиц в Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Практическое руководство. Программное добавление строк и столбцов в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Практическое руководство. Программное заполнение таблиц свойствами документа Word](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  