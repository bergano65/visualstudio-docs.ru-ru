---
title: Программное добавление текста & форматирования в ячейки таблицы Word
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
ms.openlocfilehash: acd43c82c6dae32ef6595b2f63c06fe61f3c6168
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538051"
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
