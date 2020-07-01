---
title: Как программно снять защиту с листов
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 72448f9d1e5c24c917459b8c2c59e317190e0a11
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519877"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Как программно снять защиту с листов
  Защиту с листа Microsoft Office Excel можно снять программными средствами.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 В приведенном ниже примере используется переменная `getPasswordFromUser`, которая содержит пароль, полученный от пользователя.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Снятие защиты с листа в настройке на уровне документа

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A>При необходимости вызовите метод листа и передайте пароль. В этом примере предполагается, что вы работаете с листом `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Снятие защиты листа в надстройке VSTO

1. Вызовите <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> метод активного листа и передайте пароль при необходимости.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Как программно защитить листы](../vsto/how-to-programmatically-protect-worksheets.md)
- [Руководство. Программная защита книг](../vsto/how-to-programmatically-protect-workbooks.md)
- [Как программно скрыть листы](../vsto/how-to-programmatically-hide-worksheets.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
