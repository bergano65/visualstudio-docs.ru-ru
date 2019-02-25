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
ms.openlocfilehash: f9d8ab4be67ffd84406869c956f9046a53d6ec79
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611897"
---
# <a name="how-to-programmatically-open-workbooks"></a>Практическое руководство. Программное открытие книг Excel
  <xref:Microsoft.Office.Interop.Excel.Workbooks> Коллекции в Microsoft Office Excel позволяет работать со всеми открытыми книгами и открывать книги.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Чтобы открыть существующую книгу

1.  Используйте <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> метод <xref:Microsoft.Office.Interop.Excel.Workbooks> коллекции, передавая путь к книге.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

-   Книга с именем `YourWorkbook.xls` должен существовать в каталог с именем `Test` на диске C.

## <a name="see-also"></a>См. также
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Практическое руководство. Программное открытие текстовых файлов как книг Excel](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Практическое руководство. Программное создание книг Excel](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Практическое руководство. Программное Сохранение книг Excel](../vsto/how-to-programmatically-save-workbooks.md)
- [Практическое руководство. Программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
