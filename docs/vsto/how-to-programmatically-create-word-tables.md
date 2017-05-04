---
title: "Практическое руководство. Программное таблиц в Word | Microsoft Docs"
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
  - "документы [разработка решений Office в Visual Studio], добавление таблиц"
  - "таблицы [разработка решений Office в Visual Studio], добавление к документам"
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Практическое руководство. Программное таблиц в Word
  Коллекция <xref:Microsoft.Office.Interop.Word.Tables> является членом классов <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> и <xref:Microsoft.Office.Interop.Word.Range>. Это означает, что таблицу можно создать в любом из их контекстов.  Для добавления таблицы в указанном диапазоне можно использовать метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> коллекции <xref:Microsoft.Office.Interop.Word.Tables>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Создание таблиц в настройках на уровне документа  
  
#### Добавление простой таблицы в документ  
  
-   Для добавления таблицы, состоящей из трех строк и четырех столбцов, в начало документа используйте метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>.  
  
     Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomation#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#86)]  
  
 При создании таблицы она автоматически добавляется в коллекцию <xref:Microsoft.Office.Interop.Word.Tables> ведущего элемента <xref:Microsoft.Office.Tools.Word.Document>.  Затем на таблицу можно ссылаться по номеру ее элемента с помощью свойства <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, как показано в следующем коде.  
  
#### Ссылка на таблицу по номеру элемента  
  
1.  Используйте свойство <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> и укажите номер элемента таблицы, на которую необходимо ссылаться.  
  
     Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomation#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#87)]  
  
 Каждый объект <xref:Microsoft.Office.Interop.Word.Table> также имеет свойство <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, которое позволяет настроить атрибуты форматирования.  
  
#### Применение стиля к таблице  
  
1.  Для применения одного из встроенных стилей Word к таблице используйте свойство <xref:Microsoft.Office.Interop.Word.Table.Style%2A>.  
  
     Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomation#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#88)]  
  
## Создание таблиц в надстройках VSTO  
  
#### Добавление простой таблицы в документ  
  
-   Для добавления таблицы, состоящей из трех строк и четырех столбцов, в начало документа используйте метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>.  
  
     Следующий пример кода добавляет таблицу в активный документ.  Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#86)]  
  
 При создании таблицы она автоматически добавляется в коллекцию <xref:Microsoft.Office.Interop.Word.Tables> в <xref:Microsoft.Office.Interop.Word.Document>.  Затем на таблицу можно ссылаться по номеру ее элемента с помощью свойства <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, как показано в следующем коде.  
  
#### Ссылка на таблицу по номеру элемента  
  
1.  Используйте свойство <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> и укажите номер элемента таблицы, на которую необходимо ссылаться.  
  
     В следующем примере кода используется активный документ.  Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#87)]  
  
 Каждый объект <xref:Microsoft.Office.Interop.Word.Table> также имеет свойство <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, которое позволяет настроить атрибуты форматирования.  
  
#### Применение стиля к таблице  
  
1.  Для применения одного из встроенных стилей Word к таблице используйте свойство <xref:Microsoft.Office.Interop.Word.Table.Style%2A>.  
  
     В следующем примере кода используется активный документ.  Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#88)]  
  
## См. также  
 [Практическое руководство. Программное добавление текста и форматирования в ячейки таблиц Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Практическое руководство. Программное добавление строк и столбцов в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Практическое руководство. Программное заполнение таблиц свойствами документа Word](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  