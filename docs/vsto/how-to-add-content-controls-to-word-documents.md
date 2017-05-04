---
title: "Практическое руководство. Добавление элементов управления содержимым в документы Word | Microsoft Docs"
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
  - "ограниченные разрешения [разработка решений Office в Visual Studio]"
  - "DropDownListContentControl, добавление к документам"
  - "BuildingBlockGalleryContentControl, добавление к документам"
  - "частичная защита документов [разработка решений Office в Visual Studio]"
  - "RichTextContentControl, добавление к документам"
  - "Word [разработка решений Office в Visual Studio], частичная защита документов"
  - "Элементы управления содержимым [разработка решений Office в Visual Studio], защита"
  - "PictureContentControl, добавление к документам"
  - "GroupContentControl, добавление к документам"
  - "защита документов [разработка решений Office в Visual Studio]"
  - "PlainTextContentControl, добавление к документам"
  - "Элементы управления содержимым [разработка решений Office в Visual Studio], добавление"
  - "ComboBoxContentControl, добавление к документам"
  - "DatePickerContentControl, добавление к документам"
  - "Word [разработка решений Office в Visual Studio], ограниченные разрешения "
ms.assetid: 68ddb24e-71c6-46f7-8e11-c9899d7814df
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Практическое руководство. Добавление элементов управления содержимым в документы Word
  В проектах на уровне документа Word элементы управления содержимым можно добавлять в документ во время разработки или во время выполнения. В проектах надстройки VSTO для Word элементы управления содержимым можно добавлять в любой открытый документ во время выполнения.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 В этом разделе описываются следующие задачи.  
  
