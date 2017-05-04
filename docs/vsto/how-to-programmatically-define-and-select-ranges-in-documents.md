---
title: "Практическое руководство. Программное определение и выделение диапазонов в документах | Microsoft Docs"
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
  - "документы [разработка решений Office в Visual Studio], диапазоны"
  - "документы [разработка решений Office в Visual Studio], выбор предложений"
  - "диапазоны, определение в документах"
  - "диапазоны, выбор в документах"
  - "предложения, выбор в документах"
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Практическое руководство. Программное определение и выделение диапазонов в документах
  Вы можете определить диапазон в документе Microsoft Office Word с помощью объекта <xref:Microsoft.Office.Interop.Word.Range>.  Вы можете выбрать весь документ несколькими способами, например с помощью метода <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> или с помощью свойства Content класса <xref:Microsoft.Office.Tools.Word.Document> \(в настройке уровня документа\) или класса <xref:Microsoft.Office.Interop.Word.Document> \(в надстройке VSTO\).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Определение диапазона  
 В следующем примере показано, как создать объект <xref:Microsoft.Office.Interop.Word.Range>, включающий первые семь символов в активном документе, в том числе непечатаемые символы.  Затем выполняется выбор текста в пределах диапазона.  
  
#### Определение диапазона в настройке на уровне документа  
  
1.  Добавьте диапазон в документ, передав начальный и последний символ в метод <xref:Microsoft.Office.Tools.Word.Document.Range%2A> класса <xref:Microsoft.Office.Tools.Word.Document>.  Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#18)]  
  
#### Определение диапазона с помощью надстройки VSTO  
  
1.  Добавьте диапазон в документ, передав начальный и последний символ в метод <xref:Microsoft.Office.Interop.Word._Document.Range%2A> класса <xref:Microsoft.Office.Interop.Word.Document>.  Следующий пример кода добавляет диапазон в активный документ.  Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## Выбор диапазона в настройке на уровне документа  
 В следующих примерах показано, как выделить весь документ с помощью метода <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> или с помощью свойства <xref:Microsoft.Office.Tools.Word.Document.Content%2A> класса <xref:Microsoft.Office.Tools.Word.Document>.  
  
#### Выбор всего документа как диапазона с помощью метода Select  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>, который содержит весь документ.  Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#19)]  
  
#### Выбор всего документа как диапазона с помощью свойства Content  
  
1.  Используйте свойство <xref:Microsoft.Office.Tools.Word.Document.Content%2A>, чтобы определить диапазон, который содержит весь документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#20)]  
  
 Для определения диапазона также можно использовать методы и свойства других объектов.  
  
#### Выделение предложения в активном документе  
  
1.  Задайте диапазон с помощью коллекции <xref:Microsoft.Office.Interop.Word.Sentences>.  Используйте индекс предложения, которое нужно выбрать.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#21)]  
  
 Еще один способ выделения предложения состоит в том, чтобы вручную установить начальное и конечное значение для диапазона.  
  
#### Выделение предложения вручную с помощью установки начального и конечного значений  
  
1.  Создайте переменную диапазона.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#23)]  
  
2.  Проверьте, есть ли в документе хотя бы два предложения, задайте аргументы *Start* и *End* диапазона, а затем выберите диапазон.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#24)]  
  
## Выбор диапазона с помощью надстройки VSTO  
 В следующих примерах показано, как выделить весь документ с помощью метода <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range> или с помощью свойства <xref:Microsoft.Office.Interop.Word._Document.Content%2A> класса <xref:Microsoft.Office.Interop.Word.Document>.  
  
#### Выбор всего документа как диапазона с помощью метода Select  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Range.Select%2A> объекта <xref:Microsoft.Office.Interop.Word.Range>, который содержит весь документ.  Следующий пример кода выделяет содержимое активного документа.  Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
#### Выбор всего документа как диапазона с помощью свойства Content  
  
1.  Используйте свойство <xref:Microsoft.Office.Interop.Word._Document.Content%2A>, чтобы определить диапазон, который содержит весь документ.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
 Для определения диапазона также можно использовать методы и свойства других объектов.  
  
#### Выделение предложения в активном документе  
  
1.  Задайте диапазон с помощью коллекции <xref:Microsoft.Office.Interop.Word.Sentences>.  Используйте индекс предложения, которое нужно выбрать.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
 Еще один способ выделения предложения состоит в том, чтобы вручную установить начальное и конечное значение для диапазона.  
  
#### Выделение предложения вручную с помощью установки начального и конечного значений  
  
1.  Создайте переменную диапазона.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
2.  Проверьте, есть ли в документе хотя бы два предложения, задайте аргументы *Start* и *End* диапазона, а затем выберите диапазон.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## См. также  
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Практическое руководство. Программное извлечение символов начала и завершения в диапазонах](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Практическое руководство. Программное расширение диапазонов в документах](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Практическое руководство. Программный сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Практическое руководство. Программное свертывание диапазонов и выделений в документах](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Практическое руководство. Программное исключение знаков абзаца при создании диапазонов](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  