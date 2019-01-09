---
title: Как выполнить Программное копирование данных и форматирование между листами
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: babf55cd7728734e6ab6575c960a2b821f510154
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087871"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Как выполнить Программное копирование данных и форматирование между листами
  Данные можно скопировать из диапазона на одном листе для всех других листов в книге с помощью <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> метод. Укажите диапазон, и нужно ли выполнять копирование данных, форматирования или оба.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Этот пример требует диапазона с именем `rangeData` на листе.  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Практическое руководство. Программное добавление новых листов в книги](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Практическое руководство. Программное изменение форматирования в строках листа, содержащих выбранные ячейки](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
