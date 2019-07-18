---
title: Практическое руководство. Программная Защита листов Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d6fb66684bd51c75e655bc2403cb6a9fb5846a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438818"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Практическое руководство. Программная Защита листов Excel
  Возможность защиты в Microsoft Office Excel помогает предотвратить изменение объектов на листе пользователями и кодом. По умолчанию все ячейки заблокированы после включения защиты.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В настройках на уровне документа можно защитить листы с помощью конструктора Excel. Лист также можно защитить программными средствами во время выполнения в проекте любого типа.

> [!NOTE]
> Невозможно добавлять элементы управления Windows Forms в защищенные области листа.

## <a name="use-the-designer"></a>С помощью конструктора

### <a name="to-protect-a-worksheet-in-the-designer"></a>Защита листа в конструкторе

1. В **изменения** группе **проверки** щелкните **защитить лист**.

    **Защитить лист** откроется диалоговое окно. Вы можете задать пароль и при необходимости указать определенные действия, которые пользователям разрешено выполнять с листом, например форматирование ячеек или вставка строк.

   Также можно разрешить пользователям редактировать определенные диапазоны защищенных рабочих листов.

### <a name="to-allow-editing-in-specific-ranges"></a>Включение редактирования в определенных диапазонах

1. В **изменения** группе **проверки** щелкните **разрешить пользователям изменять диапазоны**.

     **Разрешить пользователям изменять диапазоны** откроется диалоговое окно. Можно указать диапазоны, которые разблокируются с помощью пароля, и пользователей, которым разрешено редактировать диапазоны без пароля.

## <a name="use-code-at-runtime"></a>Используйте код во время выполнения
 Следующий код задает пароль (с помощью переменной getPasswordFromUser, которая содержит пароль, полученный от пользователя) и разрешает только сортировку.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Защита листа с помощью кода в настройке на уровне документа

1. Вызовите метод <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> листа. В этом примере предполагается, что вы работаете с листом `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Защита листа с помощью кода в надстройке VSTO

1. Вызовите метод <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> активного листа.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Практическое руководство. Программное снятие защиты с листов](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Практическое руководство. Программная Защита книг Excel](../vsto/how-to-programmatically-protect-workbooks.md)
- [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)
- [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)
- [Ведущий элемент листа](../vsto/worksheet-host-item.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
