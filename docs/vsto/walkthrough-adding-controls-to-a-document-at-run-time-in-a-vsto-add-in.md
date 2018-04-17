---
title: 'Пошаговое руководство: Добавление элементов управления в документ во время выполнения в надстройке VSTO | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1f26a60bdbd0db2464a8ac479b7534fb63f18cea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>Пошаговое руководство. Добавление элементов управления в документ во время выполнения в надстройке VSTO
  Вы можете добавлять элементы управления в любой открытый документ Microsoft Office Word с помощью надстройки VSTO. В этом пошаговом руководстве показано, как с помощью ленты предоставить пользователям возможность добавлять <xref:Microsoft.Office.Tools.Word.Controls.Button> или <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в документ.  
  
 **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для Word 2010. Дополнительные сведения см. в разделе [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание нового проекта надстройки VSTO для Word.  
  
-   Предоставление пользовательского интерфейса для добавления элементов управления в документ.  
  
-   Добавление элементов управления в документ во время выполнения.  
  
-   Удаление элементов управления из документа.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-a-new-word-add-in-project"></a>Создание нового проекта надстройки Word  
 Начнем с создания проекта надстройки VSTO для Word  
  
#### <a name="to-create-a-new-word-vsto-add-in-project"></a>Создание нового проекта надстройки VSTO для Word  
  
1.  Создайте проект надстройки VSTO для Word с именем **WordDynamicControls**. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Добавьте ссылку на сборку **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** . Эта ссылка потребуется для программного добавления элемента управления Windows Forms в документ далее в этом пошаговом руководстве.  
  
## <a name="providing-a-ui-to-add-controls-to-a-document"></a>Предоставление пользовательского интерфейса для добавления элементов управления в документ  
 Добавьте настраиваемую вкладку на ленту Word. Пользователи могут устанавливать флажки на вкладке, чтобы добавлять элементы управления в документ.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Предоставление пользовательского интерфейса для добавления элементов управления в документ  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
2.  В диалоговом окне **Добавление нового элемента** выберите элемент **Лента (визуальный конструктор)**.  
  
3.  Измените имя новой ленты на **MyRibbon**и нажмите кнопку **Добавить**.  
  
     В конструкторе лент откроется файл **MyRibbon.cs** или **MyRibbon.vb** ; отобразятся вкладка и группа, используемые по умолчанию.  
  
4.  В конструкторе ленты щелкните группу **group1** .  
  
5.  В окне **Свойства** измените свойство **Метка** для **group1** на **Добавить элементы управления**.  
  
6.  Перетащите элемент управления **CheckBox** с вкладки **Элементы управления ленты Office** **панели элементов** в группу **group1**.  
  
7.  Щелкните **CheckBox1** , чтобы выбрать его.  
  
8.  В окне **Свойства** измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**addButtonCheckBox**|  
    |**Метка**|**Кнопка “Добавить”**|  
  
9. Добавьте второй флажок в **group1**, а затем измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**addRichTextCheckBox**|  
    |**Label**|**Добавление элемента управления форматированием текста**|  
  
10. В конструкторе лент дважды щелкните элемент **Добавить кнопку**.  
  
     Обработчик событий <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> флажка **Добавить кнопку** откроется в редакторе кода.  
  
11. Вернитесь в конструктор ленты и дважды щелкните элемент **Добавить элемент управления форматированием текста**.  
  
     Обработчик событий <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> флажка **Добавить элемент управления форматированием текста** откроется в редакторе кода.  
  
 Далее в этом пошаговом руководстве вы добавите код в эти обработчики событий для добавления и удаления элементов управления в активном документе.  
  
## <a name="adding-and-removing-controls-on-the-active-document"></a>Добавление и удаление элементов управления в активном документе  
 В коде надстройки VSTO необходимо преобразовать активный документ в <xref:Microsoft.Office.Tools.Word.Document>*T:Microsoft.Office.Tools.Word.Document* , прежде чем можно будет добавить элемент управления. В решениях Office управляемые элементы управления можно добавлять только в ведущие элементы, которые действуют как контейнеры для элементов управления. В проектах надстройки VSTO ведущие элементы могут создаваться во время выполнения с помощью метода GetVstoObject.  
  
 Добавьте в класс `ThisAddIn` методы, которые могут вызываться для добавления или удаления <xref:Microsoft.Office.Tools.Word.Controls.Button> или <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в активном документе. Далее в этом пошаговом руководстве вы будете вызывать эти методы из обработчиков событий <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> флажков на ленте.  
  
#### <a name="to-add-and-remove-controls-on-the-active-document"></a>Добавление и удаление элементов управления в активном документе  
  
1.  В **обозревателе решений**дважды щелкните файл ThisAddIn.cs или ThisAddIn.vb, чтобы открыть его в редакторе кода.  
  
2.  Добавьте следующий код в класс `ThisAddIn` . Этот код объявляет объекты <xref:Microsoft.Office.Tools.Word.Controls.Button> и <xref:Microsoft.Office.Tools.Word.RichTextContentControl> , представляющие элементы управления, которые будут добавлены в документ.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]  
  
