---
title: "Практическое руководство. Программная вставка текста в документы Word"
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
  - "диапазоны, вставка текста в документы"
  - "текст [разработка решений Office в Visual Studio], вставка в документы"
  - "диапазоны, замена текста в документах"
  - "документы [разработка решений Office в Visual Studio], вставка текста"
  - "текст [разработка решений Office в Visual Studio], замена"
ms.assetid: 405d7442-8ba3-4fcc-b17e-7b289ffd3967
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Практическое руководство. Программная вставка текста в документы Word
  Существует три основных способа вставки текста в документы Microsoft Office Word:  
  
-   вставка текста в диапазон;  
  
-   замена текста в диапазоне на новый текст;  
  
-   использование метода <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> объекта <xref:Microsoft.Office.Interop.Word.Selection> для вставки текста в позиции курсора или выделения.  
  
> [!NOTE]  
>  Вы также можете вставить текст в элементы управления содержимым и закладки. Дополнительные сведения см. в разделах [Элементы управления содержимым](../vsto/content-controls.md) и [Элементы управления Bookmark](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Вставка текста в диапазон  
 Используйте свойство <xref:Microsoft.Office.Interop.Word.Range.Text%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> для вставки текста в документ.  
  
#### Вставка текста в диапазон  
  
1.  Укажите диапазон в начале документа и вставьте текст **New Text**.  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomation#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#51)]  
  
     Следующий пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#51)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#51)]  
  
2.  Выберите объект <xref:Microsoft.Office.Interop.Word.Range>, который был расширен от одного символа до длины вставленного текста.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#52](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#52)]
     [!code-vb[Trin_VstcoreWordAutomation#52](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#52)]  
  
## Замена текста в диапазоне  
 Если указанный диапазон содержит текст, весь текст в диапазоне заменяется на вставленный текст.  
  
#### Замена текста в диапазоне  
  
1.  Создайте объект <xref:Microsoft.Office.Interop.Word.Range>, состоящий из первых 12 символов в документе.  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomation#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#53)]  
  
     Следующий пример кода можно использовать в надстройке VSTO. В этом примере кода используется активный документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#53)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#53)]  
  
2.  Замените эти символы строкой **New Text**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#54](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#54)]
     [!code-vb[Trin_VstcoreWordAutomation#54](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#54)]  
  
3.  Выберите диапазон.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#55](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#55)]
     [!code-vb[Trin_VstcoreWordAutomation#55](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#55)]  
  
## Вставка текста с помощью метода TypeText  
 Метод <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> вставляет текст в выделение.<xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> ведет себя по\-разному в зависимости от параметров, заданных на компьютере пользователя. Код в следующей процедуре объявляет объектную переменную <xref:Microsoft.Office.Interop.Word.Selection>, а также отключает параметр **Overtype**, если он включен. Если параметр **Overtype** включен, любой текст рядом с курсором будет перезаписан.  
  
#### Вставка текста с помощью метода TypeText  
  
1.  Объявите переменную объекта <xref:Microsoft.Office.Interop.Word.Selection>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#57](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#57)]
     [!code-vb[Trin_VstcoreWordAutomation#57](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#57)]  
  
2.  Отключите параметр **Overtype**, если он включен.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#58](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#58)]
     [!code-vb[Trin_VstcoreWordAutomation#58](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#58)]  
  
3.  Проверьте, находится ли текущее выделение у точки вставки.  
  
     Если это так, код вставляет предложение с помощью <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>, а затем знак абзаца с помощью метода <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A>.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#59](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#59)]
     [!code-vb[Trin_VstcoreWordAutomation#59](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#59)]  
  
4.  Код в блоке **ElseIf** проверяет, является ли выделение обычным блоком выделения. Если это так, другой блок **If** проверяет, включен ли параметр **ReplaceSelection**. Если это так, код использует метод <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> выделения, чтобы свернуть его до точки вставки в начале выделенного блока текста. Вставьте текст и знак абзаца.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#60](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#60)]
     [!code-vb[Trin_VstcoreWordAutomation#60](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#60)]  
  
5.  Если выделение не является точкой вставки или блоком выделенного текста, код в блоке **Else** не выполняет никаких действий.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#61](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#61)]
     [!code-vb[Trin_VstcoreWordAutomation#61](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#61)]  
  
 Можно также использовать метод <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> объекта <xref:Microsoft.Office.Interop.Word.Selection>, который имитирует нажатие клавиши BACKSPACE на клавиатуре. Но когда дело доходит до вставки и изменения текста, объект <xref:Microsoft.Office.Interop.Word.Range> предоставляет больше возможностей для управления.  
  
 В следующем примере показан полный код. Чтобы использовать этот пример, запустите код из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#56](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#56)]
 [!code-vb[Trin_VstcoreWordAutomation#56](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#56)]  
  
## См. также  
 [Практическое руководство. Программное форматирование текста в документах](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  