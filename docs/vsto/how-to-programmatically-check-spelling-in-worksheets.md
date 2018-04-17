---
title: 'Как: Программная проверка орфографии на листах | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 874a85063dae34f0fd650149583bade40ca60d29
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Практическое руководство. Программная проверка орфографии на листах
  Вы можете программными средствами проверять орфографию слов в листе. Диалоговое окно **Орфография** автоматически появляется при появлении в листе слов с ошибками.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Проверка орфографии в листе в настройке уровня документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> листа.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]  
  
### <a name="to-check-spelling-in-a-worksheet-in-an-vsto-add-in"></a>Проверка орфографии в листе в надстройке VSTO  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> активного листа.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: программное выполнение вычислений Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  