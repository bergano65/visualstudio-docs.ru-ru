---
title: 'Как: программным путем список недавно использовавшихся файлов книг Excel | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c2d9c333b6d96329abec3fd52ecaa5da1cf97c74
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Практическое руководство. Программный вывод списка последних использовавшихся файлов книг Excel
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> Свойство возвращает коллекцию, содержащую имена всех файлов, которые отображаются в списке недавно использовавшихся файлов Microsoft Office Excel. Длина списка зависит от числа файлов, которые пользователь выбрал для сохранения. Результаты могут отображаться в диапазоне.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Чтобы вывести список недавно использовавшихся книг в объекте range  
  
1.  Циклическую обработку списка недавно открывавшихся файлов и отображаемые имена в ячейки <xref:Microsoft.Office.Interop.Excel.Range> объекта.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  