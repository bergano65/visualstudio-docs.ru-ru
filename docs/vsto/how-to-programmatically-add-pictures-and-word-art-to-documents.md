---
title: Практическое руководство. Программное добавление рисунков и объекта Word Art в документы
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f805153a35517c473e95beb871ae7d12a2776bd4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967612"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>Практическое руководство. Программное добавление рисунков и объекта Word Art в документы
  Вы можете добавлять изображения и графические объекты в документы во время разработки или во время выполнения. WordArt позволяет добавлять декоративный текст в документы Microsoft Office Word. Эти специальные текстовые эффекты представляют собой графические объекты, которые можно настроить и вставить в документ.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>Добавление рисунка во время разработки
 При создании настройки на уровне документа вы можете добавить изображение в документ во время разработки.

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>Добавление рисунка в документ Word во время разработки

1. Поместите курсор в место вставки изображения в документе.

2. Нажмите кнопку **вставить** вкладке ленты.

3. В **иллюстрации** щелкните **рисунок**.

4. В **Вставка рисунка** диалоговом окне перейдите к рисунку, который требуется вставить и нажмите кнопку **вставить**.

     Рисунок добавляется в документ в текущем положении курсора.

## <a name="add-a-picture-at-runtime"></a>Добавление рисунка во время выполнения
 Рисунок можно вставить в документ в текущем положении курсора.

### <a name="to-add-a-picture-at-the-cursor-location"></a>Добавление рисунка в позиции курсора

1. Вызовите метод <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> коллекции <xref:Microsoft.Office.Interop.Word.InlineShapes> и передайте имя файла.

     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]

## <a name="add-wordart-at-design-time"></a>Добавление объекта WordArt во время разработки
 При создании настройки на уровне документа вы можете добавить объект WordArt в документ во время разработки.

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>Добавление объекта WordArt в документ Word во время разработки

1. Поместите курсор в место вставки объекта WordArt в документе.

2. Нажмите кнопку **вставить** вкладке ленты.

3. В **текст** щелкните **WordArt**, а затем выберите стиль WordArt.

4. Введите текст, который будет отображаться в документе, чтобы **изменение текста WordArt** диалоговое окно и нажмите кнопку **ОК**.

     Текст добавляется к документу с выбранным стилем WordArt.

## <a name="add-wordart-at-runtime"></a>Добавление объекта WordArt во время выполнения
 Вы можете вставить объект WordArt в документ в текущем положении курсора. Процедура вставки отличается для настроек на уровне документа и надстроек VSTO.

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>Добавление объекта WordArt в положении курсора в настройке уровня документа

1. Получите левую и верхнюю позицию текущего положения курсора.

     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]

2. Вызовите метод <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> объекта <xref:Microsoft.Office.Interop.Word.Shapes> в документе.

     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>Добавление объекта WordArt в положении курсора в надстройке VSTO

1. Получите левую и верхнюю позицию текущего положения курсора.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]

2. Вызовите метод <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> объекта <xref:Microsoft.Office.Interop.Word.Shapes> активного документа (или другого указанного документа).

     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]

## <a name="compile-the-code"></a>Компиляция кода

- Рисунок с именем *SamplePicture.jpg* должен существовать на диске C.

## <a name="see-also"></a>См. также
- [Практическое руководство. Программное Открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)
- [Практическое руководство. Программная Вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Практическое руководство. Программное восстановление выделения после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Практическое руководство. Программное сохранение документов](../vsto/how-to-programmatically-save-documents.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
