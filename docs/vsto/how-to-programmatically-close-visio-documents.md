---
title: Практическое руководство. Программное закрытие документов Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9059e0f066cbd1dc6ced5f11f1139d7687afacf3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597211"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Практическое руководство. Программное закрытие документов Visio
  Вы можете закрыть активный документ Microsoft Office Visio с помощью метода `Microsoft.Office.Interop.Visio.Document.Close`.

 Сведения об этом методе см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Document.Close) .

## <a name="close-the-active-document"></a>Закрыть активный документ

### <a name="to-close-the-active-document"></a>Закрытие активного документа

-   Вызовите метод `Microsoft.Office.Interop.Visio.Document.Close`, чтобы закрыть активный документ.

     Чтобы использовать в следующем примере кода, запустите его `ThisAddIn` класса в проекте надстройки VSTO для Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>См. также
- [Решения Visio](../vsto/visio-solutions.md)
- [Обзор объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Практическое руководство. Программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Практическое руководство. Открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Практическое руководство. Программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)
