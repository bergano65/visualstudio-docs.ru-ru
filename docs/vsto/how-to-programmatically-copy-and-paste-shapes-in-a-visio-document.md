---
title: "Как: программное копирование и вставка фигур в документ Visio | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
ms.assetid: 762d95cf-2d5c-4dea-988b-8f4da88fa1f1
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5b1f3a402d4f39b3648bbcf577ff48a130625b50
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
  