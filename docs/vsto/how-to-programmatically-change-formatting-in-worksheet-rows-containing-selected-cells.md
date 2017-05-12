---
title: "Практическое руководство. Программное изменение форматирования в строках листа, содержащих выбранные ячейки | Microsoft Docs"
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
  - "форматирование [разработка решений Office в Visual Studio]"
  - "строки [разработка решений Office в Visual Studio]"
  - "листы, изменение форматирования"
ms.assetid: c55cd488-98d1-46c6-9715-0e9212d178de
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Практическое руководство. Программное изменение форматирования в строках листа, содержащих выбранные ячейки
  Можно изменить шрифт всей строки, содержащей выбранную ячейку, сделав ее текст жирным.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Преобразование текущей строки в жирную и возвращение предыдущей жирной строке нормального форматирования  
  
1.  Объявите статическую переменную для отслеживания предыдущей выбранной строки.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#37)]
     [!code-vb[Trin_VstcoreExcelAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#37)]  
  
2.  Извлеките ссылку на текущую ячейку с помощью свойства <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#38)]
     [!code-vb[Trin_VstcoreExcelAutomation#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#38)]  
  
3.  Примените к текущей строке стиль жирного написания с помощью свойства активной ячейки <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#39)]
     [!code-vb[Trin_VstcoreExcelAutomation#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#39)]  
  
4.  Убедитесь в том, что текущее значение элемента `previousRow` не равно 0.  Значение 0 \(ноль\) указывает на то, что код выполняется впервые.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#40](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#40)]
     [!code-vb[Trin_VstcoreExcelAutomation#40](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#40)]  
  
5.  Убедитесь, что текущая строка отличается от предыдущей.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#41](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#41)]
     [!code-vb[Trin_VstcoreExcelAutomation#41](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#41)]  
  
6.  Извлеките ссылку на диапазон, представляющий ранее выбранную строку, а затем отмените жирное начертание для этой строки.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#42)]
     [!code-vb[Trin_VstcoreExcelAutomation#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#42)]  
  
7.  Сохраните текущую строку, чтобы она стала предыдущей строкой при следующем проходе.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#43)]
     [!code-vb[Trin_VstcoreExcelAutomation#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#43)]  
  
 Ниже приведен полный пример метода.  
  
## Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#36)]  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Практическое руководство. Программное копирование данных и форматирование на листах](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  