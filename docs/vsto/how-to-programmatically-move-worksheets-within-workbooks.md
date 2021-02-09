---
title: Руководство. Программное перемещение листов в книгах
description: Узнайте, как программным способом изменить расположение листов относительно других листов в книге Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 427f3f47e141d9c3ae17bab4b253389c68d4dc1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888788"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Руководство. Программное перемещение листов в книгах
  Вы можете программными средствами изменять положение листов относительно других листов в книге. Если не указать расположение для перемещаемого листа, Excel создает для него новую книгу.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Перемещение листа в настройке уровня документа

1. Назначьте переменной общее число листов в книге и затем переместите первый лист, чтобы он стал последним.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Перемещение листа в надстройке VSTO

1. Назначьте переменной общее число листов в книге и затем переместите первый лист, чтобы он стал последним.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>См. также раздел
- [Работа с листами](../vsto/working-with-worksheets.md)
- [Как программно скрыть листы](../vsto/how-to-programmatically-hide-worksheets.md)
- [Руководство. Программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Как программно защитить листы](../vsto/how-to-programmatically-protect-worksheets.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