-   [Добавление элементов управления содержимым во время разработки.](#designtime)  
  
-   [Добавление элементов управления содержимым во время выполнения в проекте на уровне документа.](#runtimedoclevel)  
  
-   [Добавление элементов управления содержимым во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
 Сведения об элементах управления содержимым см. в разделе [Элементы управления содержимым](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Добавление элементов управления содержимым во время разработки  
 Вы можете добавить элементы управления содержимым в документ Word в проекте на уровне документа во время разработки несколькими способами.  
  
-   Добавьте элемент управления содержимым из вкладки **Элементы управления Wordпанели элементов**.  
  
-   Добавьте элемент управления содержимым в документ так же, как вы добавляете управляемый элемент управления содержимым в Word.  
  
-   Перетащите элемент управления в документ из окна **Источники данных**. Это полезно, если нужно одновременно привязать элемент управления к данным при его создании. Дополнительные сведения см. в разделах [Практическое руководство. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md) и [Практическое руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Добавление элемента управления содержимым в документ с помощью панели элементов  
  
1.  В документе, который размещен в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], поместите курсор там, где необходимо добавить элемент управления содержимым, или выделите текст, который заменит элемент управления содержимым.  
  
2.  Откройте **панель элементов** и щелкните вкладку **Элементы управления Word**.  
  
3.  Добавьте элемент управления одним из следующих способов.  
  
    -   Дважды щелкните элемент управления содержимым в **панели элементов**.  
  
         или  
  
    -   Щелкните элемент управления содержимым в **панели элементов** и нажмите клавишу ВВОД.  
  
         или  
  
    -   Перетащите элемент управления содержимым из **панели элементов** в документ. Элемент управления содержимым добавляется в текущее выделение в документе, а не в позиции указателя мыши.  
  
> [!NOTE]  
>  Невозможно добавить <xref:Microsoft.Office.Tools.Word.GroupContentControl> с помощью **панели элементов**.<xref:Microsoft.Office.Tools.Word.GroupContentControl> можно добавлять только в Word или во время выполнения.  
  
> [!NOTE]  
>  Visual Studio не предоставляет элемент управления содержимым «Флажок» в панели элементов. Чтобы добавить элемент управления содержимым «Флажок» в документ, необходимо создать <xref:Microsoft.Office.Tools.Word.ContentControl> программно. Для получения дополнительной информации см. [Элементы управления содержимым](../vsto/content-controls.md).  
  
#### Добавление элемента управления содержимым «Флажок» в документ из Word  
  
1.  В документе, который размещен в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], поместите курсор там, где необходимо добавить элемент управления содержимым, или выделите текст, который заменит элемент управления содержимым.  
  
2.  На ленте перейдите на вкладку **Разработчик**.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Для получения дополнительной информации см. [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  В группе **Элементы управления** щелкните значок элемента управления содержимым, который требуется добавить.  
  
##  <a name="runtimedoclevel"></a> Добавление элементов управления содержимым во время выполнения в проекте на уровне документа  
 Элементы управления содержимым можно добавить в документ программным образом во время выполнения с помощью методов свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> класса `ThisDocument` в проекте. У каждого метода есть три перегрузки, которые можно использовать для добавления элемента управления содержимым следующими способами:  
  
-   добавление элемента управления в текущее выделение;  
  
-   добавление элемента управления в указанный диапазон;  
  
-   добавление элемента управления, основанного на управляемом элементе управления содержимым, в документ.  
  
 При закрытии документа динамически созданные элементы управления содержимым не сохраняются в документе. Однако неуправляемый элемент управления содержимым остается в документе. Можно повторно создать элемент управления содержимым, основанный на управляемом элементе управления содержимым, при очередном открытии документа. Для получения дополнительной информации см. [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Чтобы добавить элемент управления содержимым «Флажок» в документ в проекте Word 2010, необходимо создать объект <xref:Microsoft.Office.Tools.Word.ContentControl>. Для получения дополнительной информации см. [Элементы управления содержимым](../vsto/content-controls.md).  
  
#### Добавление элемента управления содержимым в текущее выделение  
  
1.  Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection> с именем `Add`\<*класс элемента управления*\> \(где *класс элемента управления* — это имя класса элемента управления содержимым, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) и одним параметром для имени нового элемента управления.  
  
     Следующий пример кода использует метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>, чтобы добавить новый <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в начало документа. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `AddRichTextControlAtSelection` обработчика событий `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlReference#700](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#700)]  
  
#### Добавление элемента управления в указанный диапазон  
  
1.  Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection> с именем `Add`\<*класс элемента управления*\> \(где *класс элемента управления* — это имя класса элемента управления содержимым, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) и параметром <xref:Microsoft.Office.Interop.Word.Range>.  
  
     Следующий пример кода использует метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>, чтобы добавить новый <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в начало документа. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `AddRichTextControlAtRange` обработчика событий `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlReference#701](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#701)]  
  
#### Добавление элемента управления содержимым, основанного на управляемом элементе управления содержимым  
  
1.  Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection> с именем `Add`\<*класс элемента управления*\> \(где *класс элемента управления* — это имя класса элемента управления содержимым, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) и параметром Microsoft.Office.Interop.Word.ContentControl.  
  
     В следующем примере кода метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> используется для создания нового объекта <xref:Microsoft.Office.Tools.Word.RichTextContentControl> для каждого управляемого элемента управления форматированием текста, который есть в документе. Для выполнения этого кода добавьте код в класс `ThisDocument` в проекте и вызовите метод `CreateRichTextControlsFromNativeControls` обработчика событий `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlReference#702](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Добавление элементов управления содержимым во время выполнения в проекте надстройки VSTO  
 Вы можете добавить элементы управления содержимым программным способом в любой открытый документ во время выполнения с помощью надстройки VSTO. Для этого следует создать ведущий элемент <xref:Microsoft.Office.Tools.Word.Document>, основанный на открытом документе, а затем использовать методы свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> этого ведущего элемента. У каждого метода есть три перегрузки, которые можно использовать для добавления элемента управления содержимым следующими способами:  
  
-   добавление элемента управления в текущее выделение;  
  
-   добавление элемента управления в указанный диапазон;  
  
-   добавление элемента управления, основанного на управляемом элементе управления содержимым, в документ.  
  
 При закрытии документа динамически созданные элементы управления содержимым не сохраняются в документе. Однако неуправляемый элемент управления содержимым остается в документе. Можно повторно создать элемент управления содержимым, основанный на управляемом элементе управления содержимым, при очередном открытии документа. Дополнительные сведения см. в разделе [Сохранение динамических элементов управления в документах Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Дополнительные сведения о создании ведущих элементов в проекте надстройки VSTO см. в разделе [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Чтобы добавить элемент управления содержимым «Флажок», необходимо создать объект <xref:Microsoft.Office.Tools.Word.ContentControl>. Дополнительные сведения см. в разделе [Элементы управления содержимым](../vsto/content-controls.md).  
  
#### Добавление элемента управления содержимым в текущее выделение  
  
1.  Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection> с именем `Add`\<*класс элемента управления*\> \(где *класс элемента управления* — это имя класса элемента управления содержимым, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) и одним параметром для имени нового элемента управления.  
  
     Следующий пример кода использует метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>, чтобы добавить новый <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в начало активного документа. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `AddRichTextControlAtSelection` обработчика событий `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
#### Добавление элемента управления в указанный диапазон  
  
1.  Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection> с именем `Add`\<*класс элемента управления*\> \(где *класс элемента управления* — это имя класса элемента управления содержимым, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) и параметром <xref:Microsoft.Office.Interop.Word.Range>.  
  
     Следующий пример кода использует метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>, чтобы добавить новый <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в начало активного документа. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте и вызовите метод `AddRichTextControlAtRange` обработчика событий `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
#### Добавление элемента управления содержимым, основанного на управляемом элементе управления содержимым  
  
1.  Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection> с именем `Add`\<*класс элемента управления*\> \(где *класс элемента управления* — это имя класса элемента управления содержимым, который требуется добавить, например <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) и параметром Microsoft.Office.Interop.Word.ContentControl.  
  
     В следующем примере кода метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> используется для создания нового объекта <xref:Microsoft.Office.Tools.Word.RichTextContentControl> для каждого управляемого элемента управления форматированием текста в документе после его открытия. Для выполнения этого кода добавьте код в класс `ThisAddIn` в проекте.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
     Для C\# необходимо присоединить обработчик `Application_DocumentOpen` к событию <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#6)]  
  
## См. также  
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Настройки программирования уровня документа](../vsto/programming-document-level-customizations.md)  
  
  