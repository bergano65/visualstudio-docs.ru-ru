---
title: 'Как: программное закрытие документов Visio | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 314d8e5bfd40e1e45d4795a6e4523db19124741a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
  