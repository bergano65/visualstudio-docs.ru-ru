---
title: "Практическое руководство. Защита частей документов с помощью элементов управления содержимым"
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
  - "элементы управления содержимым [разработка решений Office в Visual Studio], защита документов"
  - "защита документов [разработка решений Office в Visual Studio]"
  - "GroupContentControl"
  - "частичная защита документов [разработка решений Office в Visual Studio]"
  - "ограниченные разрешения [разработка решений Office в Visual Studio]"
  - "Word [разработка решений Office в Visual Studio], частичная защита документов"
  - "Word [разработка решений Office в Visual Studio], ограниченные разрешения"
ms.assetid: 50d7286a-7746-446f-8eef-06ceeadc94d0
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Практическое руководство. Защита частей документов с помощью элементов управления содержимым
  При защите части документа вы запрещаете пользователям изменять или удалять содержимое в ней.  Для защиты частей документа Microsoft Office с помощью элементов управления содержимым можно использовать несколько способов:  
  
-   можно защитить элемент управления содержимым;  
  
-   можно защитить часть документа, расположенного вне элемента управления содержимым.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> Защита элемента управления содержимым  
 Вы можете запретить пользователям изменять или удалять элемент управления содержимым, задав свойства элемента управления в проекте уровня документа во время разработки или во время выполнения.  
  
 Также можно защитить элементы управления содержимым, которые вы добавляете в документ во время выполнения с помощью проекта надстройки VSTO.  Дополнительные сведения см. в разделе [Практическое руководство. Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
#### Защита элемента управления содержимым во время разработки  
  
1.  В документе, размещенном в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], выберите элемент управления содержимым, который необходимо защитить.  
  
2.  В окне **Свойства** задайте одно или оба следующих свойства.  
  
    -   Чтобы запретить пользователям изменять элемент управления, установите для свойства **LockContents** значение **True**.  
  
    -   Чтобы запретить пользователям удалять элемент управления, установите для свойства **LockContentControl** значение **True**.  
  
3.  Нажмите кнопку **ОК**.  
  
#### Защита элемента управления содержимым во время выполнения  
  
1.  Задайте для свойства `LockContents` элемента управления содержимым значение **true**, чтобы запретить пользователям изменять элемент управления, и задайте для свойства `LockContentControl` значение **true**, чтобы запретить пользователям удалять элемент управления.  
  
     В следующем примере кода показано использование свойств <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> и <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> двух разных объектов <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в проекте на уровне документа.  Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `AddProtectedContentControls` обработчика событий `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#2)]  
  
     В следующем примере кода показано использование свойств <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> и <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> двух разных объектов <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в проекте надстройки VSTO.  Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `AddProtectedContentControls` обработчика событий `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_WordAddInDynamicControls#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#14)]  
  
## Защита части документа, расположенной вне элемента управления содержимым  
 Вы можете запретить пользователям изменять часть документа, поместив ее в <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Это полезно в следующих случаях:  
  
-   вы хотите защитить область, которая не содержит элементов управления содержимым;  
  
-   вы хотите защитить область, в которой уже есть элементы управления содержимым, но текст или другие элементы, которые необходимо защитить, расположены вне элементов управления содержимым.  
  
> [!NOTE]  
>  При создании элемента <xref:Microsoft.Office.Tools.Word.GroupContentControl>, который содержит внедренные элементы управления содержимым, такие элементы автоматически не защищаются.  Чтобы запретить пользователям изменять внедренный элемент управления, необходимо использовать свойство **LockContents** элемента управления.  
  
#### Защита области документа во время разработки  
  
1.  В документе, размещенном в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], выберите область, которую необходимо защитить.  
  
2.  На ленте перейдите на вкладку **Разработчик**.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой.  Дополнительные сведения см. в разделе [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  В группе **Элементы управления** нажмите кнопку раскрывающегося списка **группы** и щелкните **Группа**.  
  
     Объект <xref:Microsoft.Office.Tools.Word.GroupContentControl>, содержащий защищенную область, создается автоматически в классе `ThisDocument` в проекте.  Граница, представляющая элемент управления группы, видна во время разработки, но не во время выполнения.  
  
#### Защита области документа во время выполнения  
  
1.  Программными средствами выберите область, которую требуется защитить, а затем вызовите метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> для создания <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
     Следующий пример кода для проекта уровня документа добавляет текст в первый абзац документа, выделяет первый абзац и создает экземпляр <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `ProtectFirstParagraph` обработчика событий `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#1)]  
  
     Следующий пример кода для проекта надстройки VSTO добавляет текст в первый абзац активного документа, выделяет первый абзац и создает экземпляр <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `ProtectFirstParagraph` обработчика событий `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_WordAddInDynamicControls#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#15)]  
  
## См. также  
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элементы управления содержимым](../vsto/content-controls.md)   
 [Практическое руководство. Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  