3.  Добавьте следующий метод в класс `ThisAddIn` . Когда пользователь щелкает флажок **Добавить кнопку** на ленте, этот метод добавляет <xref:Microsoft.Office.Tools.Word.Controls.Button> в выделенный фрагмент документа, если флажок устанавливается, или удаляет <xref:Microsoft.Office.Tools.Word.Controls.Button> , если флажок снимается.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]  
  
4.  Добавьте следующий метод в класс `ThisAddIn` . Когда пользователь щелкает флажок **Добавить элемент управления форматированием текста** на ленте, этот метод добавляет <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в выделенный фрагмент документа, если флажок устанавливается, или удаляет <xref:Microsoft.Office.Tools.Word.RichTextContentControl> , если флажок снимается.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]  
  
## <a name="removing-the-button-control-when-the-document-is-saved"></a>Удаление элемента управления "Кнопка" при сохранении документа  
 Элементы управления Windows Forms не сохраняются, когда документ сохраняется, а затем закрывается. Однако оболочка ActiveX для каждого элемента управления остается в документе, и границу этой оболочки конечные пользователи могут видеть при повторном открытии документа. Существует несколько способов очистить динамически созданные элементы управления Windows Forms в надстройках VSTO. В этом пошаговом руководстве вы будете программными средствами удалять элемент управления <xref:Microsoft.Office.Tools.Word.Controls.Button> при сохранении документа.  
  
#### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Удаление элемента управления "Кнопка" при сохранении документа  
  
1.  В файле кода ThisAddIn.cs или ThisAddIn.vb добавьте в класс `ThisAddIn` следующий метод. Этот метод является обработчиком событий для события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . Если у сохраненного документа есть связанный с ним ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> , обработчик событий получает этот ведущий элемент и удаляет элемент управления <xref:Microsoft.Office.Tools.Word.Controls.Button> , если он существует.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]  
  
2.  В C# добавьте в обработчик событий `ThisAddIn_Startup` следующий код. Этот код требуется в C# для подключения обработчика событий `Application_DocumentBeforeSave` к событию <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]  
  
## <a name="adding-and-removing-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Добавление и удаление элементов управления при щелчке пользователем флажков на ленте  
 Наконец, измените обработчики событий <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> флажков, добавленных на ленту, для добавления или удаления элементов управления в документе.  
  
#### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Добавление и удаление элементов управления при щелчке пользователем флажков на ленте  
  
1.  В файле кода MyRibbon.cs или MyRibbon.vb замените созданные обработчики событий `addButtonCheckBox_Click` и `addRichTextCheckBox_Click` следующим кодом. Этот код переопределяет данные обработчики событий, задавая вызов методов `ToggleButtonOnDocument` и `ToggleRichTextControlOnDocument` , которые вы добавили в класс `ThisAddIn` ранее в этом пошаговом руководстве.  
  
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]  
  
## <a name="testing-the-solution"></a>Тестирование решения  
 Добавьте элементы управления в документ, выбрав их в настраиваемой вкладке на ленте. При сохранении документа элемент управления <xref:Microsoft.Office.Tools.Word.Controls.Button> удаляется.  
  
#### <a name="to-test-the-solution"></a>Тестирование решения  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  В активном документе нажмите клавишу ВВОД несколько раз, чтобы добавить в документ новые пустые абзацы.  
  
3.  Выделите первый абзац.  
  
4.  Перейдите на вкладку **Надстройки** .  
  
5.  В группе **Добавить элементы управления** щелкните **Добавить кнопку**.  
  
     В первом абзаце появляется кнопка.  
  
6.  Выделите последний абзац.  
  
7.  В группе **Добавить элементы управления** щелкните **Добавить элемент управления форматированием текста**.  
  
     В последний абзац добавляется элемент управления форматированием текста.  
  
8.  Сохраните документ.  
  
     Кнопка удаляется из документа.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения об элементах управления в надстройках VSTO см. в следующих статьях.  
  
-   Пример, демонстрирующий способы добавления других типов элементов управления в документ во время выполнения и повторного создания этих элементов управления при повторном открытии документа, см. в разделе "Пример динамических элементов управления в надстройке Word" по адресу [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
-   Пошаговое руководство демонстрирует, как добавить элементы управления на лист с помощью надстройки VSTO для Excel см. в разделе [Пошаговое руководство: Добавление элементов управления на лист во время выполнения в VSTO надстройки проекта](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).  
  
## <a name="see-also"></a>См. также  
 [Решения Word](../vsto/word-solutions.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Сохранение динамических элементов управления в документах Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Как: Добавление элементов управления в документы Office Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Как: Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Расширение документов Word и книг Excel в надстройках VSTO в среде выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  