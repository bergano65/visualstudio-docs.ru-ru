---
title: "Практическое руководство. Программное задание параметров поиска в Word | Microsoft Docs"
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
  - "документы [разработка решений Office в Visual Studio], параметры поиска"
  - "поиск, параметры Word"
  - "параметры, параметры поиска Word"
  - "Word, параметры поиска"
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Практическое руководство. Программное задание параметров поиска в Word
  Предусмотрено два способа установки параметров поиска в объекте выделения в документах Microsoft Office Word:  
  
-   Установка отдельных свойств объекта <xref:Microsoft.Office.Interop.Word.Find>.  
  
-   Использование аргументов метода <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> объекта <xref:Microsoft.Office.Interop.Word.Find>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Использование свойств объекта Find  
 В следующем примере кода устанавливаются свойства объекта <xref:Microsoft.Office.Interop.Word.Find>, определяющие порядок поиска текста в текущем объекте выделения.  Обратите внимание, что условия поиска, например поиск вперед, обтекание текстом и искомый текст, являются свойствами объекта <xref:Microsoft.Office.Interop.Word.Find>.  
  
 Устанавливать свойства объекта <xref:Microsoft.Office.Interop.Word.Find> при написании кода C\# не требуется, поскольку в этом случае также необходимо устанавливать эти свойства в качестве параметров метода <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  В связи с этим в этом примере представлен только код Visual Basic.  
  
#### Установка параметров поиска с помощью объекта Find  
  
1.  Установите свойства объекта <xref:Microsoft.Office.Interop.Word.Find>, определяющие поиск вперед текста **find me** в объекте выделения.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#76)]  
  
## Использование аргументов метода Execute  
 В следующем коде для поиска текста в текущем объекте выделения используется метод <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> объекта <xref:Microsoft.Office.Interop.Word.Find>.  Обратите внимание, что условия поиска, например поиск вперед, обтекание текстом и искомый текст, передаются в качестве параметров метода <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  
  
#### Установка параметров поиска с помощью аргументов метода Execute  
  
1.  Передайте условия поиска в качестве параметров метода <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>, чтобы выполнить поиск вперед текста **find me** в объекте выделения.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#77](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#77)]
     [!code-vb[Trin_VstcoreWordAutomation#77](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#77)]  
  
## См. также  
 [Практическое руководство. Программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Практическое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Практическое руководство. Программное восстановление выделения после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  