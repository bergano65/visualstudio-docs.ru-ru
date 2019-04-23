---
title: Практическое руководство. Программное добавление новых листов в книги
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1b45196fa70328809aa5da3a1f56ea57fce2085
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087356"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Практическое руководство. Программное добавление новых листов в книги
  Можно программно создать лист и затем добавить лист в коллекцию листов в книге.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Добавление нового листа в книгу в настройке на уровне документа

1. Используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> .

     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]

     Новый лист — это собственный объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , а не ведущий элемент. Если вы хотите добавить ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> , следует добавить лист во время разработки.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Добавление нового листа к книге в надстройке VSTO

1. Используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> коллекции <xref:Microsoft.Office.Interop.Excel.Sheets> .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]

     Новый лист — это собственный объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , а не ведущий элемент. Также можно создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> из собственного объекта <xref:Microsoft.Office.Interop.Excel.Worksheet> . Для получения дополнительной информации см. [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
- [Практическое руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Практическое руководство. Программный выбор листов Excel](../vsto/how-to-programmatically-select-worksheets.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
