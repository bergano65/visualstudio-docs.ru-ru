---
title: 'Как: программное копирование и вставка фигур в документ Visio | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 488cda5519a211754498b50a88995de64a8ed366
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Практическое руководство. Программное копирование и вставка фигур в документе Visio
  Вы можете программными средствами копировать фигуры на одной странице документа и вставлять их в новую страницу того же документа. Можно вставлять их в расположение по умолчанию (центр активного окна) или в то же расположение, в котором они находились на исходной странице.  
  
## <a name="copying-and-pasting-shapes"></a>Копирование и вставка фигур  
 Подробные сведения об объектной модели см. в справочной документации VBA для методов [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)и [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) и для флага [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
#### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Копирование фигур в центр другой страницы  
  
-   В следующем примере показано, как копировать фигуры с первой страницы и вставлять их в центр второй страницы.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]  
  
## <a name="copying-and-pasting-shapes-with-the-same-positions"></a>Копирование и вставка фигур с сохранением расположения  
 Подробные сведения об объектной модели см. в справочной документации VBA для методов [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](https://msdn.microsoft.com/library/office/ff765757.aspx), [Microsoft.Office.Interop.Visio.Shape.DrawOval](https://msdn.microsoft.com/library/office/ff767121.aspx), [Microsoft.Office.Interop.Visio.Shape.Copy](https://msdn.microsoft.com/library/office/ff765638.aspx)и [Microsoft.Office.Interop.Visio.Shape.Paste](https://msdn.microsoft.com/library/office/ff768361.aspx) и для флага [Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](https://msdn.microsoft.com/library/office/ff765187.aspx) .  
  
 Если необходимо управлять форматом вставляемых данных и (Дополнительно) установить ссылку на исходный файл (например, документ Microsoft Office Word), используйте метод PasteSpecial.  
  
#### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Копирование фигур и их расположений на другую страницу  
  
-   В следующем примере показано, как копировать фигуры с первой страницы и вставлять их в те же места на второй странице.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения о модели объектов Visio](../vsto/visio-object-model-overview.md)   
 [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)   
 [Практическое руководство. Программное добавление фигур в документ Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)  
  
  