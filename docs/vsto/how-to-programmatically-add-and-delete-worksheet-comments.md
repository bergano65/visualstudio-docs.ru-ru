---
title: Руководство. Программное добавление и удаление комментариев на листе
description: Сведения о программном добавлении и удалении комментариев в Microsoft Office листах Excel. Комментарии можно добавлять только в отдельные ячейки, а не в диапазоны с несколькими ячейками.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ec70c03dfdce05c7445762e2cfd452f3fdf90775
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904486"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Руководство. Программное добавление и удаление комментариев на листе
  Вы можете добавлять и удалять комментарии в листах Microsoft Office Excel программными средствами. Комментарии можно добавлять только в отдельные ячейки, а не в диапазоны из нескольких ячеек.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Добавление и удаление комментария в проекте уровня документа
 В следующих примерах предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `dateComment` в одной ячейке в листе с именем `Sheet1`.

### <a name="to-add-a-new-comment-to-a-named-range"></a>Добавление нового комментария в именованный диапазон

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> и укажите текст примечания. Этот код следует разместить в классе `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]

#### <a name="to-delete-a-comment-from-a-named-range"></a>Удаление комментария из именованного диапазона

1. Проверьте наличие комментария в диапазоне и удалите его. Этот код следует разместить в классе `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Добавление и удаление комментария в проекте надстройки VSTO
 В следующих примерах предполагается, что имеется элемент управления <xref:Microsoft.Office.Interop.Excel.Range> с именем `dateComment` в одной ячейке в активном листе.

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Добавление нового комментария в диапазон Excel

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> элемента управления <xref:Microsoft.Office.Interop.Excel.Range> и укажите текст примечания.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]

### <a name="to-delete-a-comment-from-an-excel-range"></a>Удаление нового комментария из диапазона Excel

1. Проверьте наличие комментария в диапазоне и удалите его.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]

## <a name="see-also"></a>См. также раздел
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Как программно отображать комментарии на листе](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
