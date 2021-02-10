---
title: Как программно сохранять документы Visio
description: Узнайте, как можно использовать Visual Studio для программного сохранения существующих документов и новых документов Microsoft Visio, которые еще не были сохранены.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a9d3b8e7d7e7e1a0a58dee5ceb5f1ca49753930f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947766"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Как программно сохранять документы Visio
  Существует несколько способов сохранения документов Microsoft Office Visio.

- Сохранение изменений в существующем документе.

- Сохранение нового документа или сохранение документа с новым именем.

- Сохранение документ с заданными аргументами.

  Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) , метода [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) и метода [Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) .

## <a name="save-an-existing-document"></a>Сохранение существующего документа

### <a name="to-save-a-document"></a>Сохранение документа

- Вызовите метод `Microsoft.Office.Interop.Visio.Document.Save` класса `Microsoft.Office.Tools.Visio.Document` документа, который был ранее сохранен.

     Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

    > [!NOTE]
    > Метод `Microsoft.Office.Interop.Visio.Document.Save` вызывает исключение, если новый документ Visio еще не был сохранены.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]

## <a name="save-a-document-with-a-new-name"></a>Сохранение документа с новым именем
 Используйте метод `Microsoft.Office.Interop.Visio.Document.SaveAs` для сохранения нового документа или документа с новым именем. Этот метод требует указания нового имени файла.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Сохранение активного документа Visio с новым именем

- Вызовите метод `Microsoft.Office.Interop.Visio.Document.SaveAs` документа `Microsoft.Office.Tools.Visio.Document`, который требуется сохранить, используя полный путь, включающий имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения.

     Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Сохранение документа с новым именем и указанными аргументами
 Используйте метод `Microsoft.Office.Interop.Visio.Document.SaveAsEx`, чтобы сохранить документ с новым именем, и задайте любые допустимые аргументы для применения к документу.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Сохранение документа с новым именем и заданными аргументами

- Вызовите метод `Microsoft.Office.Interop.Visio.Document.SaveAsEx` документа `Microsoft.Office.Tools.Visio.Document`, который требуется сохранить, используя полный путь, включающий имя файла. Если файл с таким именем уже существует в этой папке, возникает исключение.

     В следующем примере кода выполняется сохранение активного документа с новым именем, пометка его как доступного только для чтения и отображение этого документа в списке последних использовавшихся документов. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера кода требуется следующее.

- Чтобы сохранить документ с новым именем, каталог с именем `Test` должен находиться в папке « *Мои документы* » (для Windows XP и более ранних версий) или в папке « *документы* » (для Windows Vista).

## <a name="see-also"></a>См. также раздел
- [Решения Visio](../vsto/visio-solutions.md)
- [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)
- [Как программно создавать новые документы Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Руководство. Программное открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Руководство. программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)
