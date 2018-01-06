---
title: "Как: программное сохранение документов Visio | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 946bb38d5cb79506e54206060686eac5dfc7b566
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-save-visio-documents"></a>Практическое руководство. Программное сохранение документов Visio
  Существует несколько способов сохранения документов Microsoft Office Visio.  
  
-   Сохранение изменений в существующем документе.  
  
-   Сохранение нового документа или сохранение документа с новым именем.  
  
-   Сохранение документ с заданными аргументами.  
  
 Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Document.Save](https://msdn.microsoft.com/library/office/ff766478.aspx) , метода [Microsoft.Office.Interop.Visio.Document.SaveAs](https://msdn.microsoft.com/library/office/ff765824.aspx) и метода [Microsoft.Office.Interop.Visio.Document.SaveAsEx](https://msdn.microsoft.com/library/office/ff768149.aspx) .  
  
## <a name="saving-an-existing-document"></a>Сохранение существующего документа  
  
#### <a name="to-save-a-document"></a>Сохранение документа  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Document.Save класса Microsoft.Office.Tools.Visio.Document документа, который был ранее сохранен.  
  
     Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
    > [!NOTE]  
    >  Метод Microsoft.Office.Interop.Visio.Document.Save вызывает исключение, если новый документ Visio еще не были сохранены.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Сохранение документа с новым именем  
 Используйте метод Microsoft.Office.Interop.Visio.Document.SaveAs для сохранения нового документа или документа с новым именем. Этот метод требует указания нового имени файла.  
  
#### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Сохранение активного документа Visio с новым именем  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Document.SaveAs Microsoft.Office.Tools.Visio.Document, который требуется сохранить, используя полный путь, включая имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения.  
  
     Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="saving-a-document-with-a-new-name-and-specified-arguments"></a>Сохранение документа с новым именем и заданными аргументами  
 Используйте метод Microsoft.Office.Interop.Visio.Document.SaveAsEx для сохранения документа с новым именем и задайте любые допустимые аргументы для применения к документу.  
  
#### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Сохранение документа с новым именем и заданными аргументами  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Document.SaveAsEx Microsoft.Office.Tools.Visio.Document, который требуется сохранить, используя полный путь, включая имя файла. Если файл с таким именем уже существует в этой папке, возникает исключение.  
  
     В следующем примере кода выполняется сохранение активного документа с новым именем, пометка его как доступного только для чтения и отображение этого документа в списке последних использовавшихся документов. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Для сохранения документа с новым именем каталог с именем `Test` должен быть расположен в в папке "Мои документы" (для Windows XP и более ранних версий) или в папке "Документы" (для Windows Vista).  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения о модели объектов Visio](../vsto/visio-object-model-overview.md)   
 [Как: программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Как: открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Как: программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  