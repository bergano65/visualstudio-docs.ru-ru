---
title: Как выполнить Программный вывод списка недавно использовавшихся файлов книг
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6451aa5427799f0905d19b7b90e87f8cca3d0bbd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863192"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Как выполнить Программный вывод списка недавно использовавшихся файлов книг
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> Свойство возвращает коллекцию, содержащую имена всех файлов, которые отображаются в списке недавно использовавшихся файлов Microsoft Office Excel. Длина списка зависит от числа файлов, которые пользователь выбрал для сохранения. Можно отобразить результаты в диапазон.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Чтобы вывести список недавно использовавшихся книг объекта range  
  
1.  Циклический перебор списка последних файлов и отображения названий в ячейки <xref:Microsoft.Office.Interop.Excel.Range> объекта.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
