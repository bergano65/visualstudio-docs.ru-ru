---
title: Руководство. программное выполнение вычислений Excel
description: Узнайте, как можно использовать Visual Studio для программного выполнения вычислений в книге Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9f385e7c58972844c30320c680f42d8394580d8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524698"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Руководство. программное выполнение вычислений Excel
  Аналогичный процесс используется для выполнения вычислений в <xref:Microsoft.Office.Tools.Excel.NamedRange> элементе управления или в собственном объекте Excel Range.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Выполнение вычислений в элементе управления NamedRange
 В следующем примере создается в <xref:Microsoft.Office.Tools.Excel.NamedRange> ячейке a1, а затем вычисляется ячейка. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

### <a name="to-run-calculations-in-a-namedrange-control"></a>Выполнение вычислений в элементе управления NamedRange

1. Создайте именованный диапазон.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. Вызовите <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> метод указанного диапазона.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Выполнение вычислений в собственном диапазоне Excel

### <a name="to-run-calculations-in-a-native-excel-range"></a>Выполнение вычислений в собственном диапазоне Excel

1. Создайте именованный диапазон.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. Вызовите <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> метод указанного диапазона.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>См. также раздел
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
