---
title: Как выполнить Программное выполнение вычислений Excel
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 6d1a896a7c09a7ce8c84297757d31c31deb49aa6
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871706"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Как выполнить Программное выполнение вычислений Excel  
  Подобный процесс используется для вычислений в <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления или собственный объект диапазона Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="run-calculations-in-a-namedrange-control"></a>Выполнение вычислений в элементе управления NamedRange  
 В следующем примере создается <xref:Microsoft.Office.Tools.Excel.NamedRange> ячейку A1, а затем вычисляет ячейки. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .  
  
### <a name="to-run-calculations-in-a-namedrange-control"></a>Выполнение вычислений в элементе управления NamedRange  
  
1.  Создайте именованный диапазон.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]  
  
2.  Вызовите <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> метод указанного диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]  
  
## <a name="run-calculations-in-a-native-excel-range"></a>Выполнение вычислений в собственном диапазоне Excel  
  
### <a name="to-run-calculations-in-a-native-excel-range"></a>Выполнение вычислений в собственном диапазоне Excel  
  
1.  Создайте именованный диапазон.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]  
  
2.  Вызовите <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> метод указанного диапазона.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]  
  
## <a name="see-also"></a>См. также  
 [Работа с диапазонами](../vsto/working-with-ranges.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
