---
title: Практическое руководство. Программное открытие книг Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: facf3cbeb6635324e74244983fcb33138ad64cfe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107896"
---
# <a name="how-to-programmatically-open-workbooks"></a>Практическое руководство. Программное открытие книг Excel
  <xref:Microsoft.Office.Interop.Excel.Workbooks> Коллекции в Microsoft Office Excel позволяет работать со всеми открытыми книгами и открывать книги.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Чтобы открыть существующую книгу

1. Используйте <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> метод <xref:Microsoft.Office.Interop.Excel.Workbooks> коллекции, передавая путь к книге.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Книга с именем `YourWorkbook.xls` должен существовать в каталог с именем `Test` на диске C.

## <a name="see-also"></a>См. также
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Практическое руководство. Программное открытие текстовых файлов как книг Excel](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Практическое руководство. Программное создание книг Excel](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Практическое руководство. Программное Сохранение книг Excel](../vsto/how-to-programmatically-save-workbooks.md)
- [Практическое руководство. Программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
