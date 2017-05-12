---
title: "Практическое руководство. Программный поиск и замена текста в документах"
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
  - "документы [разработка решений Office в Visual Studio], поиск"
  - "текст [разработка решений Office в Visual Studio], поиск в документах"
  - "текст [разработка решений Office в Visual Studio], текстовый поиск"
  - "текстовый поиск, документы"
  - "текстовый поиск, замена текста"
ms.assetid: a66962f5-eeb9-4dc6-a70f-9039ab437a63
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Практическое руководство. Программный поиск и замена текста в документах
  Объект <xref:Microsoft.Office.Interop.Word.Find> является членом объектов <xref:Microsoft.Office.Interop.Word.Selection> и <xref:Microsoft.Office.Interop.Word.Range>, каждый из которых можно использовать для поиска текста в документах Microsoft Office Word.  Команда замены является расширением команды поиска.  
  
 С помощью объекта <xref:Microsoft.Office.Interop.Word.Find> можно выполнять операцию перебора документа Microsoft Office Word и поиска конкретного текста, форматирования или стиля, а свойство <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> можно использовать для замены всех найденных элементов.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Использование объекта Selection  
 При использовании объекта <xref:Microsoft.Office.Interop.Word.Selection> для поиска текста все заданные условия применяются только для поиска текущего выделенного текста.  Если точкой вставки является <xref:Microsoft.Office.Interop.Word.Selection>, то поиск выполняется по документу.  Если будет найден элемент, соответствующий условиям поиска, он будет автоматически выделен.  
  
 Следует отметить, что условия <xref:Microsoft.Office.Interop.Word.Find> являются накопительными. Это означает, что условия добавляются к предыдущим условиям поиска.  Для сброса форматирования из предыдущих операций поиска перед выполнением нового поиска используйте метод <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>.  
  
#### Поиск текста с помощью объекта Selection  
  
1.  Назначьте переменной строку поиска.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#68)]
     [!code-vb[Trin_VstcoreWordAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#68)]  
  
2.  Сбросьте форматирование из предыдущих операций поиска.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#69)]
     [!code-vb[Trin_VstcoreWordAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#69)]  
  
3.  Выполните поиск и отобразите окно сообщения с результатами.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#70](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#70)]
     [!code-vb[Trin_VstcoreWordAutomation#70](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#70)]  
  
 В следующем примере показан полный метод.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#67)]
 [!code-vb[Trin_VstcoreWordAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#67)]  
  
## Использование объекта Range  
 Объект <xref:Microsoft.Office.Interop.Word.Range> позволяет искать текст, ничего не отображая в пользовательском интерфейсе.  Объект <xref:Microsoft.Office.Interop.Word.Find> возвращает **True**, если найден текст, соответствующий условиям поиска, и **False**, если это не так.  Он также переопределяет объект <xref:Microsoft.Office.Interop.Word.Range>, чтобы он соответствовал условиям поиска при обнаружении текста.  
  
#### Поиск текста с помощью объекта Range  
  
1.  Определите объект <xref:Microsoft.Office.Interop.Word.Range>, состоящий из второго абзаца в документе.  
  
     Следующий пример кода можно использовать в настройке на уровне документа.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomation#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#72)]  
  
     Следующий пример кода можно использовать в надстройке VSTO.  В этом примере используется активный документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#72)]  
  
2.  С помощью свойства <xref:Microsoft.Office.Interop.Word.Range.Find%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> сначала сбросьте все существующие параметры форматирования, а затем выполните поиск строки **find me**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#73](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#73)]
     [!code-vb[Trin_VstcoreWordAutomation#73](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#73)]  
  
3.  Отобразите результаты поиска в окне сообщения и выберите <xref:Microsoft.Office.Interop.Word.Range>, чтобы сделать его видимым.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#74](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#74)]
     [!code-vb[Trin_VstcoreWordAutomation#74](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#74)]  
  
     Если поиск заканчивается неудачно, выбирается второй абзац. При успешном выполнении поиска отображаются условия поиска.  
  
 В следующем примере показан полный код для настройки на уровне документа.  Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomation#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#71)]  
  
 В следующем примере показан полный код для надстройки VSTO.  Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#71)]  
  
## Поиск и замена текста в документах  
 Следующий код выполняет поиск текущего выделенного фрагмента и заменяет все вхождения строки **Искать** на строку **Найдено**.  
  
#### Поиск и замена текста в документах  
  
1.  Добавьте следующий пример кода в класс `ThisDocument` или `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#75)]
     [!code-vb[Trin_VstcoreWordAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#75)]  
  
     Класс <xref:Microsoft.Office.Interop.Word.Find> имеет метод <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A>, а класс <xref:Microsoft.Office.Interop.Word.Replacement> также имеет свой собственный метод <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>.  При выполнении операций поиска и замены необходимо использовать метод ClearFormatting обоих объектов.  Если его использовать только на объекте <xref:Microsoft.Office.Interop.Word.Find>, то при замене текста можно получить непредвиденные результаты.  
  
2.  Для замены каждого найденного элемента используйте метод <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> объекта <xref:Microsoft.Office.Interop.Word.Find>.  Чтобы указать заменяемые элементы, используйте параметр *Replace*.  Этот параметр может принимать одно из следующих значений <xref:Microsoft.Office.Interop.Word.WdReplace>:  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> заменяет все найденные элементы.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> не заменяет никакие найденные элементы.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> заменяет первый найденный элемент.  
  
## См. также  
 [Практическое руководство. Программное задание параметров поиска в Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Практическое руководство. Программный перебор найденных элементов в документах](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Практическое руководство. Программное восстановление выделения после поиска](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  