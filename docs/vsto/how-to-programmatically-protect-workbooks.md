---
title: Руководство. Программная защита книг
description: Узнайте, как защитить книгу Microsoft Excel, чтобы пользователи не могли добавлять или удалять листы, а также программно снимать защиту книги.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 05587b067fb5e8365433049c7da7fd3d5949a831
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963852"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Руководство. Программная защита книг
  Можно защитить книгу Excel Microsoft Office, чтобы пользователи не могли добавлять или удалять листы, а также программно снимать защиту книги. При необходимости можно указать пароль, указать, должна ли быть защищена структура (так что пользователи не смогут перемещать листы), и указать, должна ли быть защищена Windows книги.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Защита книги не останавливает редактирование ячеек пользователями. Чтобы защитить данные, необходимо защитить листы. Дополнительные сведения см. [в разделе руководство. Программная защита листов](../vsto/how-to-programmatically-protect-worksheets.md).

 В следующих примерах кода используется переменная, которая содержит пароль, полученный от пользователя.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Защита книги, которая является частью настройки уровня документа

### <a name="to-protect-a-workbook"></a>Защита книги

1. Вызовите <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> метод книги и включите пароль. Чтобы использовать следующий пример кода, запустите его в `ThisWorkbook` классе, а не в классе листа.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>Снятие защиты с книги

1. Вызовите <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> метод, передав пароль, если он требуется. Чтобы использовать следующий пример кода, запустите его в `ThisWorkbook` классе, а не в классе листа.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Защита книги с помощью надстройки уровня приложения

### <a name="to-protect-a-workbook"></a>Защита книги

1. Вызовите <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> метод книги и включите пароль. В этом примере кода используется активная книга. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>Снятие защиты с книги

1. Вызовите <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> метод активной книги, передав пароль, если он требуется. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>См. также раздел
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Как программно защитить листы](../vsto/how-to-programmatically-protect-worksheets.md)
- [Как программно скрыть листы](../vsto/how-to-programmatically-hide-worksheets.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
