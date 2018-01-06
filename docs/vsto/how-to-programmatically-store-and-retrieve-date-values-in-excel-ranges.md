---
title: "Как: программное хранение и извлечение значений дат в диапазонах Excel | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
ms.assetid: e1cdd262-0356-4499-8bc5-e730f74235a2
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8783a36ac4b15aead5ddb62badd9b56a3c1fa525
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Практическое руководство. Программное хранение и извлечение значений дат в диапазонах Excel
  Можно сохранять и извлекать значения в <xref:Microsoft.Office.Tools.Excel.NamedRange> управления или собственный объект диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Если значение даты, которое находится в течение или после 1/1/1900 диапазон с помощью средств разработки Office в Visual Studio, сохраняется в формате OLE-автоматизации (OA). Необходимо использовать <xref:System.DateTime.FromOADate%2A> метода требуется извлечь значение даты OLE-автоматизации (OA). Если дата является более ранней, чем 1/1/1900, он хранится в виде строки.  
  
> [!NOTE]  
>  Даты Excel отличаются от дат OLE-автоматизации для первых двух месяцев 1900 года. Существуют также различия при **система дат 1904** флажок. В примерах кода не рассматриваются эти различия.  
  
## <a name="using-a-namedrange-control"></a>С помощью элемента управления NamedRange  
  
-   Этот пример предназначен для настроек на уровне документа. Следующий код следует разместить в классе листа, а не в `ThisWorkbook` класса.  
  
#### <a name="to-store-a-date-value-in-a-named-range"></a>Для хранения значения даты в именованном диапазоне  
  
1.  Создание <xref:Microsoft.Office.Tools.Excel.NamedRange> управления в ячейке **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Задайте сегодняшнюю дату в качестве значения для `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
#### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Для получения значения даты из именованного диапазона  
  
1.  Извлеките значение даты из `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="using-native-excel-ranges"></a>Использование собственных диапазонов Excel  
  
#### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Для хранения значения даты в собственный объект диапазона Excel  
  
1.  Создание <xref:Microsoft.Office.Interop.Excel.Range> , представляющий ячейку **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Задайте сегодняшнюю дату в качестве значения для `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
#### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Для получения значения даты из собственного объекта диапазона Excel  
  
1.  Извлеките значение даты из `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Общие сведения о модели объектов Excel](../vsto/excel-object-model-overview.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Как: ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Как: Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  