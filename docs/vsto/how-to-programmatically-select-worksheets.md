---
title: Практическое руководство. Программный выбор листов Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee6e5d89bea21f58c8c5b1cc59f7c7f248630742
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602654"
---
# <a name="how-to-programmatically-select-worksheets"></a>Практическое руководство. Программный выбор листов Excel
  Метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> выбирает указанный объект, который перемещает выделенный пользователем фрагмент в новый объект. Если необходимо сфокусироваться на объекте без изменения выбранного пользователем фрагмента, используйте метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Если вы хотите выбрать существующий лист в надстройке VSTO или если лист был создан во время выполнения в настройке уровня документа, то необходимо открыть это с помощью Excel <xref:Microsoft.Office.Interop.Excel.Sheets> коллекции книги Excel; в противном случае можно получить доступ к <xref:Microsoft.Office.Tools.Excel.Worksheet>непосредственно ведущего элемента.

## <a name="use-the-worksheet-host-item"></a>Использовать ведущий элемент листа
 В настройке уровня документа, добавьте следующий код, чтобы *Sheet1.vb* или *Sheet1.cs*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Выбор первого листа в книге с помощью ведущего элемента

1.  Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> типа `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Использование коллекции листов книги Excel
 Обратитесь к таблице с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> Excel.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Выбор первого листа в книге с помощью коллекции листов книги Excel

1.  Вызовите метод <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets>, чтобы выбрать первый лист активной книги.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Практическое руководство. Программная печать листов Excel](../vsto/how-to-programmatically-print-worksheets.md)
- [Практическое руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)
- [Практическое руководство. Программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)
- [Ведущий элемент листа](../vsto/worksheet-host-item.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
