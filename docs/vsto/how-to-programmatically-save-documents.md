---
title: "Практическое руководство. Программное сохранение документов"
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
  - "документы [разработка решений Office в Visual Studio], сохранение"
  - "Word [разработка решений Office в Visual Studio], сохранение документов"
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Практическое руководство. Программное сохранение документов
  Существует несколько способов сохранить документы Microsoft Office Word.  Можно сохранить документ без изменения имени документа или сохранить с новым именем.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Сохранение документа без изменения имени  
  
#### Чтобы сохранить документ, связанный с настройкой на уровне документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Save%2A> класса <xref:Microsoft.Office.Tools.Word.Document>.  Чтобы воспользоваться следующим примером кода, выполните его из класса `ThisDocument` своего проекта.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreWordAutomation#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#7)]  
  
#### Чтобы сохранить активный документ  
  
1.  Вызовите для активного документа метод <xref:Microsoft.Office.Interop.Word._Document.Save%2A>.  Чтобы воспользоваться следующим примером кода, выполните его из класса `ThisDocument` или `ThisAddIn` своего проекта.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#8)]
     [!code-vb[Trin_VstcoreWordAutomation#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#8)]  
  
 Если неизвестно, является ли документ, который требуется сохранить, активным, можно указать его по имени.  
  
#### Чтобы сохранить документ, указанный по имени  
  
1.  Укажите имя документа в качестве аргумента коллекции <xref:Microsoft.Office.Interop.Word.Documents>.  Чтобы воспользоваться следующим примером кода, выполните его из класса `ThisDocument` или `ThisAddIn` своего проекта.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#9)]
     [!code-vb[Trin_VstcoreWordAutomation#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#9)]  
  
## Сохранение документа с новым именем  
 Чтобы сохранить документ с новым именем, используйте метод SaveAs.  Можно использовать этот метод ведущего элемента <xref:Microsoft.Office.Tools.Word.Document> в проекте на уровне документа Word, либо метод собственного объекта <xref:Microsoft.Office.Interop.Word.Document> в любом проекте Word.  Этот метод требует указания нового имени файл, другие аргументы необязательны.  
  
> [!NOTE]  
>  Если метод **SaveAs**, открывающий диалоговое окно, вызывается внутри обработчика событий <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> класса `ThisDocument` и параметру *Cancel* события присваивается значение **false**, то приложение может неожиданно завершиться.  Если параметру *Cancel* присвоить значение **true**, то появится сообщение об ошибке, указывающее, что автосохранение было отключено.  
  
#### Чтобы сохранить с новым именем документ, связанный с настройкой уровня документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> класса `ThisDocument` своего проекта, указав полный путь к документу.  Если файл с указанным именем уже существует в папке, он будет перезаписан без запроса подтверждения.  Чтобы воспользоваться этим примером кода, запустите его из класса `ThisDocument`.  
  
    > [!NOTE]  
    >  Метод <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> вызовет исключение, если каталог назначения не существует или при сохранении файла встретились другие проблемы.  Рекомендуется заключать метод <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> или вызывающий его метод в блок **try…catch**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#10)]  
  
#### Чтобы сохранить обычный документ с новым именем  
  
1.  Вызовите метод <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> сохраняемого документа <xref:Microsoft.Office.Interop.Word.Document>, указав полный путь к документу.  Если файл с указанным именем уже существует в папке, он будет перезаписан без запроса подтверждения.  
  
     В приведенном ниже примере кода активный документ сохраняется с новым именем.  Чтобы воспользоваться следующим примером кода, выполните его из класса `ThisDocument` или `ThisAddIn` своего проекта.  
  
    > [!NOTE]  
    >  Метод <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> вызовет исключение, если каталог назначения не существует или при сохранении файла встретились другие проблемы.  Рекомендуется заключать метод <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> или вызывающий его метод в блок **try…catch**.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Компиляция кода  
 Для выполнения этого примера кода требуется следующее:  
  
-   Чтобы сохранить документ с прежним именем, на диске C в каталоге Test должен существовать документ NewDocument.doc.  
  
-   Чтобы сохранить документ с новым именем, на диске C должен существовать каталог с именем Test.  
  
## См. также  
 [Практическое руководство. Программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)   
 [Практическое руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  