---
title: Руководство. Программный поиск текста в диапазонах листа
description: Узнайте, как можно использовать Visual Studio для программного поиска текста в диапазонах листов Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3cf3894a2fb6d34678786686fe3c229d2e16a9a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877893"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Руководство. Программный поиск текста в диапазонах листа
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>Метод <xref:Microsoft.Office.Interop.Excel.Range> объекта позволяет искать текст в диапазоне. Этот текст также может быть любой строкой ошибок, которая может присутствовать в ячейке листа, например `#NULL!` или `#VALUE!` . Дополнительные сведения о строках ошибок см. в разделе [значения ошибок ячеек](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В следующем примере выполняется поиск в диапазоне с именем `Fruits` и изменяется шрифт для ячеек, содержащих слово «яблоки». Эта процедура также использует <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> метод, который использует ранее заданные параметры поиска для повторения поиска. Вы указываете ячейку, после которой будет производиться поиск, и <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> метод обрабатывает остальные.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>Поиск метода выполняет обратную передачу к началу диапазона поиска после того, как он достиг конца диапазона. Код должен гарантировать, что поиск не будет перетекать в бесконечный цикл. В примере процедуры показан один из способов обработки этого с помощью <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> Свойства.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Поиск текста в диапазоне на листе

1. Объявите переменные для отслеживания всего диапазона, первого найденного диапазона и текущего найденного диапазона.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. Выполните поиск первого совпадения, указав все параметры, кроме ячейки для поиска.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. Продолжайте поиск, пока есть совпадения.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. Сравните первый найденный диапазон ( `firstFind` ) с **Nothing**. Если `firstFind` параметр не содержит значения, код сохраняет содержимое вне найденного диапазона ( `currentFind` ).

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. Выйти из цикла, если адрес найденного диапазона совпадает с адресом первого найденного диапазона.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. Задайте внешний вид найденного диапазона.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. Выполните еще один поиск.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   В следующем примере показан полный метод.

## <a name="example"></a>Пример
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>См. также раздел
- [Работа с диапазонами](../vsto/working-with-ranges.md)
- [Руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Как программно ссылаться на диапазоны листов в коде](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
