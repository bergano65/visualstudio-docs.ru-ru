---
title: "Как: программное сохранение документов | Документы Microsoft"
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
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c6a47bae9923d68acc189c53766d5206244f97c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-save-documents"></a>Практическое руководство. Программное сохранение документов
  Существует несколько способов сохранения документов Microsoft Office Word. Можно сохранить документ без изменения имени документа или сохранении документа с новым именем.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="saving-a-document-without-changing-the-name"></a>Сохранение документа без изменения имени  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Чтобы сохранить документ, связанный с помощью настройки уровня документа  
  
1.  Вызовите метод <xref:Microsoft.Office.Tools.Word.Document.Save%2A> класса <xref:Microsoft.Office.Tools.Word.Document>. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
#### <a name="to-save-the-active-document"></a>Чтобы сохранить активный документ  
  
1.  Вызовите <xref:Microsoft.Office.Interop.Word._Document.Save%2A> метод для активного документа. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 Если вы не уверены, является ли документ, который вы хотите сохранить является активным документом, в него можно ссылаться по его имени.  
  
#### <a name="to-save-a-document-specified-by-name"></a>Чтобы сохранить документ, указанный по имени  
  
1.  Укажите имя документа в качестве аргумента <xref:Microsoft.Office.Interop.Word.Documents> коллекции. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="saving-a-document-with-a-new-name"></a>Сохранение документа с новым именем  
 Метод SaveAs для сохранения документа с новым именем. Этот метод можно использовать <xref:Microsoft.Office.Tools.Word.Document> ведущего элемента в проекте уровня документа Word или собственного <xref:Microsoft.Office.Interop.Word.Document> объекта в любом проекте Word. Этот метод требует указания нового имени файла, что другие аргументы являются необязательными.  
  
> [!NOTE]  
>  При отображении **SaveAs** диалоговое окно внутри <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> обработчик событий `ThisDocument` и задайте *отменить* параметр **false**, приложение может неожиданно завершить работу. Если задать *отменить* параметр **true**, появится сообщение об ошибке, указывающее на то, что эта функция отключена.  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Чтобы сохранить документ, связанный с помощью настройки уровня документа с новым именем  
  
1.  Вызовите <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> метод `ThisDocument` класса в проекте, используя полный путь и имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` .  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> Метод создает исключение, если целевой каталог не существует или если имеются другие проблемы при сохранении файла. Рекомендуется использовать **try... catch** блока вокруг <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> метода или внутри вызывающего метода.  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
#### <a name="to-save-a-native-document-with-a-new-name"></a>Для сохранения исходного документа с новым именем  
  
1.  Вызовите <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> метод <xref:Microsoft.Office.Interop.Word.Document> , необходимо сохранить, используя полный путь и имя файла. Если файл с таким именем уже существует в этой папке, он будет перезаписан без запроса подтверждения.  
  
     В следующем примере кода Сохранение активного документа под новым именем. Чтобы использовать этот пример кода, запустите его из класса `ThisDocument` или `ThisAddIn` в своем проекте.  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Метод создает исключение, если целевой каталог не существует или если имеются другие проблемы при сохранении файла. Рекомендуется использовать **try... catch** блока вокруг <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> метода или внутри вызывающего метода.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера кода требуется следующее.  
  
-   Чтобы сохранить документ по имени, должен существовать документ NewDocument.doc в каталоге с именем Test на диске C.  
  
-   Сохранение документа с новым именем, должен существовать каталог с именем Test на диске C.  
  
## <a name="see-also"></a>См. также  
 [Как: программное закрытие документов](../vsto/how-to-programmatically-close-documents.md)   
 [Как: Открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Ведущий элемент документа](../vsto/document-host-item.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  