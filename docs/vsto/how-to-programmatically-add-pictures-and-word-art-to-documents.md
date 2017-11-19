---
title: "Как: программное добавление рисунков и объектов Word Art в документы | Документы Microsoft"
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
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a30c865a1bee9f3e8a75d5362688f1a83baba02a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Практическое руководство. Программное добавление рисунков и объектов Word Art в документы
  Вы можете добавлять изображения и графические объекты в документы во время разработки или во время выполнения. WordArt позволяет добавлять декоративный текст в документы Microsoft Office Word. Эти специальные текстовые эффекты представляют собой графические объекты, которые можно настроить и вставить в документ.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="adding-a-picture-at-design-time"></a>Добавление рисунка во время разработки  
 При создании настройки на уровне документа вы можете добавить изображение в документ во время разработки.  
  
#### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Добавление рисунка в документ Word во время разработки  
  
1.  Поместите курсор в место вставки изображения в документе.  
  
2.  Нажмите кнопку **вставить** ленты.  
  
3.  В **иллюстрации** щелкните **рисунок**.  
  
4.  В **Вставка рисунка** диалоговое окно, перейдите к рисунку, который требуется вставить и нажмите кнопку **вставить**.  
  
     Рисунок добавляется в документ в текущем положении курсора.  
  
## <a name="adding-a-picture-at-run-time"></a>Добавление рисунка во время выполнения  
 Рисунок можно вставить в документ в текущем положении курсора.  
  
#### <a name="to-add-a-picture-at-the-cursor-location"></a>Добавление рисунка в позиции курсора  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> коллекции <xref:Microsoft.Office.Interop.Word.InlineShapes> и передайте имя файла.  
  
     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]  
  
## <a name="adding-wordart-at-design-time"></a>Добавление объекта WordArt во время разработки  
 При создании настройки на уровне документа вы можете добавить объект WordArt в документ во время разработки.  
  
#### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Добавление объекта WordArt в документ Word во время разработки  
  
1.  Поместите курсор в место вставки объекта WordArt в документе.  
  
2.  Нажмите кнопку **вставить** ленты.  
  
3.  В **текст** щелкните **WordArt**, а затем выберите стиль WordArt.  
  
4.  Введите текст, который будет отображаться в документе, в **изменение текста WordArt** диалоговое окно и нажмите кнопку **ОК**.  
  
     Текст добавляется к документу с выбранным стилем WordArt.  
  
## <a name="adding-wordart-at-run-time"></a>Добавление объекта WordArt во время выполнения  
 Вы можете вставить объект WordArt в документ в текущем положении курсора. Процедура вставки отличается для настроек на уровне документа и надстроек VSTO.  
  
#### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Добавление объекта WordArt в положении курсора в настройке уровня документа  
  
1.  Получите левую и верхнюю позицию текущего положения курсора.  
  
     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]  
  
2.  Вызовите метод <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> объекта <xref:Microsoft.Office.Interop.Word.Shapes> в документе.  
  
     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]  
  
#### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Добавление объекта WordArt в положении курсора в надстройке VSTO  
  
1.  Получите левую и верхнюю позицию текущего положения курсора.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]  
  
2.  Вызовите метод <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> объекта <xref:Microsoft.Office.Interop.Word.Shapes> активного документа (или другого указанного документа).  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
  
-   Рисунок с именем **SamplePicture.jpg** должен находиться на диске C.  
  
## <a name="see-also"></a>См. также  
 [Как: Открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Как: программная Вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Как: программное восстановление выделения после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Как: программное сохранение документов](../vsto/how-to-programmatically-save-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  