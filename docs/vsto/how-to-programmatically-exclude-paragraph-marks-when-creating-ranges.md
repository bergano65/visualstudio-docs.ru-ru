---
title: "Как: программное исключение знаков абзаца при создании диапазонов | Документы Microsoft"
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
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4012211a39e1286becadd503a20d402f9ac7c7a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Практическое руководство. Программное исключение знаков абзаца при создании диапазонов
  При каждом создании объекта <xref:Microsoft.Office.Interop.Word.Range> на основе абзаца все непечатаемые символы, такие как знаки абзаца, включаются в диапазон. Можно вставить текст из исходного абзаца в целевой абзац. Если вы не хотите разделять целевой абзац на отдельные абзацы, то необходимо сначала удалить знаки абзаца из исходного абзаца. Кроме того, поскольку сведения о форматировании абзаца хранятся в знаке абзаца, вы можете не захотеть включать их при вставке диапазона в существующий абзац.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 В приведенной ниже процедуре объявляются две строковые переменные, извлекается содержимое первого и второго абзаца в активном документе, а потом их содержимое обменивается. Затем в примере демонстрируется удаление знака абзаца из диапазона с помощью метода <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> и вставка текста в абзаце.  
  
### <a name="to-control-paragraph-structure-when-inserting-text"></a>Управление структурой абзаца при вставке текста  
  
1.  Создайте две переменные диапазона для первого и второго абзаца и извлеките их содержимое при помощи свойства <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  
  
     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]  
  
     Приведенный ниже пример кода можно использовать в надстройке VSTO уровня приложения. В этом примере кода используется активный документ.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]  
  
2.  Назначьте свойство <xref:Microsoft.Office.Interop.Word.Range.Text%2A> , переключающее текст между двумя абзацами.  
  
     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]  
  
3.  По очереди выбирайте каждый диапазон и делайте паузу, чтобы отобразить результаты в окне сообщения.  
  
     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]  
  
4.  Настройте `firstRange` с помощью метода <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> , чтобы символ абзаца больше не являлся частью `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]  
  
5.  Замените оставшийся текст в первом абзаце, назначив новую строку в свойстве <xref:Microsoft.Office.Interop.Word.Range.Text%2A> диапазона.  
  
     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]  
  
6.  Замените текст в `secondRange`, включая знак абзаца.  
  
     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]  
  
7.  Выберите `firstRange` и сделайте паузу для отображения результатов в окне сообщения, а затем сделайте то же самое с `secondRange`.  
  
     Поскольку `firstRange` был переопределен, чтобы исключить знак абзаца, первоначальное форматирование абзаца сохраняется. Однако вместо знака абзаца в `secondRange`было вставлено предложение, удаляющее отдельный абзац.  
  
     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]  
  
     Исходное содержимое обоих диапазонов было сохранено в виде строк, поэтому можно восстановить исходное состояние документа.  
  
8.  Перенастройте `firstRange` , чтобы включить знак абзаца, используя метод <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> для одной символьной позиции.  
  
     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]  
  
9. Удалите `secondRange`. Это восстановит третий абзац в исходное положение.  
  
     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]  
  
10. Восстановите первоначальный текст абзаца в `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]  
  
11. Используйте метод <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> для вставки исходного содержимого второго абзаца после `firstRange`, а затем выберите `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]  
  
## <a name="document-level-customization-example"></a>Пример настройки на уровне документа  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Управление структурой абзаца при вставке текста в настройках уровня документа  
  
1.  В следующем примере показан полный метод для настройки на уровне документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]  
  
## <a name="vsto-add-in-example"></a>Примеры надстройки VSTO  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-an-vsto-add-in"></a>Управление структурой абзаца при вставке текста в надстройке VSTO  
  
1.  В следующем примере показан полный метод для надстройки VSTO. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Как: программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Как: программная Вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Как: программным образом сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Как: программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  