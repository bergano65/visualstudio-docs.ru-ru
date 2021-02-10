---
title: Копирование и вставка фигур в документ Visio программным способом
description: Узнайте, как программно копировать фигуры на одной странице документа и вставлять их в новую страницу в одном документе.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 90a065ec98da440af6e52a191e11f4371575c2d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964229"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Руководство. программное копирование и вставка фигур в документ Visio
  Вы можете программными средствами копировать фигуры на одной странице документа и вставлять их в новую страницу того же документа. Можно вставлять их в расположение по умолчанию (центр активного окна) или в то же расположение, в котором они находились на исходной странице.

## <a name="copy-and-paste-shapes"></a>Копирование и вставка фигур
 Подробные сведения об объектной модели см. в справочной документации VBA для методов [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)и [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) и для флага [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Копирование фигур в центр другой страницы

- В следующем примере показано, как копировать фигуры с первой страницы и вставлять их в центр второй страницы.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Копирование и вставка фигур с одинаковыми позициями
 Подробные сведения об объектной модели см. в справочной документации VBA для методов [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)и [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) и для флага [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .

 Если необходимо управлять форматом вставленных данных и (необязательно) установить ссылку на исходный файл (например, в Microsoft Office документе Word), используйте метод PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Копирование фигур и их расположений на другую страницу

- В следующем примере показано, как копировать фигуры с первой страницы и вставлять их в те же места на второй странице.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>См. также раздел
- [Решения Visio](../vsto/visio-solutions.md)
- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)
- [Руководство. Программное добавление фигур в документ Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
