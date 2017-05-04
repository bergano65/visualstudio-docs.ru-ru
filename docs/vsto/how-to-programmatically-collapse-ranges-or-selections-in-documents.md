---
title: "Практическое руководство. Программное свертывание диапазонов и выделений в документах | Microsoft Docs"
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
  - "выбор, сворачивание"
  - "документы [разработка решений Office в Visual Studio], сворачивание диапазонов"
  - "сворачивание - выбор"
  - "диапазоны, сворачивание"
  - "сворачивание диапазонов"
ms.assetid: 0bd059dd-8606-42ae-a8a9-97f8f3bd5cc5
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Практическое руководство. Программное свертывание диапазонов и выделений в документах
  Если вы работаете с объектом <xref:Microsoft.Office.Interop.Word.Range> или <xref:Microsoft.Office.Interop.Word.Selection>, может потребоваться изменить выделение на точку вставки перед вставкой текста, чтобы избежать перезаписи существующего текста. Оба объекта <xref:Microsoft.Office.Interop.Word.Range> и <xref:Microsoft.Office.Interop.Word.Selection> имеют Collapse метод, использующий значения перечисления <xref:Microsoft.Office.Interop.Word.WdCollapseDirection>.  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> сворачивает выделение к началу выделения. Это значение по умолчанию, если не указано значение перечисления.  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> сворачивает выделение к концу выделения.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Сворачивание диапазона и вставка нового текста  
  
1.  Создайте объект <xref:Microsoft.Office.Interop.Word.Range>, состоящий из первого абзаца в документе.  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomation#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#46)]  
  
     Приведенный ниже пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#46)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#46)]  
  
2.  Используйте значение перечисления <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> для сворачивания диапазона.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#47](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#47)]
     [!code-vb[Trin_VstcoreWordAutomation#47](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#47)]  
  
3.  Вставьте новый текст.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#48](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#48)]
     [!code-vb[Trin_VstcoreWordAutomation#48](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#48)]  
  
4.  Выберите <xref:Microsoft.Office.Interop.Word.Range>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#49](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#49)]
     [!code-vb[Trin_VstcoreWordAutomation#49](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#49)]  
  
 Если вы используете значение перечисления <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd>, текст вставляется в начало следующего абзаца.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#50](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#50)]
 [!code-vb[Trin_VstcoreWordAutomation#50](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#50)]  
  
 Можно предположить, что вставка нового предложения выполняется перед символом абзаца, но это не так, поскольку исходный диапазон включает символ абзаца. Для получения дополнительной информации см. [Практическое руководство. Программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## Пример настройки на уровне документа  
  
#### Сворачивание диапазона в настройке на уровне документа  
  
1.  В следующем примере показан полный метод для настройки на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomation#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#45)]  
  
## Примеры надстройки VSTO  
  
#### Сворачивание диапазона в надстройке VSTO  
  
1.  В следующем примере показан полный метод для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#45)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#45)]  
  
## См. также  
 [Практическое руководство. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое руководство. Программное извлечение символов начала и завершения в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Практическое руководство. Программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Практическое руководство. Программный сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  
  