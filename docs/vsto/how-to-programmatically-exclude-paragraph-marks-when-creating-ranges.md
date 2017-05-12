---
title: "Практическое руководство. Программное исключение знаков абзаца при создании диапазонов"
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
  - "документы [разработка решений Office в Visual Studio], исключение абзацев"
  - "диапазоны, исключение знаков абзаца в Word"
  - "документы [разработка решений Office в Visual Studio], знаки абзаца"
  - "абзацы, управление структурой"
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Практическое руководство. Программное исключение знаков абзаца при создании диапазонов
  При каждом создании объекта <xref:Microsoft.Office.Interop.Word.Range> на основе абзаца все непечатаемые символы, такие как знаки абзаца, включаются в диапазон. Можно вставить текст из исходного абзаца в целевой абзац. Если вы не хотите разделять целевой абзац на отдельные абзацы, то необходимо сначала удалить знаки абзаца из исходного абзаца. Кроме того, поскольку сведения о форматировании абзаца хранятся в знаке абзаца, вы можете не захотеть включать их при вставке диапазона в существующий абзац.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 В приведенной ниже процедуре объявляются две строковые переменные, извлекается содержимое первого и второго абзаца в активном документе, а потом их содержимое обменивается. Затем в примере демонстрируется удаление знака абзаца из диапазона с помощью метода <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> и вставка текста в абзаце.  
  
### Управление структурой абзаца при вставке текста  
  
1.  Создайте две переменные диапазона для первого и второго абзаца и извлеките их содержимое при помощи свойства <xref:Microsoft.Office.Interop.Word.Range.Text%2A>.  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#27)]  
  
     Приведенный ниже пример кода можно использовать в надстройке VSTO уровня приложения. В этом примере кода используется активный документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
2.  Назначьте свойство <xref:Microsoft.Office.Interop.Word.Range.Text%2A>, переключающее текст между двумя абзацами.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#28)]
     [!code-vb[Trin_VstcoreWordAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#28)]  
  
3.  По очереди выбирайте каждый диапазон и делайте паузу, чтобы отобразить результаты в окне сообщения.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#29)]
     [!code-vb[Trin_VstcoreWordAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#29)]  
  
4.  Настройте `firstRange` с помощью метода <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A>, чтобы символ абзаца больше не являлся частью `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreWordAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#30)]  
  
5.  Замените оставшийся текст в первом абзаце, назначив новую строку в свойстве <xref:Microsoft.Office.Interop.Word.Range.Text%2A> диапазона.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreWordAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#31)]  
  
6.  Замените текст в `secondRange`, включая знак абзаца.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#32)]
     [!code-vb[Trin_VstcoreWordAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#32)]  
  
7.  Выберите `firstRange` и сделайте паузу для отображения результатов в окне сообщения, а затем сделайте то же самое с `secondRange`.  
  
     Поскольку `firstRange` был переопределен, чтобы исключить знак абзаца, первоначальное форматирование абзаца сохраняется. Однако вместо знака абзаца в `secondRange` было вставлено предложение, удаляющее отдельный абзац.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#33)]
     [!code-vb[Trin_VstcoreWordAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#33)]  
  
     Исходное содержимое обоих диапазонов было сохранено в виде строк, поэтому можно восстановить исходное состояние документа.  
  
8.  Перенастройте `firstRange`, чтобы включить знак абзаца, используя метод <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> для одной символьной позиции.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreWordAutomation#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#34)]  
  
9. Удалите `secondRange`. Это восстановит третий абзац в исходное положение.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#35](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#35)]
     [!code-vb[Trin_VstcoreWordAutomation#35](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#35)]  
  
10. Восстановите первоначальный текст абзаца в `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#36)]
     [!code-vb[Trin_VstcoreWordAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#36)]  
  
11. Используйте метод <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> для вставки исходного содержимого второго абзаца после `firstRange`, а затем выберите `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#37)]
     [!code-vb[Trin_VstcoreWordAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#37)]  
  
## Пример настройки на уровне документа  
  
#### Управление структурой абзаца при вставке текста в настройках уровня документа  
  
1.  В следующем примере показан полный метод для настройки на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#26)]  
  
## Примеры надстройки VSTO  
  
#### Управление структурой абзаца при вставке текста в надстройке VSTO  
  
1.  В следующем примере показан полный метод для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
## См. также  
 [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Практическое руководство. Программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Практическое руководство. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Практическое руководство. Программный сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  