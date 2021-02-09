---
title: Хранение & получение значений дат в диапазонах Excel программными средствами
description: Узнайте, как использовать Visual Studio для программного хранения и извлечения значений дат в диапазонах Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 892f8db0a6cbeee485c8139c2d6e4614f17c1cc2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899404"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Как программно сохранять и извлекать значения дат в диапазонах Excel
  Можно сохранять и извлекать значения в <xref:Microsoft.Office.Tools.Excel.NamedRange> элементе управления или в собственном объекте Excel Range.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Если вы храните значение даты, которое попадает в диапазон или после 1/1/1900 в диапазоне с помощью средств разработки Office в Visual Studio, оно сохраняется в формате OLE Automation (OA). <xref:System.DateTime.FromOADate%2A>Для получения значений дат OLE-автоматизации (OA) необходимо использовать метод. Если дата более ранняя, чем 1/1/1900, она сохраняется в виде строки.

> [!NOTE]
> Даты Excel отличаются от дат OLE Automation на первые два месяца 1900. Существуют также различия, если установлен параметр **системы даты 1904** . Приведенные ниже примеры кода не устраняют эти различия.

## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange

- Этот пример предназначен для настроек на уровне документа. Следующий код должен быть помещен в класс листа, а не в `ThisWorkbook` класс.

### <a name="to-store-a-date-value-in-a-named-range"></a>Сохранение значения даты в именованном диапазоне

1. Создание <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления в ячейке **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. Установите сегодняшнюю дату в качестве значения параметра `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Получение значения даты из именованного диапазона

1. Получите значение даты из `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>Использовать собственные диапазоны Excel

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Сохранение значения даты в собственном объекте Excel Range

1. Создайте объект <xref:Microsoft.Office.Interop.Excel.Range> , представляющий ячейку **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. Установите сегодняшнюю дату в качестве значения параметра `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Получение значения даты из собственного объекта диапазона Excel

1. Получите значение даты из `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>См. также раздел
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Как программно ссылаться на диапазоны листов в коде](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Как добавить элементы управления NamedRange в листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
