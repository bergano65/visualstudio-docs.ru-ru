---
title: Руководство. программное закрытие документов Visio
description: Узнайте, как можно закрыть активный Microsoft Office документ Visio с помощью Microsoft.Office.Interop.Visio.Docумент. Метод Close.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c1592bd500103a2db42934ab8f81392a5f1fa0d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903688"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Руководство. программное закрытие документов Visio
  Вы можете закрыть активный документ Microsoft Office Visio с помощью метода `Microsoft.Office.Interop.Visio.Document.Close`.

 Сведения об этом методе см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Document.Close) .

## <a name="close-the-active-document"></a>Закрыть активный документ

### <a name="to-close-the-active-document"></a>Закрытие активного документа

- Вызовите метод `Microsoft.Office.Interop.Visio.Document.Close`, чтобы закрыть активный документ.

     Чтобы использовать следующий пример кода, запустите его в `ThisAddIn` классе в проекте надстройки VSTO для Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>См. также раздел
- [Решения Visio](../vsto/visio-solutions.md)
- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Как программно создавать новые документы Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Руководство. Программное открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Как программно сохранять документы Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)
