---
title: Как выполнить Программное сохранение документов Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cd49be6f7ab4e87f0592470e1c5af6039a5f56aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865626"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Как выполнить Программное сохранение документов Visio
  Существует несколько способов сохранения документов Microsoft Office Visio.  
  
- Сохранение изменений в существующем документе.  
  
- Сохранение нового документа или сохранение документа с новым именем.  
  
- Сохранение документ с заданными аргументами.  
  
  Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) , метода [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) и метода [Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) .  
  
## <a name="save-an-existing-document"></a>Сохранение существующего документа  
  
### <a name="to-save-a-document"></a>Сохранение документа  
  
-   Вызовите метод `Microsoft.Office.Interop.Visio.Document.Save` класса `Microsoft.Office.Tools.Visio.Document` документа, который был ранее сохранен.  
  
     Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
    > [!NOTE]  
    >  Метод `Microsoft.Office.Interop.Visio.Document.Save` вызывает исключение, если новый документ Visio еще не был сохранены.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>Сохранение документа с новым именем  
 Используйте метод `Microsoft.Office.Interop.Visio.Document.SaveAs` для сохранения нового документа или документа с новым именем. Этот метод требует указания нового имени файла.  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Сохранение активного документа Visio с новым именем  
  
-   Вызовите метод `Microsoft.Office.Interop.Visio.Document.SaveAs` документа `Microsoft.Office.Tools.Visio.Document`, который требуется сохранить, используя полный путь, включающий имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения.  
  
     Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Сохранение документа с новым именем и заданными аргументами  
 Используйте метод `Microsoft.Office.Interop.Visio.Document.SaveAsEx`, чтобы сохранить документ с новым именем, и задайте любые допустимые аргументы для применения к документу.  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Сохранение документа с новым именем и заданными аргументами  
  
-   Вызовите метод `Microsoft.Office.Interop.Visio.Document.SaveAsEx` документа `Microsoft.Office.Tools.Visio.Document`, который требуется сохранить, используя полный путь, включающий имя файла. Если файл с таким именем уже существует в этой папке, возникает исключение.  
  
     В следующем примере кода выполняется сохранение активного документа с новым именем, пометка его как доступного только для чтения и отображение этого документа в списке последних использовавшихся документов. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Для сохранения документа с новым именем, каталог с именем `Test` должен быть расположен в *Мои документы* папки (для Windows XP и более ранних версий) или *документов* папки (для Windows Vista).  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Обзор объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Практическое руководство. Программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Практическое руководство. Открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Практическое руководство. Программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
