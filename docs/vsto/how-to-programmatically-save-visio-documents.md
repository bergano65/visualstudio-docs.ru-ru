---
title: "Практическое руководство. Программное сохранение документов Visio | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "документы [разработка решений Office в Visual Studio], сохранение документов Visio"
  - "Visio [разработка решений Office в Visual Studio], сохранение документов Visio"
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Практическое руководство. Программное сохранение документов Visio
  Существует несколько способов сохранения документов Microsoft Office Visio.  
  
-   Сохранение изменений в существующем документе.  
  
-   Сохранение нового документа или сохранение документа с новым именем.  
  
-   Сохранение документ с заданными аргументами.  
  
 Дополнительные сведения см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Document.Save](HV10071468), метода [Microsoft.Office.Interop.Visio.Document.SaveAs](HV10071469) и метода [Microsoft.Office.Interop.Visio.Document.SaveAsEx](HV10071470).  
  
## Сохранение существующего документа  
  
#### Сохранение документа  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Document.Save класса Microsoft.Office.Tools.Visio.Document документа, который был ранее сохранен.  
  
     Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
    > [!NOTE]  
    >  Метод Microsoft.Office.Interop.Visio.Document.Save вызывает исключение, если новый документ Visio еще не был сохранены.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
## Сохранение документа с новым именем  
 Используйте метод Microsoft.Office.Interop.Visio.Document.SaveAs для сохранения нового документа или документа с новым именем. Этот метод требует указания нового имени файла.  
  
#### Сохранение активного документа Visio с новым именем  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Document.SaveAs документа Microsoft.Office.Tools.Visio.Document, который требуется сохранить, используя полный путь, включающий имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения.  
  
     Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Сохранение документа с новым именем и заданными аргументами  
 Используйте метод Microsoft.Office.Interop.Visio.Document.SaveAsEx, чтобы сохранить документ с новым именем, и задайте любые допустимые аргументы для применения к документу.  
  
#### Сохранение документа с новым именем и заданными аргументами  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Document.SaveAsEx документа Microsoft.Office.Tools.Visio.Document, который требуется сохранить, используя полный путь, включающий имя файла. Если файл с таким именем уже существует в этой папке, возникает исключение.  
  
     В следующем примере кода выполняется сохранение активного документа с новым именем, пометка его как доступного только для чтения и отображение этого документа в списке последних использовавшихся документов. Чтобы использовать этот пример кода, запустите его из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Для сохранения документа с новым именем каталог с именем `Test` должен быть расположен в в папке "Мои документы" \(для Windows XP и более ранних версий\) или в папке "Документы" \(для Windows Vista\).  
  
## См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения об объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Практическое руководство. Программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Практическое руководство. Программное открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Практическое руководство. Программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Практическое руководство. Программная печать документов Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  