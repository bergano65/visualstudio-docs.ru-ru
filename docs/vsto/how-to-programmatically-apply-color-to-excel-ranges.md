---
title: "Практическое руководство. Программное применение цвета к диапазонам Excel"
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
  - "цвет, диапазоны Excel"
  - "форматирование [разработка решений Office в Visual Studio]"
  - "диапазоны, применение цвета"
ms.assetid: a9c40229-5308-459a-9216-7e13d82c7cb5
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Практическое руководство. Программное применение цвета к диапазонам Excel
  Чтобы применить цвет к тексту в диапазоне ячеек, можно использовать элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> или собственный объект диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Использование элемента управления NamedRange  
 В этом примере демонстрируется настройка уровня документа.  
  
#### Применение цвета к элементу управления NamedRange  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейке A1.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#65)]  
  
2.  Задайте цвет текста в элементе управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#66)]  
  
## Использование собственных диапазонов Excel  
  
#### Применение цвета к собственному объекту диапазона Excel  
  
1.  Создайте диапазон, начиная с ячейки A1, а затем установите цвет текста.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#67)]  
  
## См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Практическое руководство. Ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  