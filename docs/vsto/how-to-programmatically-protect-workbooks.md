---
title: Практическое руководство. Программная Защита книг Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 12391f16e2797941cf83177aa1c83ed0dd2c0045
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644605"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Практическое руководство. Программная Защита книг Excel
  Можно защитить книгу Microsoft Office Excel, чтобы пользователи не могут быть Добавление или удаление листов и также снять защиту с книги программными средствами. При необходимости можно указать пароль, указывают ли защиты (чтобы пользователи не могли перемещать листы) структуры и укажите, хотите ли вы защиты окон книги.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Защита книги не запрещает пользователям редактировать ячейки. Для защиты данных, необходимо защитить листы. Дополнительные сведения см. в разделе [Как Программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md).

 В следующих примерах кода использовать переменную, которая содержит пароль, полученный от пользователя.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Защита книги, которая является частью настройки уровня документа

### <a name="to-protect-a-workbook"></a>Чтобы защитить книгу

1.  Вызовите <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> метод книги и включите пароль. Чтобы использовать в следующем примере кода, запустите его `ThisWorkbook` класса, а не в классе листа.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>Чтобы снять защиту с книги

1.  Вызовите <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> метод, передав пароль, если это необходимо. Чтобы использовать в следующем примере кода, запустите его `ThisWorkbook` класса, а не в классе листа.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Защита книги с помощью надстройки уровня приложения

### <a name="to-protect-a-workbook"></a>Чтобы защитить книгу

1.  Вызовите <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> метод книги и включите пароль. Данный пример кода использует активную книгу. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>Чтобы снять защиту с книги

1.  Вызовите <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> метод активной книги, передав пароль, если это необходимо. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>См. также
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Практическое руководство. Программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)
- [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
