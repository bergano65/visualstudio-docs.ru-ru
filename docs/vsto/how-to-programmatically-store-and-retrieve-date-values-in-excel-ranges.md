---
title: "Практическое руководство. Программное хранение и извлечение значений дат в диапазонах Excel | Microsoft Docs"
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
  - "значения даты"
  - "значения даты, сортировка в диапазонах Excel"
  - "даты, извлечение из диапазонов Excel"
  - "даты, сортировка в диапазонах Excel"
  - "Excel [разработка решений Office в Visual Studio], извлечение значений даты из диапазонов"
  - "Excel [разработка решений Office в Visual Studio], хранение значений даты в диапазонах"
  - "диапазоны, извлечение значений данных"
  - "диапазоны, хранение значений даты"
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Практическое руководство. Программное хранение и извлечение значений дат в диапазонах Excel
  Значения можно сохранять и извлекать из элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> или собственного объекта "диапазон" Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Если значение даты, которое равно 01.01.1900 или находится позже, сохраняется в диапазон с помощью средств разработки Office в Visual Studio, то оно приобретает формат OLE\-автоматизации \(OA\).  Чтобы извлечь значения дат в формате OLE\-автоматизации \(OA\), необходимо использовать метод <xref:System.DateTime.FromOADate%2A>.  Если дата меньше 01.01.1900, то она сохраняется в виде строки.  
  
> [!NOTE]  
>  Даты Excel отличаются от дат OLE\-автоматизации для двух первых месяцев 1900 года.  Кроме того, при выбранном параметре **Система дат 1904** возможны другие различия.  Указанные ниже примеры кодов не используют эти отличия.  
  
## Использование элемента управления NamedRange  
  
-   В этом примере демонстрируется настройка уровня документа.  Данный код необходимо поместить в класс листа, а не в класс `ThisWorkbook`.  
  
#### Сохранение значения даты в именованном диапазоне  
  
1.  Создайте элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейке **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#50)]  
  
2.  Задайте сегодняшнюю дату в качестве значения для `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#51)]  
  
#### Извлечение значения даты из именованного диапазона  
  
1.  Извлеките значение даты из `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#52)]  
  
## Использование собственных диапазонов Excel  
  
#### Сохранение значения даты в собственном объекте "диапазон" Excel  
  
1.  Создайте объект <xref:Microsoft.Office.Interop.Excel.Range>, представляющий ячейку **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#25)]  
  
2.  Задайте сегодняшнюю дату в качестве значения для `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
#### Извлечение значения даты из собственного объекта "диапазон" Excel  
  
1.  Извлеките значение даты из `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
## См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Практическое руководство. Ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  