---
title: Практическое руководство. Программное Сохранение книг Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f82e469997a7d072ab04e4c5ef6df0f36a8dc9ec
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419486"
---
# <a name="how-to-programmatically-save-workbooks"></a>Практическое руководство. Программное Сохранение книг Excel
  Сохранить книгу можно несколькими способами. Можно сохранить книгу без изменения пути к файлу. Если книга не сохранялась ранее, следует сохранить книгу, указав путь. Без явного пути Microsoft Office Excel сохраняет файл в текущей папке с именем, заданным при его создании. Можно также сохранить копию книги, не изменяя открытую книгу в памяти.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Сохранение книги без изменения пути

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Сохранение книги, связанной с настройкой на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> класса `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Сохранение активной книги в надстройке VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A>, чтобы сохранить активную книгу. Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]

## <a name="save-a-workbook-with-a-new-path"></a>Сохранение книги с новым путем
 Вы можете сохранить указанную книгу в новой папке или с новым именем, указав при необходимости формат файла, пароль, режим доступа и т. д.

> [!NOTE]
> Вы можете задать <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> свойства **False** перед сохранением книги с новым путем, так как для сохранения в некоторых форматах требуется взаимодействие. Этому свойству присвоить **False** Excel будет использовать все значения по умолчанию.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Сохранение книги, связанной с настройкой на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> класса `ThisWorkbook` . Чтобы использовать следующий пример кода, запустите его из класса `ThisWorkbook`.

     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Сохранение активной книги в надстройке VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A>, чтобы сохранить активную книгу с новым путем. Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]

## <a name="save-a-copy-of-the-workbook"></a>Сохранить копию книги
 Вы можете также сохранить копию книги в файл, не изменяя открытую книгу в памяти. Это полезно, если вам нужно создать резервную копию без изменения местоположения книги.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Сохранение книги, связанной с настройкой на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> класса `ThisWorkbook` . Чтобы использовать следующий пример кода, запустите его из класса `ThisWorkbook`.

     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Сохранение активной книги в надстройке VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A>, чтобы сохранить копию активной книги. Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]

## <a name="robust-programming"></a>Отказоустойчивость
 Интерактивная отмена любых методов, которые сохраняют или копируют книгу, вызывает ошибку времени выполнения в коде. Например, если процедура вызывает <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> метод, но не отключает запросы из Excel, и ваш пользователь нажимает кнопку **отменить** при появлении Excel, возникает ошибка времени выполнения.

## <a name="see-also"></a>См. также
- [Работа с книгами](../vsto/working-with-workbooks.md)
- [Ведущий элемент книги](../vsto/workbook-host-item.md)
- [Практическое руководство. Программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)
- [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
