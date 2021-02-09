---
title: Руководство. Программное открытие документов Visio
description: Узнайте, как можно использовать Visual Studio для программного открытия документа Visio с помощью методов Open или Опенекс.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cb24851562beec0b40a8e66a38db202745f4771e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903660"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Руководство. Программное открытие документов Visio
  Существует два метода открытия существующих Microsoft Office документов Visio: Open и Опенекс. Метод Опенекс идентичен методу Open, за исключением того, что он предоставляет аргументы, в которых вызывающий объект может указать способ открытия документа.

 Подробные сведения об объектной модели см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) и метода [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) .

## <a name="open-a-visio-document"></a>Открытие документа Visio

### <a name="to-open-a-visio-document"></a>Открытие документа Visio

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.Open` и укажите полный путь к документу Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>Открытие документа Visio с указанными аргументами

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Открытие документа Visio как закрепленного и доступного только для чтения

- Вызовите метод `Microsoft.Office.Interop.Visio.Documents.OpenEx`, укажите полный путь к документу Visio и включите аргументы, которые вы хотите использовать — в данном случае Docked и Read-only.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Документ Visio с именем `myDrawing.vsd` должен находиться в каталоге с именем `Test` в папке " *Мои документы* " (для Windows XP и более ранних версий) или в папке " *документы* " (для Windows Vista).

## <a name="see-also"></a>См. также раздел
- [Решения Visio](../vsto/visio-solutions.md)
- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Как программно создавать новые документы Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Руководство. программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Как программно сохранять документы Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)
