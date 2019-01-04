---
title: Как выполнить Программное добавление текста и форматирования в ячейки таблиц Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50c6c1fc0b2aa06771999e512d05821099b362c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865600"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Как выполнить Программное добавление текста и форматирования в ячейки таблиц Word
  Каждая таблица представляет собой набор ячеек. Каждый отдельный объект <xref:Microsoft.Office.Interop.Word.Cell> представляет одну ячейку в таблице. Обращайтесь к каждой ячейке по ее расположению в таблице. Этот пример ссылается на ячейку, расположенную в первой строке и первом столбце таблицы, добавляет в ячейку текст и применяет форматирование.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-add-text-and-formatting-to-cells"></a>Добавление текста и форматирования в ячейки  
  
1.  Обратитесь к ячейке по ее расположению в таблице, добавьте текст в ячейку и примените форматирование.  
  
     Следующий пример кода можно использовать в настройке на уровне документа. Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Программное создание таблиц Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Практическое руководство. Программное добавление строк и столбцов в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Практическое руководство. Программное заполнение таблиц Word свойствами документа](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
