---
title: 'Практическое: Добавление элементов управления Bookmark в документы Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f07fc3534c7963beda0d08d4ebf659979731d7f
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674445"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Практическое: Добавление элементов управления Bookmark в документы Word
  В проектах уровня документа, можно добавить <xref:Microsoft.Office.Tools.Word.Bookmark> элементы управления в документ в проекте во время разработки или во время выполнения. В проектах надстройки VSTO можно добавить <xref:Microsoft.Office.Tools.Word.Bookmark> элементов управления в любой открытый документ во время выполнения.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 В этом разделе описываются следующие задачи.  
  
-   [Добавление элементов управления Bookmark во время разработки](#designtime)  
  
-   [Добавление элементов управления Bookmark во время выполнения в проекте уровня документа](#runtimedoclevel)  
  
-   [Добавление элементов управления Bookmark во время выполнения в проекте надстройки VSTO](#runtimeaddin)  
  
 Дополнительные сведения о <xref:Microsoft.Office.Tools.Word.Bookmark> элементов управления, см. в разделе [элемент управления Bookmark](../vsto/bookmark-control.md).  
  
##  <a name="designtime"></a> Добавление элементов управления Bookmark во время разработки  
 Вы можете добавить элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документ Word в проекте на уровне документа во время разработки несколькими способами.  
  
-   Из **панели элементов**Visual Studio.  
  
     Вы можете перетащить элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> из области **Панель элементов** в документ. Этот способ удобен, если вы уже используете **панель элементов** для добавления элементов управления Windows Forms в документ.  
  
-   Из приложения Word.  
  
     Вы можете добавить элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документ так же, как и закладку. Преимущество этого способа заключается в том, что вы можете задать имя элемента управления во время его создания.  
  
-   Из окна **Источники данных** .  
  
     Вы можете перетащить элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> из окна **Источники данных** . Это удобно, если нужно одновременно привязать элемент управления к данным. Можно добавить элемент управления ведущего приложения так же, как вы добавляете элемент управления Windows Form из окна **Источники данных** . Дополнительные сведения см. в разделе [привязка данных и Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Добавление элемента управления Bookmark в документ из панели элементов  
  
1.  Откройте **панель элементов** и щелкните вкладку **Элементы управления Word** .  
  
2.  Перетащите элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документ.  
  
     Отображается диалоговое окно **Добавление закладки** .  
  
3.  Выберите текст или другие элементы, которые необходимо включить в закладку.  
  
4.  Нажмите кнопку **ОК**.  
  
     Если вы не хотите использовать имя закладки по умолчанию, измените его в окне **Свойства** .  
  
#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Добавление элемента управления Bookmark в документ из Word  
  
1.  В документе, который размещен в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , поместите курсор туда, куда необходимо добавить закладку, или выделите текст, который требуется добавить в закладку.  
  
2.  На вкладке **Вставка** ленты в группе **Ссылки** нажмите кнопку **Закладка** .  
  
3.  В диалоговом окне **Закладка** введите имя новой закладки и нажмите кнопку **Добавить**.  
  
##  <a name="runtimedoclevel"></a> Добавление элементов управления Bookmark во время выполнения в проекте уровня документа  
 Вы можете добавить <xref:Microsoft.Office.Tools.Word.Bookmark> управляет программным способом в документ во время выполнения с помощью методов класса <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> свойство `ThisDocument` в своем проекте. Существуют две перегрузки метода, которые можно использовать для добавления элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> следующими способами:  
  
-   добавление <xref:Microsoft.Office.Tools.Word.Bookmark> в указанный диапазон;  
  
-   добавление <xref:Microsoft.Office.Tools.Word.Bookmark> , основанного на собственной закладке, в документ (т. е. <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
 При закрытии документа динамически созданные элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в нем не сохраняются. Однако собственный объект <xref:Microsoft.Office.Interop.Word.Bookmark> остается в документе. Можно повторно создать <xref:Microsoft.Office.Tools.Word.Bookmark> , основанный на собственной закладке, при очередном открытии документа. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Добавление элемента управления Bookmark в документ программными средствами  
  
1.  Вставьте следующий код в обработчике событий `ThisDocument_Startup` в проекте, чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> в первый абзац документа.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Если необходимо создать элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> на основе существующего <xref:Microsoft.Office.Interop.Word.Bookmark>, используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> и передайте его в существующий <xref:Microsoft.Office.Interop.Word.Bookmark>.  
  
##  <a name="runtimeaddin"></a> Добавление элементов управления Bookmark во время выполнения в проекте надстройки VSTO  
 Вы можете добавить <xref:Microsoft.Office.Tools.Word.Bookmark> элементы управления программным способом в любой открытый документ во время выполнения с помощью надстройки VSTO. Для этого следует создать ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> , основанный на открытом документе, а затем использовать методы свойства <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> этого ведущего элемента. Существуют две перегрузки метода, которые можно использовать для добавления элемента управления <xref:Microsoft.Office.Tools.Word.Bookmark> следующими способами:  
  
-   добавление <xref:Microsoft.Office.Tools.Word.Bookmark> в указанный диапазон;  
  
-   добавление <xref:Microsoft.Office.Tools.Word.Bookmark> , основанного на собственной закладке, в документ (т. е. <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
 При закрытии документа динамически созданные элементы управления <xref:Microsoft.Office.Tools.Word.Bookmark> в нем не сохраняются. Однако собственный объект <xref:Microsoft.Office.Interop.Word.Bookmark> остается в документе. Можно повторно создать <xref:Microsoft.Office.Tools.Word.Bookmark> , основанный на собственной закладке, при очередном открытии документа. Дополнительные сведения см. в разделе [сохранение динамических элементов управления в документы Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Дополнительные сведения о создании ведущих элементов в проектах надстройки VSTO, см. в разделе [документов расширения Word и книг Excel в надстройках VSTO во время выполнения](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Добавление элемента управления Bookmark в указанный диапазон  
  
1.  Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> и передайте ему объект <xref:Microsoft.Office.Interop.Word.Range> , в который вы хотите добавить <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Следующий пример кода добавляет новый <xref:Microsoft.Office.Tools.Word.Bookmark> в начало активного документа. Чтобы использовать этот пример, запустите его из обработчика событий `ThisAddIn_Startup` в проекте надстройки VSTO Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]  
  
#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Добавление элемента управления Bookmark, основанного на собственном элементе управления Bookmark  
  
1.  Используйте метод <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> и передайте ему существующий объект <xref:Microsoft.Office.Interop.Word.Bookmark> , который будет использоваться в качестве основы для нового <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     В следующем примере кода создается новый объект <xref:Microsoft.Office.Tools.Word.Bookmark> , основанный на первом объекте <xref:Microsoft.Office.Interop.Word.Bookmark> в активном документе. Чтобы использовать этот пример, запустите его из обработчика событий `ThisAddIn_Startup` в проекте надстройки VSTO Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]  
  
## <a name="see-also"></a>См. также  
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md)   
 [Практическое: изменение размера элементов управления Bookmark](../vsto/how-to-resize-bookmark-controls.md)  
  
  