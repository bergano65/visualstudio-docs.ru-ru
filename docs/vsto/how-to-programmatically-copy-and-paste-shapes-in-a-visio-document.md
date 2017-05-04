---
title: "Практическое руководство. Программное копирование и вставка фигур в документе Visio | Microsoft Docs"
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
  - "фигуры [разработка решений Office в Visual Studio], копирование и вставка фигур Visio"
  - "Visio [разработка решений Office в Visual Studio], копирование и вставка фигур Visio"
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Практическое руководство. Программное копирование и вставка фигур в документе Visio
  Вы можете программными средствами копировать фигуры на одной странице документа и вставлять их в новую страницу того же документа. Можно вставлять их в расположение по умолчанию \(центр активного окна\) или в то же расположение, в котором они находились на исходной странице.  
  
## Копирование и вставка фигур  
 Подробные сведения об объектной модели см. в справочной документации VBA для методов [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304), [Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300), [Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) и [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) и для флага [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](HV10071835).  
  
#### Копирование фигур в центр другой страницы  
  
-   В следующем примере показано, как копировать фигуры с первой страницы и вставлять их в центр второй страницы.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#14)]  
  
## Копирование и вставка фигур с сохранением расположения  
 Подробные сведения об объектной модели см. в справочной документации VBA для методов [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](HV10070304), [Microsoft.Office.Interop.Visio.Shape.DrawOval](HV10070300), [Microsoft.Office.Interop.Visio.Shape.Copy](HV10070291) и [Microsoft.Office.Interop.Visio.Shape.Paste](HV10070437) и для флага [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](HV10071835).  
  
 Если нужно управлять форматом вставляемых данных и \(дополнительно\) установить ссылку на исходный файл \(например, на документ Microsoft Office Word\), используйте метод PasteSpecial.  
  
#### Копирование фигур и их расположений на другую страницу  
  
-   В следующем примере показано, как копировать фигуры с первой страницы и вставлять их в те же места на второй странице.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#15)]  
  
## См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)   
 [Практическое руководство. Программное добавление фигур в документ Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  