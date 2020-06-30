---
title: Руководство. Программная проверка орфографии в документах
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93ba9d9907135952f7408652bfb36f440d23138d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537856"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Руководство. Программная проверка орфографии в документах
  Чтобы проверить правописание в документе, используйте <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> метод. Этот метод возвращает логическое значение, указывающее, правильно ли написано указанный параметр.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Проверка орфографии и отображение результатов в окне сообщения

1. Вызовите <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> метод и передайте ему диапазон текста для проверки орфографических ошибок. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>См. также раздел
- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)
