---
title: "Практическое руководство. Программное заполнение таблиц свойствами документа Word"
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
  - "свойства документа, вставка в таблицы Word"
  - "документы [разработка решений Office в Visual Studio], свойства документа"
ms.assetid: 7ed65a3d-58ed-43b3-92d6-dc10a2c331db
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Практическое руководство. Программное заполнение таблиц свойствами документа Word
  Следующий пример создает таблицу Microsoft Office Word в верхней части документа и заполняет свойства ведущего документа.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Заполнение таблиц в настройке на уровне документа  
  
#### Создание и заполнение таблицы свойствами документа  
  
1.  Задайте диапазон как начало документа.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomation#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#90)]  
  
2.  Вставьте заголовок таблицы и укажите знаки абзаца.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomation#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#91)]  
  
3.  Добавьте таблицу в документ в диапазоне.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomation#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#92)]  
  
4.  Отформатируйте таблицу и примените стиль.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomation#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#93)]  
  
5.  Вставьте свойства документа в ячейки.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomation#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#94)]  
  
 В следующем примере показана полная процедура.  Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomation#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#89)]  
  
## Заполнение таблиц в надстройках VSTO  
  
#### Создание и заполнение таблицы свойствами документа  
  
1.  Задайте диапазон как начало документа.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#90](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#90)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#90](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#90)]  
  
2.  Вставьте заголовок таблицы и укажите знаки абзаца.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#91](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#91)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#91](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#91)]  
  
3.  Добавьте таблицу в документ в диапазоне.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#92](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#92)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#92](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#92)]  
  
4.  Отформатируйте таблицу и примените стиль.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#93](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#93)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#93](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#93)]  
  
5.  Вставьте свойства документа в ячейки.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#94](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#94)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#94](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#94)]  
  
 В следующем примере показана полная процедура.  Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#89](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#89)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#89](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#89)]  
  
## См. также  
 [Практическое руководство. Программное таблиц в Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Практическое руководство. Программное добавление текста и форматирования в ячейки таблиц Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Практическое руководство. Программное добавление строк и столбцов в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  