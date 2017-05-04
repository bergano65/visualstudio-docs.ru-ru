---
title: "Практическое руководство. Программное добавление рисунков и объектов Word Art в документы | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "документы [разработка решений Office в Visual Studio], добавление рисунков"
  - "графика, добавление к документам Word"
  - "документы Word, добавление рисунков"
  - "документы Word, добавление объекта Word Art"
  - "объект WordArt, добавление к документам"
ms.assetid: 944e1858-bc7c-471f-b5e7-adf3b0fa574d
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Практическое руководство. Программное добавление рисунков и объектов Word Art в документы
  Вы можете добавлять изображения и графические объекты в документы во время разработки или во время выполнения.  WordArt позволяет добавлять декоративный текст в документы Microsoft Office Word.  Эти специальные текстовые эффекты представляют собой графические объекты, которые можно настроить и вставить в документ.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Добавление рисунка во время разработки  
 При создании настройки на уровне документа вы можете добавить изображение в документ во время разработки.  
  
#### Добавление рисунка в документ Word во время разработки  
  
1.  Поместите курсор в место вставки изображения в документе.  
  
2.  На ленте перейдите на вкладку **Вставка**.  
  
3.  В группе **Иллюстрации** щелкните **Рисунок**.  
  
4.  В диалоговом окне **Вставка рисунка** перейдите к рисунку, который требуется вставить, и нажмите кнопку **Вставить**.  
  
     Рисунок добавляется в документ в текущем положении курсора.  
  
## Добавление рисунка во время выполнения  
 Рисунок можно вставить в документ в текущем положении курсора.  
  
#### Добавление рисунка в позиции курсора  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> коллекции <xref:Microsoft.Office.Interop.Word.InlineShapes> и передайте имя файла.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#108](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#108)]
     [!code-vb[Trin_VstcoreWordAutomation#108](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#108)]  
  
## Добавление объекта WordArt во время разработки  
 При создании настройки на уровне документа вы можете добавить объект WordArt в документ во время разработки.  
  
#### Добавление объекта WordArt в документ Word во время разработки  
  
1.  Поместите курсор в место вставки объекта WordArt в документе.  
  
2.  На ленте перейдите на вкладку **Вставка**.  
  
3.  В группе **Текст** щелкните **Объект WordArt**, а затем выберите стиль WordArt.  
  
4.  Введите текст, который будет отображаться в документе, в диалоговом окне **Изменение текста WordArt** и нажмите кнопку **ОК**.  
  
     Текст добавляется к документу с выбранным стилем WordArt.  
  
## Добавление объекта WordArt во время выполнения  
 Вы можете вставить объект WordArt в документ в текущем положении курсора.  Процедура вставки отличается для настроек на уровне документа и надстроек VSTO.  
  
#### Добавление объекта WordArt в положении курсора в настройке уровня документа  
  
1.  Получите левую и верхнюю позицию текущего положения курсора.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomation#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#109)]  
  
2.  Вызовите метод <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> объекта <xref:Microsoft.Office.Interop.Word.Shapes> в документе.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomation#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#110)]  
  
#### Добавление объекта WordArt в положении курсора в надстройке VSTO  
  
1.  Получите левую и верхнюю позицию текущего положения курсора.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#109)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#109)]  
  
2.  Вызовите метод <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> объекта <xref:Microsoft.Office.Interop.Word.Shapes> активного документа \(или другого указанного документа\).  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#110)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#110)]  
  
## Компиляция кода  
  
-   Рисунок с именем **SamplePicture.jpg** должен находиться на диске C.  
  
## См. также  
 [Практическое руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Практическое руководство. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Практическое руководство. Программное восстановление выделения после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Практическое руководство. Программное сохранение документов](../vsto/how-to-programmatically-save-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  