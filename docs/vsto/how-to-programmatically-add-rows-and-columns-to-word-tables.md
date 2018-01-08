---
title: "Как: программным образом добавить строки и столбцы в таблицы Word | Документы Microsoft"
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
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 56d8c3d0c578d2dc13cf65af680bc2fb804f3539
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Практическое руководство. Программное добавление строк и столбцов в таблицы Word
  В таблице Microsoft Office Word ячейки организованы по строкам и столбцам. Вы можете использовать метод <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> объекта <xref:Microsoft.Office.Interop.Word.Rows> для добавления строк в таблицу и метод <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> объекта <xref:Microsoft.Office.Interop.Word.Columns> для добавления столбцов.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Примеры настроек на уровне документа  
 Следующие примеры кода можно использовать в настройке на уровне документа. Чтобы использовать эти примеры, выполняйте их из класса `ThisDocument` в своем проекте. В этих примерах предполагается, что документ, связанный с настройкой, уже содержит по крайней мере одну таблицу.  
  
> [!IMPORTANT]  
>  Этот код выполняется только в тех проектах, которые создаются с помощью любого из следующих шаблонов проекта:  
>   
>  -   Документ Word 2013  
> -   Шаблон Word 2013  
> -   Документ Word 2010  
> -   Шаблон Word 2010  
>   
>  Если вы хотите выполнить эту задачу в проекте любого другого типа, необходимо добавить ссылку на **Microsoft.Office.Interop.Word** сборки, а затем использовать классы из этой сборки Чтобы добавить строки и столбцы в таблицы. Дополнительные сведения см. в разделе [как: целевой Office приложениям через основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Word 2010 основной сборке взаимодействия](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>Добавление строки в таблицу  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>, чтобы добавить строку в таблицу.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>Добавление столбца в таблицу  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, а затем метод <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>, чтобы сделать все столбцы одинаковой ширины.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>Примеры надстроек VSTO  
 Следующие примеры кода можно использовать в надстройке VSTO. Чтобы использовать эти примеры, выполняйте их из класса `ThisAddIn` в своем проекте. В этих примерах предполагается, что активный документ содержит хотя бы одну таблицу.  
  
> [!IMPORTANT]  
>  Этот код выполняется только в тех проектах, которые создаются с помощью шаблонов Word VSTO.  
>   
>  Если вы хотите выполнить эту задачу в проекте любого другого типа, необходимо добавить ссылку на **Microsoft.Office.Interop.Word** сборки, а затем использовать классы из этой сборки Чтобы добавить строки и столбцы в таблицы. Дополнительные сведения см. в разделе [как: целевой Office приложениям через основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) и [Word 2010 основной сборке взаимодействия](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### <a name="to-add-a-row-to-a-table"></a>Добавление строки в таблицу  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>, чтобы добавить строку в таблицу.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
#### <a name="to-add-a-column-to-a-table"></a>Добавление столбца в таблицу  
  
1.  Используйте метод <xref:Microsoft.Office.Interop.Word.Columns.Add%2A>, а затем метод <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A>, чтобы сделать все столбцы одинаковой ширины.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное создание таблицы Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Как: программное добавление текста и форматирования в ячейки таблиц Word](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Практическое руководство. Программное заполнение таблиц свойствами документа Word](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  