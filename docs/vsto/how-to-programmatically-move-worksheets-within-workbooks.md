---
title: Практическое руководство. Программное перемещение листов в книгах
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20ca03e8d7a3c574501d879cf9949d26fd7ba3a3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56595741"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Практическое руководство. Программное перемещение листов в книгах
  Вы можете программными средствами изменять положение листов относительно других листов в книге. Если не указать расположение для перемещаемого листа, Excel создает для него новую книгу.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Перемещение листа в настройке уровня документа

1.  Назначьте переменной общее число листов в книге и затем переместите первый лист, чтобы он стал последним.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Перемещение листа в надстройке VSTO

1.  Назначьте переменной общее число листов в книге и затем переместите первый лист, чтобы он стал последним.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>См. также
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)
- [Практическое руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Практическое руководство. Программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
