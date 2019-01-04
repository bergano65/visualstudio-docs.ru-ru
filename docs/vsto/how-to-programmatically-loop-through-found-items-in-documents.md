---
title: Как выполнить Программный перебор найденных элементов в документах
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2a04cf49d1414ae1cedf2d157237e53883182eb7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961846"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Как выполнить Программный перебор найденных элементов в документах
  Класс <xref:Microsoft.Office.Interop.Word.Find> имеет свойство <xref:Microsoft.Office.Interop.Word.Find.Found%2A> , которое возвращает **true** когда найден искомый элемент. Вы циклически просматривать все экземпляры, найденные в <xref:Microsoft.Office.Interop.Word.Range> , с помощью метода <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-loop-through-found-items"></a>Циклический перебор найденных элементов  
  
1. Объявите объект <xref:Microsoft.Office.Interop.Word.Range> .  
  
    Следующий пример кода можно использовать в настройке на уровне документа.  
  
    [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]  
  
    Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]  
  
2. Используйте свойство <xref:Microsoft.Office.Interop.Word.Find.Found%2A> в цикле, чтобы найти все вхождения строки в документе, и увеличивайте переменную integer на 1 каждый раз, когда она найдена.  
  
    [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
    [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]  
  
3. Отобразите число раз, которое строка была найдена, в окне сообщения.  
  
    [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
    [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]  
  
   В следующем примере показан полный метод.  
  
## <a name="document-level-customization-example"></a>Пример настройки на уровне документа  
  
### <a name="to-loop-through-items-in-a-document-level-customization"></a>Циклический перебор элементов в настройке уровня документа  
  
1.  В следующем примере показан полный код для настройки на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]  
  
## <a name="vsto-add-in-example"></a>Пример надстройки VSTO  
  
### <a name="to-loop-through-items-in-a-vsto-add-in"></a>Циклический перебор элементов в надстройке VSTO  
  
1.  В следующем примере показан полный код для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Программным способом поиска и замены rext в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Практическое руководство. Программное задание параметров поиска в Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое руководство. Программное восстановление выделения после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
