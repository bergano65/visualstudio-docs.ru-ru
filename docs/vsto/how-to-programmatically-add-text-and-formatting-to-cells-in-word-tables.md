---
title: Программное добавление текста & форматирования в ячейки таблицы Word
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c0dc63c96669848703f3c18554100841a9f6c9cb
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585370"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Руководство. Программное добавление текста и форматирования в ячейки в таблицах Word
  Каждая таблица представляет собой набор ячеек. Каждый отдельный объект <xref:Microsoft.Office.Interop.Word.Cell> представляет одну ячейку в таблице. Обращайтесь к каждой ячейке по ее расположению в таблице. Этот пример ссылается на ячейку, расположенную в первой строке и первом столбце таблицы, добавляет в ячейку текст и применяет форматирование.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Добавление текста и форматирования в ячейки

1. Обратитесь к ячейке по ее расположению в таблице, добавьте текст в ячейку и примените форматирование.

     Следующий пример кода можно использовать в настройке на уровне документа. Чтобы использовать этот пример, запустите код из класса `ThisDocument` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]

     Следующий пример кода можно использовать в надстройке VSTO. В этом примере используется активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]

## <a name="see-also"></a>См. также
- [Руководство. Программное создание таблиц Word](../vsto/how-to-programmatically-create-word-tables.md)
- [Как программно добавлять строки и столбцы в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Руководство. Программное заполнение таблиц Word свойствами документа](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
