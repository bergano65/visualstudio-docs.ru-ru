---
title: 'Практическое: программное добавление и удаление примечаний на листе'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fe41fe7f6370697335fa76b468e79e61d6e1269a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673869"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Практическое: программное добавление и удаление примечаний на листе
  Вы можете добавлять и удалять комментарии в листах Microsoft Office Excel программными средствами. Комментарии можно добавлять только в отдельные ячейки, а не в диапазоны из нескольких ячеек.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Добавление и удаление комментария в проекте уровня документа  
 В следующих примерах предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `dateComment` в одной ячейке в листе с именем `Sheet1`.  
  
### <a name="to-add-a-new-comment-to-a-named-range"></a>Добавление нового комментария в именованный диапазон  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> и укажите текст примечания. Этот код следует разместить в классе `Sheet1` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>Удаление комментария из именованного диапазона  
  
1.  Проверьте наличие комментария в диапазоне и удалите его. Этот код следует разместить в классе `Sheet1` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Добавление и удаление комментария в проекте надстройки VSTO  
 В следующих примерах предполагается, что имеется элемент управления <xref:Microsoft.Office.Interop.Excel.Range> с именем `dateComment` в одной ячейке в активном листе.  
  
### <a name="to-add-a-new-comment-to-an-excel-range"></a>Добавление нового комментария в диапазон Excel  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> элемента управления <xref:Microsoft.Office.Interop.Excel.Range> и укажите текст примечания.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
### <a name="to-delete-a-comment-from-an-excel-range"></a>Удаление нового комментария из диапазона Excel  
  
1.  Проверьте наличие комментария в диапазоне и удалите его.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое: программное отображение примечаний на листе](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)  
  
  