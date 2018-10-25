---
title: 'Практическое: защита частей документов с помощью элементов управления содержимым'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: beee4dd4a67b03f278a296d4b5f129100212fd25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850364"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Практическое: защита частей документов с помощью элементов управления содержимым
  При защите части документа вы запрещаете пользователям изменять или удалять содержимое в ней. Для защиты частей документа Microsoft Office с помощью элементов управления содержимым можно использовать несколько способов:  
  
- можно защитить элемент управления содержимым;  
  
- можно защитить часть документа, расположенного вне элемента управления содержимым.  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> Защита элемента управления содержимым  
 Вы можете запретить пользователям изменять или удалять элемент управления содержимым, задав свойства элемента управления в проекте уровня документа во время разработки или во время выполнения.  
  
 Также можно защитить элементы управления содержимым, которые вы добавляете в документ во время выполнения с помощью проекта надстройки VSTO. Дополнительные сведения см. в разделе [как: Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
### <a name="to-protect-a-content-control-at-design-time"></a>Защита элемента управления содержимым во время разработки  
  
1.  В документе, размещенном в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], выберите элемент управления содержимым, который необходимо защитить.  
  
2.  В **свойства** окна, задайте одно или оба из следующих свойств:  
  
    -   Чтобы запретить пользователям изменять элемент управления, задайте **LockContents** для **True**.  
  
    -   Чтобы запретить пользователям удалять элемент управления, задайте **LockContentControl** для **True**.  
  
3.  Нажмите кнопку **ОК**.  
  
### <a name="to-protect-a-content-control-at-runtime"></a>Защита содержимого элемента управления во время выполнения  
  
1.  Задайте `LockContents` свойство элемента управления содержимым к **true** запретить пользователям изменять элемент управления, и задайте `LockContentControl` свойства **true** чтобы запретить пользователям удалять элемент управления.  
  
     В следующем примере кода показано использование свойств <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> и <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> двух разных объектов <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в проекте на уровне документа. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `AddProtectedContentControls` обработчика событий `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#2)]  
  
     В следующем примере кода показано использование свойств <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> и <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> двух разных объектов <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в проекте надстройки VSTO. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `AddProtectedContentControls` обработчика событий `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#14)]
     [!code-csharp[Trin_WordAddInDynamicControls#14](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#14)]  
  
## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Защитить часть документа, который не находится в элементе управления содержимым  
 Вы можете запретить пользователям изменять часть документа, поместив ее в <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Это полезно в следующих случаях:  
  
-   вы хотите защитить область, которая не содержит элементов управления содержимым;  
  
-   вы хотите защитить область, в которой уже есть элементы управления содержимым, но текст или другие элементы, которые необходимо защитить, расположены вне элементов управления содержимым.  
  
> [!NOTE]  
>  При создании элемента <xref:Microsoft.Office.Tools.Word.GroupContentControl>, который содержит внедренные элементы управления содержимым, такие элементы автоматически не защищаются. Чтобы запретить пользователям изменять внедренный элемент управления содержимым, используйте **LockContents** свойство элемента управления.  
  
### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Защита области документа во время разработки  
  
1.  В документе, размещенном в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], выберите область, которую необходимо защитить.  
  
2.  На ленте перейдите на вкладку **Разработчик** .  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [как: Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  В **элементов управления** щелкните **группы** кнопку раскрывающегося списка, а затем щелкните **группы**.  
  
     Объект <xref:Microsoft.Office.Tools.Word.GroupContentControl>, содержащий защищенную область, создается автоматически в классе `ThisDocument` в проекте. Во время разработки отображается граница, представляющая элемент управления группы, но есть видимая граница отсутствует во время выполнения.  
  
### <a name="to-protect-an-area-of-a-document-at-runtime"></a>Защита области документа во время выполнения  
  
1.  Программными средствами выберите область, которую требуется защитить, а затем вызовите метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> для создания <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
     Следующий пример кода для проекта уровня документа добавляет текст в первый абзац документа, выделяет первый абзац и создает экземпляр <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `ProtectFirstParagraph` обработчика событий `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb#1)]  
  
     Следующий пример кода для проекта надстройки VSTO добавляет текст в первый абзац активного документа, выделяет первый абзац и создает экземпляр <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `ProtectFirstParagraph` обработчика событий `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#15)]
     [!code-csharp[Trin_WordAddInDynamicControls#15](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#15)]  
  
## <a name="see-also"></a>См. также  
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элементы управления содержимым](../vsto/content-controls.md)   
 [Практическое: Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)  
   