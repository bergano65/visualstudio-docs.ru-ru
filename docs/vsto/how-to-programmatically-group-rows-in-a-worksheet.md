---
title: "Практическое руководство. Программная группировка строк на листах"
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
  - "столбцы [разработка решений Office в Visual Studio], разгруппирование"
  - "группы"
  - "группы [разработка решений Office в Visual Studio], очистка в листах"
  - "группы, создание в листах"
  - "диапазоны, создание групп"
  - "строки [разработка решений Office в Visual Studio], разгруппирование"
  - "листы, группы очистки"
  - "листы, создание групп"
  - "листы, разгруппирование строк и столбцов"
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Практическое руководство. Программная группировка строк на листах
  Существует возможность группирования одной или нескольких полных строк.  Для создания группы в листе используется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> или собственный объект "диапазон" Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Использование элемента управления NamedRange  
 Если элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> добавляется в проект уровня документа во время разработки, то можно использовать этот элемент управления для создания группы программными средствами.  В следующем примере предполагается наличие на одном листе трех элементов управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именами `data2001`, `data2002` и `dataAll`.  Каждый именованный диапазон относится к целой строке в листе.  
  
#### Создание группы элементов управления NamedRange на листе  
  
1.  Чтобы сгруппировать три именованных диапазона, вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> каждого из них.  Данный код необходимо поместить в класс листа, а не в класс `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Чтобы разгруппировать строки, вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A>.  
  
## Использование собственных диапазонов Excel  
 В следующем примере предполагается наличие на листе трех диапазонов Excel с именами `data2001`, `data2002` и `dataAll`.  
  
#### Создание группы диапазонов Excel на листе  
  
1.  Чтобы сгруппировать три именованных диапазона, вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> каждого из них.  В следующем примере предполагается наличие на одном листе трех элементов управления <xref:Microsoft.Office.Interop.Excel.Range> с именами `data2001`, `data2002` и `dataAll`.  Каждый именованный диапазон относится к целой строке в листе.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Чтобы разгруппировать строки, вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A>.  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  