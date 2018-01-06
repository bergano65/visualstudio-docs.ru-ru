---
title: "Как: программное задание параметров поиска в Word | Документы Microsoft"
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
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b6bd57dfbb7cec6075d72b80228e77669e365dd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Практическое руководство. Программное задание параметров поиска в Word
  Чтобы задать параметры поиска для выбранных элементов в документы Microsoft Office Word двумя способами.  
  
-   Задать отдельные свойства <xref:Microsoft.Office.Interop.Word.Find> объекта.  
  
-   Использование аргументов <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод <xref:Microsoft.Office.Interop.Word.Find> объекта.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-properties-of-a-find-object"></a>Использование свойств объекта Find  
 Следующий код задает свойства <xref:Microsoft.Office.Interop.Word.Find> объекта для поиска текста в выделенном фрагменте. Обратите внимание, что условия поиска, например поиск вперед, упаковки и текст для поиска, свойства <xref:Microsoft.Office.Interop.Word.Find> объекта.  
  
 Задания всех свойств <xref:Microsoft.Office.Interop.Word.Find> не требуется, при написании кода C#, так как необходимо указать те же свойства в качестве параметров <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод. Поэтому этот пример содержит только код Visual Basic.  
  
#### <a name="to-set-search-options-using-a-find-object"></a>Установка параметров поиска с помощью объекта Find  
  
1.  Задание свойств <xref:Microsoft.Office.Interop.Word.Find> объекта поиск вперед выделения для текста **искать**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="using-execute-method-arguments"></a>Использование аргументов метода Execute  
 В следующем коде используется <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод <xref:Microsoft.Office.Interop.Word.Find> объекта для поиска текста в выделенном фрагменте. Обратите внимание, что условия поиска, например поиск вперед, упаковки и текст для поиска, передаются как параметры <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод.  
  
#### <a name="to-set-search-options-using-execute-method-arguments"></a>Установка параметров поиска с помощью аргументов метода Execute  
  
1.  Передайте условия поиска в качестве параметров <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> метод поиск вперед выделения для текста **искать**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>См. также  
 [Как: программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Как: программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Практическое руководство. Программное восстановление выделения после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  