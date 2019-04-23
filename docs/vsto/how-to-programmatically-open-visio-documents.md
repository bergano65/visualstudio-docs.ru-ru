---
title: Практическое руководство. Открытие документов Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b863040bcceb4e86aae7ed4efd83c2466eec12c6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60037859"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Практическое руководство. Открытие документов Visio
  Существует два метода для открытия существующих документов Microsoft Office Visio: Откройте и OpenEx. Метод OpenEx идентична метод Open, за исключением того, что предоставляет аргументы, в которых вызывающий может указать параметры открытия документа.

 Подробные сведения об объектной модели см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) и метода [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) .

## <a name="open-a-visio-document"></a>Открытие документа Visio

### <a name="to-open-a-visio-document"></a>Открытие документа Visio

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.Open` и укажите полный путь к документу Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>Открытие документа Visio с заданными аргументами

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Открытие документа Visio как закрепленного и доступного только для чтения

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.OpenEx`, укажите полный путь к документу Visio и включите аргументы, которые вы хотите использовать — в данном случае Docked и Read-only.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Документ Visio с именем `myDrawing.vsd` должен быть расположен в каталоге с именем `Test` в *Мои документы* папки (для Windows XP и более ранних версий) или *документов* папки (для Windows Vista).

## <a name="see-also"></a>См. также
- [Решения Visio](../vsto/visio-solutions.md)
- [Обзор объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Практическое руководство. Программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Практическое руководство. Программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Практическое руководство. Программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)
