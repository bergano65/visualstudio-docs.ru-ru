---
title: "Практическое руководство. Программная сортировка данных на листах | Microsoft Docs"
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
  - "данные [разработка решений Office в Visual Studio], сортировка в листах"
  - "сортировка данных, листы"
  - "сортировка данных, в листах"
  - "листы, сортировка данных"
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Практическое руководство. Программная сортировка данных на листах
  Вы можете сортировать данные, содержащиеся в списках и диапазонах листа во время выполнения.  Следующий код сортирует диапазон из нескольких столбцов с именем `Fruits` по данным в первом столбце, а затем по данным во втором столбце.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Сортировка данных в настройке на уровне документа  
  
#### Сортировка данных в элементе управления NamedRange  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  В следующем примере на листе должен находиться элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `Fruits`.  Этот код следует разместить в классе листа, а не в классе `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#78)]  
  
 Поместите следующий код в файл Sheet1.vb или Sheet1.cs для сортировки данных в элементе управления <xref:Microsoft.Office.Tools.Excel.ListObject>.  В коде предполагается, что на листе с именем `Sheet1` есть элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `fruitList`.  
  
#### Сортировка данных в элементе управления ListObject  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> свойства <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#79)]  
  
## Сортировка данных в надстройке VSTO  
  
#### Сортировка данных в собственном диапазоне  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> неуправляемого элемента управления <xref:Microsoft.Office.Interop.Excel.Range> Excel.  В следующем примере на листе должен находиться неуправляемый элемент управления Excel с именем `Fruits`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
#### Сортировка данных в элементе управления ListObject  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> свойства <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> неуправляемого элемента управления <xref:Microsoft.Office.Interop.Excel.ListObject> Excel.  В следующем примере предполагается, что на активном листе есть неуправляемый элемент управления <xref:Microsoft.Office.Interop.Excel.ListObject> Excel с именем `fruitList`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Автоматическое заполнение диапазонов данными, значения которых изменяются с постоянным шагом, с помощью программных средств](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Практическое руководство. Ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Элемент управления ListObject](../vsto/listobject-control.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  