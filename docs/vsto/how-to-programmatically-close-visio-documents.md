---
title: "Как: программное закрытие документов Visio | Документы Microsoft"
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
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cbb848c07828b8581a71e57fbeee411404632f31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-close-visio-documents"></a>Практическое руководство. Программное закрытие документов Visio
  С помощью метода Microsoft.Office.Interop.Visio.Document.Close можно закрыть активный документ Microsoft Office Visio.  
  
 Сведения об этом методе см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff767415.aspx) .  
  
## <a name="closing-the-active-document"></a>Закрытие активного документа  
  
#### <a name="to-close-the-active-document"></a>Закрытие активного документа  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Document.Close для закрытия активного документа.  
  
     Чтобы использовать следующий пример кода, запустите его в классе `ThisAddIn` в проекте надстройки VSTO для Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения о модели объектов Visio](../vsto/visio-object-model-overview.md)   
 [Как: программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Как: открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Как: программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  