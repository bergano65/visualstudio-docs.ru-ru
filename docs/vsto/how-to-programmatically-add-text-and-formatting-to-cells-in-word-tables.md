---
title: "Как: программное добавление текста и форматирования в ячейки таблиц Word | Документы Microsoft"
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
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ed593a9d03093fa092c97ce005ca190b5c433c8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Практическое руководство. Программное добавление текста и форматирования в ячейки таблиц Word
  Каждая таблица представляет собой набор ячеек. Каждый отдельный объект <xref:Microsoft.Office.Interop.Word.Cell> представляет одну ячейку в таблице. Обращайтесь к каждой ячейке по ее расположению в таблице. Этот пример ссылается на ячейку, расположенную в первой строке и первом столбце таблицы, добавляет в ячейку текст и применяет форматирование.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-add-text-and-formatting-to-cells"></a>Добавление текста и форматирования в ячейки  
  
1.  Обратитесь к ячейке по ее расположению в таблице, добавьте текст в ячейку и примените форматирование.  
  
     Следующий пример кода можно использовать в настройке на уровне документа. Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>См. также  
 [Как: программное создание таблицы Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Как: программным образом добавить строки и столбцы в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Практическое руководство. Программное заполнение таблиц свойствами документа Word](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  