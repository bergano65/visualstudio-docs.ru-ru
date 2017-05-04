---
title: "Практическое руководство. Программное добавление фигур в документ Visio | Microsoft Docs"
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
  - "Visio [разработка решений Office в Visual Studio], добавление фигур Visio"
  - "фигуры [разработка решений Office в Visual Studio], добавление фигур Visio"
ms.assetid: 29613237-88f5-41a7-9e13-cfa177f41221
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Практическое руководство. Программное добавление фигур в документ Visio
  Вы можете добавлять фигуры в документ Microsoft Office Visio, извлекая образцы из набора элементов и помещая фигуры на активной странице.  
  
 Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Document.Save](HV10069241), свойства [Microsoft.Office.Interop.Visio.Application.ActivePage](HV10069528) и метода [Microsoft.Office.Interop.Visio.Page.Drop](HV10070273).  
  
## Добавление фигур в документ Visio  
  
#### Добавление фигур в документ Visio  
  
-   В активном документе извлеките образцы из коллекции Documents.Masters и поместите фигуры в активный документ. Можно извлечь образец, используя индекс или имя образца.  
  
     В следующем примере кода создается пустой документ Visio, который затем открывается с прикрепленным набором элементов **Основные фигуры**. Затем код извлекает несколько фигур и помещает их на активной странице.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#13)]  
  
## См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)   
 [Практическое руководство. Программное копирование и вставка фигур в документе Visio](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  