---
title: "Как: программное добавление верхних и нижних колонтитулов в документы | Документы Microsoft"
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
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b11b774f88bb8d8f4882d52a4fd05954136b4b5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Практическое руководство. Программное добавление верхних и нижних колонтитулов к документам
  Для добавления текста в верхние и нижние колонтитулы в документе можно использовать свойство <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> и свойство <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> раздела <xref:Microsoft.Office.Interop.Word.Section>. Каждый раздел документа содержит три верхних и нижних колонтитула.  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Процедуры для настроек на уровне документа и надстроек VSTO отличаются друг от друга.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>Настройки уровня документа  
 Чтобы использовать следующие примеры кода, выполняйте их из класса `ThisDocument` в своем проекте.  
  
#### <a name="to-add-text-to-footers-in-the-document"></a>Добавление текста в нижние колонтитулы документа  
  
1.  Следующий пример кода задает шрифт текста, который необходимо вставить в основной нижний колонтитул каждого раздела документа, а затем вставляет текст в нижний колонтитул.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Добавление текста в верхние колонтитулы документа  
  
1.  Следующий пример кода добавляет поле для отображения номера страницы в каждом верхнем колонтитуле документа, а затем устанавливает выравнивание абзаца, чтобы выровнять текст по правому краю верхнего колонтитула.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>VSTO Add-ins  
 Чтобы использовать следующие примеры кода, выполняйте их из класса `ThisAddIn` в своем проекте.  
  
#### <a name="to-add-text-to-footers-in-a-document"></a>Добавление текста в нижние колонтитулы документа  
  
1.  Следующий пример кода задает шрифт текста, который необходимо вставить в основной нижний колонтитул каждого раздела документа, а затем вставляет текст в нижний колонтитул. В этом примере кода используется активный документ.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Добавление текста в верхние колонтитулы документа  
  
1.  Следующий пример кода добавляет поле для отображения номера страницы в каждом верхнем колонтитуле документа, а затем устанавливает выравнивание абзаца, чтобы выровнять текст по правому краю верхнего колонтитула. В этом примере кода используется активный документ.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное создание документов](../vsto/how-to-programmatically-create-new-documents.md)   
 [Как: программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Практическое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   