---
title: Как программно ссылаться на диапазоны листов в коде
description: Узнайте, как можно использовать Visual Studio для программного обозначения содержимого элемента управления NamedRange или собственного объекта диапазона Excel в листе Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 89a4b7c594f942405777145f94ed0a3503e9b16f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963761"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Как программно ссылаться на диапазоны листов в коде
  Аналогичный процесс используется для ссылки на содержимое <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления или собственного объекта диапазона Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange
 В следующем примере добавляется <xref:Microsoft.Office.Tools.Excel.NamedRange> в лист, а затем текст добавляется в ячейку в диапазоне.

### <a name="to-refer-to-a-namedrange-control"></a>Ссылка на элемент управления NamedRange

1. Присвойте строку <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> свойству <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Использовать собственные диапазоны Excel
 В следующем примере на лист добавляется собственный диапазон Excel, а затем в ячейку в диапазоне добавляется текст.

### <a name="to-refer-to-a-native-range-object"></a>Ссылка на объект собственного диапазона

1. Присвойте строку <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> свойству диапазона.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>См. также раздел
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Руководство. Программная проверка орфографии на листах](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Руководство. программное автоматическое заполнение диапазонов путем постепенного изменения данных](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Руководство. Программный поиск текста в диапазонах листа](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
