---
title: Практическое руководство. Программное удаление листов из книг
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ecc39e72a336c390c85f1caf2c80c6643acbb61
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412538"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Практическое руководство. Программное удаление листов из книг
  В книге можно удалить любой лист. Для удаления листа используйте ведущий элемент листа или получите доступ к листу с помощью коллекции листов книги.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Использовать ведущий элемент листа
 Если лист был добавлен в настройку на уровне документа во время разработки, для удаления указанного листа используйте метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>. Следующий код удаляет лист из книги с помощью прямой ссылки на ведущий элемент листа.

> [!IMPORTANT]
> Этот код выполняется только в тех проектах, которые создаются с помощью любого из следующих шаблонов проекта:
>
> - Книга Excel 2013
> - Шаблон Excel 2013
> - Книга Excel 2010
> - Шаблон Excel 2010
>
>   Если вы хотите выполнить эту задачу в проекте любого другого типа, необходимо добавить ссылку на **Microsoft.Office.Interop.Excel** сборки, а затем использовать классы из этой сборки для открытия книги и удалить лист. Дополнительные сведения см. в разделе [Как Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Удаление листа с помощью ведущего элемента листа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> типа `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Использование коллекции листов книги Excel
 Обращайтесь к листам с помощью коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> для Microsoft Office Excel в следующих случаях.

- Требуется удалить лист в надстройке VSTO.

- Лист, который требуется удалить, был создан во время выполнения в настройке на уровне документа.

  Следующий код удаляет лист из книги путем ссылки на лист через номер индекса **листы** коллекции. В этом коде предполагается, что новый лист был создан программным образом.

> [!IMPORTANT]
> Если вы хотите выполнить эту задачу в проекте любого другого типа, необходимо добавить ссылку на **Microsoft.Office.Interop.Excel** сборки, а затем использовать классы из этой сборки для открытия книги и удалить лист. Дополнительные сведения см. в разделе [Как Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Удаление листа с помощью коллекции листов книги Excel

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets>.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)
- [Практическое руководство. Программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Практическое руководство. Программный выбор листов Excel](../vsto/how-to-programmatically-select-worksheets.md)
- [Практическое руководство. Программное добавление новых листов в книги](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Ведущий элемент листа](../vsto/worksheet-host-item.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
