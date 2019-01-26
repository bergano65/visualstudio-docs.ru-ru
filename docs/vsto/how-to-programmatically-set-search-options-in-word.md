---
title: Как выполнить Программное задание параметров поиска в Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 66bd4258d04259c5356ce459328012d50445de62
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874371"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Как выполнить Программное задание параметров поиска в Word
  Чтобы задать параметры поиска для выбранных элементов в документах Microsoft Office Word двумя способами:  
  
- Задавать отдельные свойства из <xref:Microsoft.Office.Interop.Word.Find> объекта.  
  
- Использование аргументов <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод <xref:Microsoft.Office.Interop.Word.Find> объекта.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="use-properties-of-a-find-object"></a>Использование свойств объекта Find  
 Следующий код задает свойства <xref:Microsoft.Office.Interop.Word.Find> объекта для поиска текста в текущем выделении. Обратите внимание на то, что условия поиска, например поиск вперед, упаковки и текст для поиска, являются свойствами <xref:Microsoft.Office.Interop.Word.Find> объекта.  
  
 Задания всех свойств <xref:Microsoft.Office.Interop.Word.Find> не требуется, когда вы напишете код C#, так как в качестве параметров необходимо указать те же свойства <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод. Поэтому в этом примере содержится только код Visual Basic.  
  
### <a name="to-set-search-options-using-a-find-object"></a>Чтобы задать параметры поиска, с помощью объекта Find  
  
1.  Задание свойств <xref:Microsoft.Office.Interop.Word.Find> объект для поиска в прямом направлении для текста в объекте выделения **искать**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="use-execute-method-arguments"></a>Используйте аргументы метода Execute  
 В следующем коде используется <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод <xref:Microsoft.Office.Interop.Word.Find> объекта для поиска текста в текущем выделении. Обратите внимание, что условия поиска, например поиск вперед, упаковки и текст для поиска, передаются как параметры <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод.  
  
### <a name="to-set-search-options-using-execute-method-arguments"></a>Установка параметров поиска, с использованием аргументов метода Execute  
  
1.  Передайте условия поиска в качестве параметров <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод для поиска в прямом направлении для текста в объекте выделения **искать**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Программным способом поиска и замены текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Практическое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Практическое руководство. Программное восстановление выделения после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
