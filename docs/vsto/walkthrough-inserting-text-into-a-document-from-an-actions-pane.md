---
title: Пошаговое руководство. Вставка текста в документ из панели действий
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 55c5bc57cb419b8614c6c6055a75c633e4012d60
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634751"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Пошаговое руководство. Вставка текста в документ из панели действий
  В этом пошаговом руководстве показано, как создать панель действий в документ Microsoft Office Word. Панель действий содержит два элемента управления, которые собирают входные данные и затем отправить текст в документ.

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

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание документа Word.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1.  Создайте проект документа Word с именем **основные панель действий**. В мастере выберите **создания документа**. Дополнительные сведения см. в разделе [Как Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio открывает новый документ Word в конструкторе и добавляет **основные панель действий** проект **обозревателе решений**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Добавление текста и закладок в документ
 Панель действий будет посылать текст в закладки в документе. Чтобы создать документ, введите текст для создания простой формы.

### <a name="to-add-text-to-your-document"></a>Для добавления текста в документ

1. Введите следующий текст в документ Word:

    **21 марта 2008 г.**

    **Name**

    **Адрес**

    **Это пример базовой панели действий в Word.**

   Вы можете добавить <xref:Microsoft.Office.Tools.Word.Bookmark> элемента управления в документ, перетащив его из **элементов** в Visual Studio или с помощью **закладки** диалоговое окно в Word.

### <a name="to-add-a-bookmark-control-to-your-document"></a>Добавление элемента управления Bookmark в документ

1.  Из **элементы управления Word** вкладке **элементов**, перетащите <xref:Microsoft.Office.Tools.Word.Bookmark> элемента управления в документ.

     **Добавьте элемент управления Bookmark** откроется диалоговое окно.

2.  Выбрать слово **имя**, не выбирая знак абзаца и нажмите кнопку **ОК**.

    > [!NOTE]
    >  Знак абзаца должно находиться за пределами закладки. Если знаки абзаца в документе не отображаются, щелкните **средства** последовательно выберите пункты **средства Microsoft Office Word** и нажмите кнопку **параметры**. Нажмите кнопку **представление** и выберите **знаки абзаца** флажок в **знаки форматирования** раздел **параметры** диалоговое окно.

3.  В **свойства** измените **имя** свойство **Bookmark1** для **showName**.

4.  Выбрать слово **адрес**, не выбирая знак абзаца.

5.  На **вставить** вкладке ленты в **ссылки** щелкните **закладку**.

6.  В **закладки** диалоговом окне **showAddress** в **имя закладки** поле и нажмите кнопку **добавить**.

## <a name="add-controls-to-the-actions-pane"></a>Добавление элементов управления в панели действий
 Для проектирования интерфейса панели действий, добавьте в проект элемента управления панели действий, а затем добавьте элементы управления Windows Forms для элемента управления панели действий.

### <a name="to-add-an-actions-pane-control"></a>Чтобы добавить элемент управления панели действий

1.  Выберите **основные панель действий** в проекте **обозревателе решений**.

2.  В меню **Проект** выберите пункт **Добавить новый элемент**.

3.  В **Добавление нового элемента** диалоговом окне щелкните **элемента управления панели действий**, назовите элемент управления **InsertTextControl,** и нажмите кнопку **добавить**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Чтобы добавить элементы управления Windows для элемента управления панели действий

1.  Если элемент управления не отображается в конструкторе, дважды щелкните **InsertTextControl**.

2.  Из **стандартные элементы управления** вкладке **элементов**, перетащите **метка** управления для элемента управления панели действий.

3.  Изменение **текст** свойство элемента управления Label в **имя**.

4.  Добавить **Textbox** управления для элемента управления панели действий и измените следующие свойства.

    |Свойство.|Значение|
    |--------------|-----------|
    |**Name**|**GetName**|
    |**Size**|**130, 20**|

5.  Добавьте второй **метка** управления для элемента управления панели действий и измените **текст** свойства **адрес**.

6.  Добавьте второй **Textbox** управления для элемента управления панели действий и измените следующие свойства.

    |Свойство.|Значение|
    |--------------|-----------|
    |**Name**|**GetAddress**|
    |**Принимает возврата**|**True**|
    |**Multiline**|**True**|
    |**Size**|**130, 40**|

7.  Добавить **кнопку** управления для элемента управления панели действий и измените следующие свойства.

    |Свойство.|Значение|
    |--------------|-----------|
    |**Name**|**addText**|
    |**Text**|**Вставить**|

## <a name="add-code-to-insert-text-into-the-document"></a>Добавьте код для вставки текста в документ
 На панели действий, написать код, который вставляет текст из поля в соответствующие <xref:Microsoft.Office.Tools.Word.Bookmark> элементов управления в документе. Можно использовать `Globals` класс для доступа к элементам управления в документе из элементов управления в панели действий. Дополнительные сведения см. в разделе [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Вставить текст из области действия в закладке в документе

1.  Добавьте следующий код, чтобы <xref:System.Windows.Forms.Control.Click> обработчик событий **addText** кнопки.

     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]

2.  В C# необходимо добавить обработчик событий для нажатия кнопки. Можно поместить этот код в `InsertTextControl` конструктора после вызова `InitializeComponent`. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]

## <a name="add-code-to-show-the-actions-pane"></a>Добавьте код, чтобы отобразить панель действий
 Чтобы отобразить панель действий, добавьте элемент управления, созданный в коллекцию элементов управления.

### <a name="to-show-the-actions-pane"></a>Чтобы отобразить панель действий

1.  Создайте новый экземпляр элемента управления панели действий в `ThisDocument` класса.

     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]

2.  Добавьте следующий код, чтобы <xref:Microsoft.Office.Tools.Word.Document.Startup> обработчик событий `ThisDocument`.

     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]

## <a name="test-the-application"></a>Тестирование приложения
 Проверьте документ, чтобы убедиться, что панель действий открывается при открытии документа, и что текст, вводимый в текстовых полях вставляется в закладки, при нажатии кнопки.

### <a name="to-test-your-document"></a>Проверка документа

1.  Нажмите клавишу **F5** для запуска проекта.

2.  Убедитесь, что панель действий является видимым.

3.  Введите имя и адрес в текстовые поля в панели действий и нажмите кнопку **вставить**.

## <a name="next-steps"></a>Следующие шаги
 Ниже приводятся некоторые из возможных последующих задач.

-   Создайте панель действий в Excel. Дополнительные сведения см. в разделе [Как Добавление панели действий к книгам Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).

-   Привязка данных к элементам управления в панели действий. Дополнительные сведения см. в разделе [Пошаговое руководство: Привязка данных к элементам управления в панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>См. также
- [Общие сведения о панели действий](../vsto/actions-pane-overview.md)
- [Практическое руководство. Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Практическое руководство. Добавление панели действий для книг Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Практическое руководство. Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Элемент управления Bookmark](../vsto/bookmark-control.md)
