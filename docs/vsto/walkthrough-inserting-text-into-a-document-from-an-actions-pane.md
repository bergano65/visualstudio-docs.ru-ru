---
title: "Пошаговое руководство: Вставка текста в документ из панели действий | Документы Microsoft"
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
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 789ad22524a5c0128320bfb833b8ad97e294a86f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-inserting-text-into-a-document-from-an-actions-pane"></a>Пошаговое руководство. Вставка текста в документ из панели действий
  В этом пошаговом руководстве показано, как создать панель действий в документ Microsoft Office Word. Панель действий содержит два элемента управления для сбора входных данных и затем отправить текст в документ.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Разработка интерфейса с помощью элементов управления Windows Forms в элемент управления панели действий.  
  
-   Отображение панели действий при открытии приложения.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Создание проекта  
 Первым шагом является создание документа Word.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект документа Word с именем **Моя базовая панель действий**. В мастере выберите **создания документа**. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет новый документ Word в конструкторе и добавляет **Моя базовая панель действий** проекта **обозревателе решений**.  
  
## <a name="adding-text-and-bookmarks-to-the-document"></a>Добавление текста и закладок в документ  
 Панель действий будет посылать текст в закладки в документе. Чтобы создать документ, введите текст для создания базовой форме.  
  
#### <a name="to-add-text-to-your-document"></a>Добавление текста в документ  
  
1.  Введите следующий текст в документ Word:  
  
     **21 марта 2008 г.**  
  
     **Name**  
  
     **Адрес**  
  
     **Это пример базовой панели действий в Word.**  
  
 Можно добавить <xref:Microsoft.Office.Tools.Word.Bookmark> управления в документ, перетащив его из **элементов** в Visual Studio или с помощью **закладки** диалоговое окно в Word.  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>Добавление элемента управления Bookmark в документ  
  
1.  Из **элементы управления Word** вкладке **элементов**, перетащите <xref:Microsoft.Office.Tools.Word.Bookmark> элемент управления.  
  
     **Добавление элемента управления Bookmark** откроется диалоговое окно.  
  
2.  Выделите слово **имя**, без выберите знак абзаца и нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  Знак абзаца должно находиться за пределами закладки. Если знаки абзаца в документе не отображаются, щелкните **средства** последовательно выберите пункты **средства Microsoft Office Word** и нажмите кнопку **параметры**. Нажмите кнопку **представление** и выберите **знаки абзаца** флажок в **знаки форматирования** раздел **параметры** диалоговое окно.  
  
3.  В **свойства** измените **имя** свойство **Bookmark1** для **showName**.  
  
4.  Выделите слово **адрес**, не выбирая знак абзаца.  
  
5.  На **вставить** ленты в **ссылки** щелкните **закладку**.  
  
6.  В **закладки** диалоговом **showAddress** в **имя закладки** и нажмите кнопку **добавить**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Добавление элементов управления в панели действий  
 Для разработки интерфейса панели действий, добавьте элемент управления панели действий в проект и затем добавить элементы управления Windows Forms в элемент управления панели действий.  
  
#### <a name="to-add-an-actions-pane-control"></a>Чтобы добавить элемент управления панели действий  
  
1.  Выберите **Моя базовая панель действий** проекта в **обозревателе решений**.  
  
2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
3.  В **Добавление нового элемента** диалоговое окно, нажмите кнопку **управления панели действий**, имя элемента управления **InsertTextControl,** и нажмите кнопку **добавить**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Добавление элементов управления Windows Forms в элемент управления панели действий  
  
1.  Если элемент управления не виден в конструкторе, дважды щелкните **InsertTextControl**.  
  
2.  Из **стандартные элементы управления** вкладке **элементов**, перетащите **метка** элемента управления к элементу управления панели действий.  
  
3.  Изменение **текст** свойства для элемента управления метка **имя**.  
  
4.  Добавить **Textbox** управления к элементу управления панели действий и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**getName**|  
    |**Size**|**130, 20**|  
  
5.  Добавьте второй **метка** управления к элементу управления панели действий и измените **текст** свойства **адрес**.  
  
6.  Добавьте второй **Textbox** управления к элементу управления панели действий и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**getAddress**|  
    |**Принимает возврата**|**True**|  
    |**Multiline**|**True**|  
    |**Size**|**130, 40**|  
  
7.  Добавить **кнопку** управления к элементу управления панели действий и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**addText**|  
    |**Text**|**Вставить**|  
  
## <a name="adding-code-to-insert-text-into-the-document"></a>Добавление кода для вставки текста в документ  
 В области действия написать код, который вставляет текст из поля в соответствующие <xref:Microsoft.Office.Tools.Word.Bookmark> элементов управления в документе. Можно использовать `Globals` класса для доступа к элементам управления в документе из элементов управления в панели действий. Дополнительные сведения см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Вставить текст из области действия в закладки в документе  
  
1.  Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий **addText** кнопки.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  В C# необходимо добавить обработчик событий для нажатия кнопки. Можно заменить этот код в `InsertTextControl` конструктор после вызова `IntializeComponent`. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="adding-code-to-show-the-actions-pane"></a>Добавление кода для отображения панели «действия»  
 Чтобы отобразить панель действий, добавьте элемент управления, созданный в коллекцию элементов управления.  
  
#### <a name="to-show-the-actions-pane"></a>Чтобы отобразить панель действий  
  
1.  Создать новый экземпляр элемента управления панели действий в `ThisDocument` класса.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Добавьте следующий код в <xref:Microsoft.Office.Tools.Word.Document.Startup> обработчик событий `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Проверьте документ, чтобы убедиться, что панель действий открывается при открытии документа и что текст, вводимый в текстовые поля вставляется в закладки, при нажатии кнопки.  
  
#### <a name="to-test-your-document"></a>Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Убедитесь, что панель действий становится видимой.  
  
3.  Введите имя и адрес в текстовые поля в панели действий и нажмите кнопку **вставить**.  
  
## <a name="next-steps"></a>Следующие шаги  
 Ниже приводятся некоторые из возможных последующих задач.  
  
-   Создание панели действий в Excel. Дополнительные сведения см. в разделе [как: Добавление панели действий к книгам Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Привязка данных к элементам управления в панели действий. Дополнительные сведения см. в разделе [Пошаговое руководство: привязка данных к элементам управления в панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о панели действий](../vsto/actions-pane-overview.md)   
 [Как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Как: Добавление панели действий для книг Excel](http://msdn.microsoft.com/en-us/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Как: Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Элемент управления Bookmark](../vsto/bookmark-control.md)  
  
  