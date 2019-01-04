---
title: Как выполнить Программное копирование и вставка фигур в документ Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a7994d605d22b38b64219a384e5afb0b002ff755
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856492"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Как выполнить Программное копирование и вставка фигур в документ Visio
  Вы можете программными средствами копировать фигуры на одной странице документа и вставлять их в новую страницу того же документа. Можно вставлять их в расположение по умолчанию (центр активного окна) или в то же расположение, в котором они находились на исходной странице.  
  
## <a name="copy-and-paste-shapes"></a>Копирование и вставка фигур  
 Подробные сведения об объектной модели см. в справочной документации VBA для методов [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)и [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) и для флага [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .  
  
### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Копирование фигур в центр другой страницы  
  
-   В следующем примере показано, как копировать фигуры с первой страницы и вставлять их в центр второй страницы.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Копирование и вставка фигур с сохранением расположения  
 Подробные сведения об объектной модели см. в справочной документации VBA для методов [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy)и [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) и для флага [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .  
  
 Если вам нужно управлять форматом вставляемых данных и (при необходимости) установления связи с исходным файлом (например, документ Microsoft Office Word), используйте метод PasteSpecial.  
  
### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Копирование фигур и их расположений на другую страницу  
  
-   В следующем примере показано, как копировать фигуры с первой страницы и вставлять их в те же места на второй странице.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Обзор объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)   
 [Практическое руководство. Программное добавление фигур в документ Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
