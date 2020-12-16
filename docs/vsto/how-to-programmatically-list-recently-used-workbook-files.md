---
title: Руководство. программный список недавно использованных файлов книг
description: Узнайте, как программным способом получить список недавно использовавшихся файлов книг Microsoft Excel с помощью Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: bbcad553ade6234d3a688c8f718a0dd6e6cda509
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525632"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Руководство. программный список недавно использованных файлов книг
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>Свойство возвращает коллекцию, содержащую имена всех файлов, которые отображаются в списке недавно использовавшихся файлов Microsoft Office Excel. Длина списка зависит от числа файлов, которые пользователь выбрал для удержания. Результаты можно отобразить в диапазоне.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Вывод списка недавно использовавшихся книг в объекте Range

1. Пройдите по списку последних файлов и отобразите имена в ячейках относительно <xref:Microsoft.Office.Interop.Excel.Range> объекта.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>См. также раздел
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Элемент управления NamedRange](../vsto/namedrange-control.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
