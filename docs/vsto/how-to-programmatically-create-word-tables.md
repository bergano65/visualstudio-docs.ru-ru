---
title: Как выполнить Программное создание таблиц Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 639fa67599cfee71d3d41fa6512ca609aa4d099a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902023"
---
# <a name="how-to-programmatically-create-word-tables"></a>Как выполнить Программное создание таблиц Word
  Коллекция <xref:Microsoft.Office.Interop.Word.Tables> является членом классов <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> и <xref:Microsoft.Office.Interop.Word.Range>. Это означает, что таблицу можно создать в любом из их контекстов. Для добавления таблицы в указанном диапазоне можно использовать метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> коллекции <xref:Microsoft.Office.Interop.Word.Tables>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="create-tables-in-document-level-customizations"></a>Создание таблиц в настройках уровня документа  
  
### <a name="to-add-a-table-to-a-document"></a>Чтобы добавить таблицу в документ  
  
- Для добавления таблицы, состоящей из трех строк и четырех столбцов, в начало документа используйте метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>.  
  
   Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
   [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
  При создании таблицы она автоматически добавляется в коллекцию <xref:Microsoft.Office.Interop.Word.Tables> ведущего элемента <xref:Microsoft.Office.Tools.Word.Document>. Затем на таблицу можно ссылаться по номеру ее элемента с помощью свойства <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, как показано в следующем коде.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>Ссылка на таблицу по номеру элемента  
  
1. Используйте свойство <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> и укажите номер элемента таблицы, на которую необходимо ссылаться.  
  
    Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
    [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
   Каждый объект <xref:Microsoft.Office.Interop.Word.Table> также имеет свойство <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, которое позволяет настроить атрибуты форматирования.  
  
### <a name="to-apply-a-style-to-a-table"></a>Применение стиля к таблице  
  
1.  Для применения одного из встроенных стилей Word к таблице используйте свойство <xref:Microsoft.Office.Interop.Word.Table.Style%2A>.  
  
     Чтобы использовать следующий пример кода, выполните его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="create-tables-in-vsto-add-ins"></a>Создание таблиц в надстройках VSTO  
  
### <a name="to-add-a-table-to-a-document"></a>Чтобы добавить таблицу в документ  
  
- Для добавления таблицы, состоящей из трех строк и четырех столбцов, в начало документа используйте метод <xref:Microsoft.Office.Interop.Word.Tables.Add%2A>.  
  
   Следующий пример кода добавляет таблицу в активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
   [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
  При создании таблицы она автоматически добавляется в коллекцию <xref:Microsoft.Office.Interop.Word.Tables> в <xref:Microsoft.Office.Interop.Word.Document>. Затем на таблицу можно ссылаться по номеру ее элемента с помощью свойства <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, как показано в следующем коде.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>Ссылка на таблицу по номеру элемента  
  
1. Используйте свойство <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> и укажите номер элемента таблицы, на которую необходимо ссылаться.  
  
    В следующем примере кода используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
   Каждый объект <xref:Microsoft.Office.Interop.Word.Table> также имеет свойство <xref:Microsoft.Office.Interop.Word.Table.Range%2A>, которое позволяет настроить атрибуты форматирования.  
  
### <a name="to-apply-a-style-to-a-table"></a>Применение стиля к таблице  
  
1.  Для применения одного из встроенных стилей Word к таблице используйте свойство <xref:Microsoft.Office.Interop.Word.Table.Style%2A>.  
  
     В следующем примере кода используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Программное добавление текста и форматирования в ячейки таблиц Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Практическое руководство. Программное добавление строк и столбцов в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Практическое руководство. Программное заполнение таблиц Word свойствами документа](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
