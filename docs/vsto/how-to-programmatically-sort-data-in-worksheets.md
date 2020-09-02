---
title: Руководство. Программная сортировка данных на листах
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 08fa461dc55bf42857e21a5419cab6a0ff147173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546982"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Руководство. Программная сортировка данных на листах
  Вы можете сортировать данные, содержащиеся в списках и диапазонах листа во время выполнения. Следующий код сортирует диапазон из нескольких столбцов с именем `Fruits` по данным в первом столбце, а затем по данным во втором столбце.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Сортировка данных в настройке на уровне документа

### <a name="to-sort-data-in-a-namedrange-control"></a>Сортировка данных в элементе управления NamedRange

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>. В следующем примере на листе должен находиться элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `Fruits`. Этот код следует разместить в классе листа, а не в классе `ThisWorkbook` .

    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]

   Поместите следующий код в *Лист1. vb* или *Sheet1.CS* для сортировки данных в <xref:Microsoft.Office.Tools.Excel.ListObject> элементе управления. В коде предполагается, что на листе с именем `Sheet1` есть элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> с именем `fruitList`.

### <a name="to-sort-data-in-a-listobject-control"></a>Сортировка данных в элементе управления ListObject

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> свойства <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> элемента управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.ListObject>.

     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]

## <a name="sort-data-in-a-vsto-add-in"></a>Сортировка данных в надстройке VSTO

### <a name="to-sort-data-in-a-native-range"></a>Сортировка данных в собственном диапазоне

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> неуправляемого элемента управления <xref:Microsoft.Office.Interop.Excel.Range> Excel. В следующем примере на листе должен находиться неуправляемый элемент управления Excel с именем `Fruits`.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]

### <a name="to-sort-data-in-a-listobject-control"></a>Сортировка данных в элементе управления ListObject

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> свойства <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> неуправляемого элемента управления <xref:Microsoft.Office.Interop.Excel.ListObject> Excel. В следующем примере предполагается, что на активном листе есть неуправляемый элемент управления <xref:Microsoft.Office.Interop.Excel.ListObject> Excel с именем `fruitList`.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]

## <a name="see-also"></a>См. также раздел
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Руководство. программное автоматическое заполнение диапазонов путем постепенного изменения данных](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Как программно ссылаться на диапазоны листов в коде](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [ListObject - элемент управления](../vsto/listobject-control.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
