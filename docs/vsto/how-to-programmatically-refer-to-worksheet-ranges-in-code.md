---
title: "Практическое руководство. Ссылки на диапазоны листов в коде программными средствами"
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
  - "Excel [разработка решений Office в Visual Studio], диапазоны листа - ссылка"
  - "диапазоны, ссылка на"
  - "диапазоны листа - ссылка"
  - "листы, ссылка на диапазоны"
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Практическое руководство. Ссылки на диапазоны листов в коде программными средствами
  Подобный процесс используется для ссылок на содержимое элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> или собственного объекта диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Использование элемента управления NamedRange  
 В приведенном ниже примере кода на лист добавляется объект <xref:Microsoft.Office.Tools.Excel.NamedRange>, после чего в ячейку в диапазоне добавляется текст.  
  
#### Ссылка на элемент управления NamedRange  
  
1.  Присвойте строковое значение <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  Данный код необходимо поместить в класс листа, а не в класс `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#46)]  
  
## Использование собственных диапазонов Excel  
 В приведенном ниже примере кода на лист добавляется собственный диапазон Excel, после чего в ячейку в диапазоне добавляется текст.  
  
#### Ссылка на собственный объект диапазона  
  
1.  Присвойте строковое значение свойству <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#47)]  
  
## См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Практическое руководство. Программная проверка орфографии на листах](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Практическое руководство. Автоматическое заполнение диапазонов данными, значения которых изменяются с постоянным шагом, с помощью программных средств](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Практическое руководство. Программный поиск текста в диапазонах ячеек на листе](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  