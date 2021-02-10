---
title: Программное копирование данных и форматирования на листах
description: Узнайте, как копировать данные из диапазона на одном листе во все другие листы книги с помощью метода Филлакроссшитс.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d768eb086707af2eeddeb18a77bad1ef1f101839
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964242"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Руководство. программное копирование данных и форматирование на листах
  Данные из диапазона на одном листе можно скопировать на все другие листы книги с помощью <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> метода. Укажите диапазон, а также сведения о том, требуется ли копировать данные, форматирование или и то, и другое.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Пример
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуется диапазон с именем `rangeData` в листе.

## <a name="see-also"></a>См. также раздел
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Как программно добавлять новые листы в книги](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Руководство. Программное изменение форматирования в строках листа, содержащих выбранные ячейки](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
