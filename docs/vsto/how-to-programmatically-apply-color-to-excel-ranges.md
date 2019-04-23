---
title: Практическое руководство. Программное применение цвета к диапазонам Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 56ecbfcdaf22132f63df1ecf5eadba97dee426af
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078087"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Практическое руководство. Программное применение цвета к диапазонам Excel
  Чтобы применить цвет для текста в диапазон ячеек, используйте <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления или собственный объект диапазона Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Использование элемента управления NamedRange
 Этот пример предназначен для настроек уровня документа.

### <a name="to-apply-color-to-a-namedrange-control"></a>Чтобы применить цвет к элементу управления NamedRange

1. Создание <xref:Microsoft.Office.Tools.Excel.NamedRange> управления ячейку A1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Задайте цвет текста в <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Использование собственного диапазонах Excel

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Чтобы применить цвет к собственный объект диапазона Excel

1. Создайте диапазон в ячейку A1, а затем задайте цвет текста.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>См. также
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Практическое руководство. Ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
