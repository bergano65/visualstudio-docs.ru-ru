---
title: Как программно выбрать листы
description: Используйте Visual Studio для программного выбора листов Microsoft Excel с ведущим элементом листа или коллекцией листов книги Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a58c4cc53597714eb65010c2fdbb423dd20a35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899390"
---
# <a name="how-to-programmatically-select-worksheets"></a>Как программно выбрать листы
  Метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> выбирает указанный объект, который перемещает выделенный пользователем фрагмент в новый объект. Если необходимо сфокусироваться на объекте без изменения выбранного пользователем фрагмента, используйте метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Если вы хотите выбрать существующий лист в надстройке VSTO или если лист был создан во время выполнения в настройке на уровне документа, необходимо получить доступ к нему с помощью <xref:Microsoft.Office.Interop.Excel.Sheets> коллекции Excel книги Excel. в противном случае можно напрямую получить доступ к <xref:Microsoft.Office.Tools.Excel.Worksheet> ведущему элементу.

## <a name="use-the-worksheet-host-item"></a>Использование ведущего элемента листа
 В настройке на уровне документа добавьте следующий код в *Лист1. vb* или *Sheet1.CS*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Выбор первого листа в книге с помощью ведущего элемента

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> типа `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Использование коллекции листов книги Excel
 Обратитесь к таблице с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> Excel.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Выбор первого листа в книге с помощью коллекции листов книги Excel

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets>, чтобы выбрать первый лист активной книги.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>См. также раздел
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Как программно печатать листы](../vsto/how-to-programmatically-print-worksheets.md)
- [Руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Как программно скрыть листы](../vsto/how-to-programmatically-hide-worksheets.md)
- [Как программно защитить листы](../vsto/how-to-programmatically-protect-worksheets.md)
- [Ведущий элемент листа](../vsto/worksheet-host-item.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
