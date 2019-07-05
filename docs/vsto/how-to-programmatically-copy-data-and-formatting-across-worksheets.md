---
title: Копирование данных и форматирование между листами программным способом
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b90704d6d9fe555920fb042939079bd53884cfbe
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402209"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Практическое руководство. Программное копирование данных и форматирование между листами
  Данные можно скопировать из диапазона на одном листе для всех других листов в книге с помощью <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> метод. Укажите диапазон, и нужно ли выполнять копирование данных, форматирования или оба.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Компиляция кода
 Этот пример требует диапазона с именем `rangeData` на листе.

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Практическое руководство. Программное добавление новых листов в книги](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Практическое руководство. Программное изменение форматирования в строках листа, содержащих выбранные ячейки](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
