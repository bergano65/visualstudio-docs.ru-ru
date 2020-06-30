---
title: Руководство. Программное добавление фигур в документ Visio
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: adde20bff07b54a7fb5777bd9e03a995b4fbd7df
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538064"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Руководство. Программное добавление фигур в документ Visio
  Вы можете добавлять фигуры в документ Microsoft Office Visio, извлекая образцы из набора элементов и помещая фигуры на активной странице.

 Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Documents.Add) , свойства [Microsoft.Office.Interop.Visio.Application.ActivePage](/office/vba/api/Visio.Application.ActivePage) и метода [Microsoft.Office.Interop.Visio.Page.Drop](/office/vba/api/Visio.Page.Drop) .

## <a name="add-shapes-to-a-visio-document"></a>Добавление фигур в документ Visio

### <a name="to-add-shapes-to-a-visio-document"></a>Добавление фигур в документ Visio

- В активном документе извлеките образцы из коллекции Documents.Masters и поместите фигуры в активный документ. Можно извлечь образец, используя индекс или имя образца.

     В следующем примере кода создается пустой документ Visio, который затем открывается с прикрепленным набором элементов **Основные фигуры** . Затем код извлекает несколько фигур и помещает их на активной странице.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]

## <a name="see-also"></a>См. также раздел
- [Решения Visio](../vsto/visio-solutions.md)
- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Работа с фигурами Visio](../vsto/working-with-visio-shapes.md)
- [Руководство. программное копирование и вставка фигур в документ Visio](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)
