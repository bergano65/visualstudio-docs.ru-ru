---
title: Как выполнить Программным способом хранения и извлечения значений дат в диапазонах Excel
ms.date: 02/02/2017
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a28a357aa6a01615d269c6fba41c690f41c7b93d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863908"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Как выполнить Программным способом хранения и извлечения значений дат в диапазонах Excel
  Можно сохранять и извлекать значения в <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления или собственный объект диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Если вы храните значение даты, которое находится в течение или после 1/1/1900 диапазон с помощью средств разработки Office в Visual Studio, он хранится в формате OLE-автоматизации (OA). Необходимо использовать <xref:System.DateTime.FromOADate%2A> метод для извлечения значение даты OLE-автоматизации (OA). Если дата является более ранней, чем 1/1/1900 г., он хранится в виде строки.  
  
> [!NOTE]  
>  Даты Excel отличаются от даты OLE-автоматизации для первых двух месяцев 1900. Существуют также различия Если **система дат 1904** флажок. В примерах кода не используют эти различия.  
  
## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange  
  
-   Этот пример предназначен для настроек уровня документа. Следующий код должен быть помещен в классе листа, не в `ThisWorkbook` класса.  
  
### <a name="to-store-a-date-value-in-a-named-range"></a>Для хранения значения даты в именованный диапазон  
  
1.  Создание <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в ячейке **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Задайте сегодняшнюю дату в качестве значения для `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Для получения значения даты из именованного диапазона  
  
1.  Получите значение даты из `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="use-native-excel-ranges"></a>Использование собственного диапазонах Excel  
  
### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Для хранения значения даты в собственный объект диапазона Excel  
  
1.  Создание <xref:Microsoft.Office.Interop.Excel.Range> , представляющий ячейку **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Задайте сегодняшнюю дату в качестве значения для `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Для получения значения даты из собственный объект диапазона Excel  
  
1.  Получите значение даты из `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Обзор объектной модели Excel](../vsto/excel-object-model-overview.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Практическое руководство. Ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
