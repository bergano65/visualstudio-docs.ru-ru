---
title: "Как: программное создание таблиц Word | Документы Microsoft"
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
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0c903ed815e35c3d4f6821d70910ef56611889f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-word-tables"></a>Практическое руководство. Программное таблиц в Word
  Коллекция <xref:Microsoft.Office.Interop.Word.Tables> является членом классов <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> и <xref:Microsoft.Office.Interop.Word.Range>. Это означает, что таблицу можно создать в любом из их контекстов. Для добавления таблицы в указанном диапазоне можно использовать метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> коллекции <xref:Microsoft.Office.Interop.Word.Tables>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="creating-tables-in-document-level-customizations"></a>Создание таблиц в настройках на уровне документа  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>Добавление простой таблицы в документ  
  
-   Для добавления таблицы, состоящей из трех строк и четырех столбцов, в начало документа используйте метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>.  
  
     Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
 При создании таблицы она автоматически добавляется в коллекцию <xref:Microsoft.Office.Interop.Word.Tables> ведущего элемента <xref:Microsoft.Office.Tools.Word.Document>. Затем на таблицу можно ссылаться по номеру ее элемента с помощью свойства <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, как показано в следующем коде.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>Ссылка на таблицу по номеру элемента  
  
1.  Используйте свойство <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> и укажите номер элемента таблицы, на которую необходимо ссылаться.  
  
     Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
 Каждый объект <xref:Microsoft.Office.Interop.Word.Table> также имеет свойство <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, которое позволяет настроить атрибуты форматирования.  
  
#### <a name="to-apply-a-style-to-a-table"></a>Применение стиля к таблице  
  
1.  Для применения одного из встроенных стилей Word к таблице используйте свойство <xref:Microsoft.Office.Interop.Word.Table.Style%2A>.  
  
     Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="creating-tables-in-vsto-add-ins"></a>Создание таблиц в надстройках VSTO  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>Добавление простой таблицы в документ  
  
-   Для добавления таблицы, состоящей из трех строк и четырех столбцов, в начало документа используйте метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>.  
  
     Следующий пример кода добавляет таблицу в активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
 При создании таблицы она автоматически добавляется в коллекцию <xref:Microsoft.Office.Interop.Word.Tables> в <xref:Microsoft.Office.Interop.Word.Document>. Затем на таблицу можно ссылаться по номеру ее элемента с помощью свойства <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, как показано в следующем коде.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>Ссылка на таблицу по номеру элемента  
  
1.  Используйте свойство <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> и укажите номер элемента таблицы, на которую необходимо ссылаться.  
  
     В следующем примере кода используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
 Каждый объект <xref:Microsoft.Office.Interop.Word.Table> также имеет свойство <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, которое позволяет настроить атрибуты форматирования.  
  
#### <a name="to-apply-a-style-to-a-table"></a>Применение стиля к таблице  
  
1.  Для применения одного из встроенных стилей Word к таблице используйте свойство <xref:Microsoft.Office.Interop.Word.Table.Style%2A>.  
  
     В следующем примере кода используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное добавление текста и форматирования в ячейки таблиц Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Как: программным образом добавить строки и столбцы в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Как: программное заполнение таблиц Word свойствами документа](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  