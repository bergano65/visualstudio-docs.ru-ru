---
title: Как выполнить Программное восстановление выделения после поиска
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ae27f4e24ac367741bcdf2dfa2bae8598c6c7d99
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865613"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Как выполнить Программное восстановление выделения после поиска
  Поиск и замена текста в документе, может потребоваться восстановление выделения пользователя после завершения поиска.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Код в примере использует два объекта <xref:Microsoft.Office.Interop.Word.Range> объектов. Один сохраняет текущее <xref:Microsoft.Office.Interop.Word.Selection>, и один задает весь документ, чтобы использовать в качестве диапазона поиска.  
  
## <a name="to-restore-the-users-original-selection-after-a-search"></a>Чтобы восстановление выделения после поиска пользователя  
  
1. Создание <xref:Microsoft.Office.Interop.Word.Range> объекты для документа и текущее выделение.  
  
    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2. Выполнения поиска и замены.  
  
    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3. Выберите начальный диапазон для восстановления выделения пользователя.  
  
    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
   В следующем примере показан полный метод.  
  
## <a name="example"></a>Пример  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Программным способом поиска и замены текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Практическое руководство. Программное задание параметров поиска в Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Практическое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
