---
title: "Практическое руководство. Программное добавление строк и столбцов в таблицы Word"
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
  - "столбцы [разработка решений Office в Visual Studio], добавление к таблицам Word"
  - "строки [разработка решений Office в Visual Studio], добавление к таблицам Word"
  - "таблицы [разработка решений Office в Visual Studio], добавление строк и столбцов"
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Практическое руководство. Программное добавление строк и столбцов в таблицы Word
  В таблице Microsoft Office Word ячейки организованы по строкам и столбцам.  Вы можете использовать метод <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> объекта <xref:Microsoft.Office.Interop.Word.Rows> для добавления строк в таблицу и метод <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> объекта <xref:Microsoft.Office.Interop.Word.Columns> для добавления столбцов.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Примеры настроек на уровне документа  
 Следующие примеры кода можно использовать в настройке на уровне документа.  Чтобы использовать эти примеры, выполняйте их из класса `ThisDocument` в своем проекте.  В этих примерах предполагается, что документ, связанный с настройкой, уже содержит по крайней мере одну таблицу.  
  
> [!IMPORTANT]  
>  Этот код выполняется только в тех проектах, которые создаются с помощью любого из следующих шаблонов проекта:  
>   
>  -   Документ Word 2013  
> -   Шаблон Word 2013  
> -   Документ Word 2010  
> -   Шаблон Word 2010  
>   
>  Если эту задачу требуется выполнить в проекте любого другого типа, необходимо добавить ссылку на сборку **Microsoft.Office.Interop.Word**, а затем использовать классы из этой сборки, чтобы добавить строки и столбцы в таблицы.  Дополнительные сведения см. в разделе[Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия для Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### Добавление строки в таблицу  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>, чтобы добавить строку в таблицу.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomation#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#95)]  
  
#### Добавление столбца в таблицу  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, а затем метод <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>, чтобы сделать все столбцы одинаковой ширины.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomation#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#96)]  
  
## Примеры надстроек VSTO  
 Следующие примеры кода можно использовать в надстройке VSTO.  Чтобы использовать эти примеры, выполняйте их из класса `ThisAddIn` в своем проекте.  В этих примерах предполагается, что активный документ содержит хотя бы одну таблицу.  
  
> [!IMPORTANT]  
>  Этот код выполняется только в тех проектах, которые создаются с помощью шаблонов Word VSTO.  
>   
>  Если эту задачу требуется выполнить в проекте любого другого типа, необходимо добавить ссылку на сборку **Microsoft.Office.Interop.Word**, а затем использовать классы из этой сборки, чтобы добавить строки и столбцы в таблицы.  Дополнительные сведения см. в разделе[Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Справочник по основной сборке взаимодействия для Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### Добавление строки в таблицу  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>, чтобы добавить строку в таблицу.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#95)]  
  
#### Добавление столбца в таблицу  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, а затем метод <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>, чтобы сделать все столбцы одинаковой ширины.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#96)]  
  
## См. также  
 [Практическое руководство. Программное таблиц в Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Практическое руководство. Программное добавление текста и форматирования в ячейки таблиц Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Практическое руководство. Программное заполнение таблиц свойствами документа Word](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  