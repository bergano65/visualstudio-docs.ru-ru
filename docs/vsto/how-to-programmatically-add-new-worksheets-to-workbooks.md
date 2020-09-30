---
title: Как программно добавлять новые листы в книги
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 3c014d8ea1701dde4e83e6849cce337656579f5d
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585409"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Как программно добавлять новые листы в книги
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

     Новый лист — это собственный объект <xref:Microsoft.Office.Interop.Excel.Worksheet> , а не ведущий элемент. Также можно создать ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> из собственного объекта <xref:Microsoft.Office.Interop.Excel.Worksheet> . Дополнительные сведения см. в разделе [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Как программно выбрать листы](../vsto/how-to-programmatically-select-worksheets.md)
- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
