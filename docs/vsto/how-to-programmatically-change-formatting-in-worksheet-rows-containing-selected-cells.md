---
title: Изменение форматов в строках, содержащих выбранные ячейки, с помощью кода
description: Узнайте, как можно изменить шрифт всей строки, содержащей выбранную ячейку, чтобы текст был полужирным.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio]
- formatting [Office development in Visual Studio]
- worksheets, changing formatting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 62b9f94bfa423b149fef6abb984a03536d0e3d8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875319"
---
# <a name="how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells"></a>Руководство. Программное изменение форматирования в строках листа, содержащих выбранные ячейки
  Можно изменить шрифт всей строки, содержащей выбранную ячейку, чтобы текст был полужирным.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-make-the-current-row-bold-and-the-previously-bolded-row-normal"></a>Чтобы сделать текущую строку полужирной и выделенную ранее строку с полужирным шрифтом обычной

1. Объявите статическую переменную для наблюдения за ранее выбранной строкой.

    [!code-csharp[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#37)]
    [!code-vb[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#37)]

2. Получение ссылки на текущую ячейку с помощью <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> Свойства.

    [!code-csharp[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#38)]
    [!code-vb[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#38)]

3. Применение стиля к текущей строке полужирным шрифтом с помощью <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> свойства активной ячейки.

    [!code-csharp[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#39)]
    [!code-vb[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#39)]

4. Убедитесь, что текущее значение `previousRow` не равно 0. 0 (ноль) указывает, что этот код впервые используется в этом коде.

    [!code-csharp[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#40)]
    [!code-vb[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#40)]

5. Убедитесь, что текущая строка отличается от предыдущей строки.

    [!code-csharp[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#41)]
    [!code-vb[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#41)]

6. Получите ссылку на диапазон, представляющий ранее выбранную строку, и задайте для этой строки значение не полужирным.

    [!code-csharp[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#42)]
    [!code-vb[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#42)]

7. Сохраните текущую строку, чтобы она могла стать предыдущей строкой на следующем этапе.

    [!code-csharp[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#43)]
    [!code-vb[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#43)]

   В следующем примере показан полный метод.

## <a name="example"></a>Пример
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#36)]

## <a name="see-also"></a>См. также раздел
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Руководство. программное копирование данных и форматирование на листах](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
