---
title: Общие сведения о панели действий
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 628620005c43ae465107e43572684cb74c8d1aa9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099745"
---
# <a name="actions-pane-overview"></a>Общие сведения о панели действий
  Панель действий — это настраиваемая **действия с документами** область задач, который подключен к конкретному документу Microsoft Office Word или книгу Microsoft Office Excel. Панель действий размещается внутри области задач Office вместе с другими встроенными областями задач, таких как **источник XML** в Excel или **стили и форматирование** области задач в Word. Для разработки пользовательского интерфейса панели действий можно использовать элементы управления Windows Forms или элементы управления WPF.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Панель действий можно создать только в настройке на уровне документа Word или Excel. Невозможно создать панель действий в надстройке VSTO. Дополнительные сведения см. в разделе [функций по типам приложений и проектов Office](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
>  Панель действий отличается от настраиваемых областей задач. Настраиваемые области задач связаны с приложением, а не с конкретным документом. Вы можете создавать настраиваемые области задач в надстройках VSTO для некоторых приложений Microsoft Office. Дополнительные сведения см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md).

 ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") демонстрационные видеоматериалы см. в разделе [инструкции: Используйте элементы управления WPF в панели действий Excel? ](http://go.microsoft.com/fwlink/?LinkId=132763).

## <a name="display-the-actions-pane"></a>Отображение панели действий
 Панель действий представлена классом <xref:Microsoft.Office.Tools.ActionsPane>. При создании проекта на уровне документа экземпляр данного класса доступен в коде с помощью поля `ActionsPane` класса `ThisWorkbook` (для Excel) или `ThisDocument` (для Word) в проекте. Чтобы отобразить панель действий, добавьте элемент управления Windows Forms в свойство <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> поля `ActionsPane`. Следующий пример кода добавляет элемент управления с именем `actions` на панель действий.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 Панель действий становится видимой во время выполнения, как только вы явно добавить элемент управления к нему. После отображения панели действий вы можете динамически добавлять или удалять элементы управления в ответ на действия пользователя. Как правило, вы добавляете код, чтобы показать панель действий, в обработчик событий `Startup` для `ThisDocument` или `ThisWorkbook`, чтобы панель действий отображалась при первом открытии документа. Однако вам может потребоваться отобразить панель действий только в ответ на действия пользователя в документе. Например, можно добавить код в событие `Click` элемента управления в документе.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Добавление нескольких элементов управления на панель действий
 При добавлении нескольких элементов управления на панель действий, следует объединить их в пользовательский элемент управления и затем добавьте пользовательский элемент управления для <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> свойство. Этот процесс состоит из следующих шагов.

1. Создание пользовательского интерфейса (UI) в панели действий, добавив **элемента управления панели действий** или **пользовательский элемент управления** в проект. Оба эти элемента включают пользовательский класс <xref:System.Windows.Forms.UserControl> Windows Forms. **Элемента управления панели действий** и **пользовательский элемент управления** элементы эквивалентны; единственное различие заключается в их именах.

2. Добавление элементов управления Windows Forms в <xref:System.Windows.Forms.UserControl> с помощью конструктора или кода.

   > [!NOTE]
   >  Можно также добавить элементы управления WPF на панель действий, добавив WPF <xref:System.Windows.Controls.UserControl> в <xref:System.Windows.Forms.UserControl> Windows Forms. Дополнительные сведения см. в разделе [управляет использования WPF в решениях Office](../vsto/using-wpf-controls-in-office-solutions.md).

3. Добавьте экземпляр настраиваемого пользовательского элемента управления к элементам управления, которые содержатся в поле `ActionsPane` класса `ThisWorkbook` (для Excel) или `ThisDocument` (для Word) в проекте.

   Примеры, демонстрирующие этот процесс более подробно, см. в разделе [как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

## <a name="hide-the-actions-pane"></a>Скрыть панель действий
 Хотя класс <xref:Microsoft.Office.Tools.ActionsPane> содержит метод <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> и свойство <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, панель действий невозможно удалить из пользовательского интерфейса с помощью членов класса <xref:Microsoft.Office.Tools.ActionsPane>. Вызов <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> метода или параметра <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> свойства **false** скрывает только элементы управления в панели действий; она будет отображаться на панели задач.

 Существует несколько способов скрыть область задач в решении.

- Word задайте <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> свойство <xref:Microsoft.Office.Interop.Word.TaskPane> , представляющий область действия с документами задач **false**. Код в следующем примере должен выполняться из класса `ThisDocument` в проекте.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- Для Excel присвойте <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> свойство <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> объект **false**. Код в следующем примере должен выполняться из класса `ThisWorkbook` в проекте.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- Для Word или Excel, можно также задать <xref:Microsoft.Office.Core.CommandBar.Visible%2A> свойства, представляющего область задач на панели команд **false**. Код в следующем примере должен выполняться из класса `ThisDocument` или `ThisWorkbook` в проекте.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Очистка панели действий при открытии документа
 Когда пользователь сохраняет документ, когда панель действий видима, панель действий отображается каждый раз при открытии документа независимо от того, имеется ли панель действий содержит все элементы управления. Если вы хотите управлять отображением панели действий, вызовите метод <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> поля `ActionsPane` в обработчике событий `Startup` для `ThisDocument` или `ThisWorkbook`, чтобы убедиться, что панель действий невидима при открытии документа.

### <a name="determine-when-the-actions-pane-is-closed"></a>Определить, при закрытии панели действий
 При закрытии панели действий события не инициируются. Хотя класс <xref:Microsoft.Office.Tools.ActionsPane> содержит событие <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, оно не возникает, когда пользователь закрывает панель действий. Вместо этого, это событие возникает, когда элементы управления на панели действий скрываются при вызове <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> метод или задав <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> свойства **false**.

 Когда пользователь закрывает панель действий, пользователь может отобразить ее повторно, выполнив одну из следующих процедур в пользовательском интерфейсе (UI) приложения.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Отображение панели действий с помощью пользовательского интерфейса Word или Excel

1. На ленте щелкните **представление** вкладки.

2. В **Показать/скрыть** щелкните **действия с документами** кнопки-переключателя.

## <a name="program-actions-pane-events"></a>Событий панели действий программы
 Вы можете добавить несколько элементов управления на панель действий и затем написать код для реагирования на события в документе, отображая и скрывая пользовательские элементы управления. Если сопоставить элементы схемы XML с вашим документом, вы сможете показывать определенные пользовательские элементы управления в панели действий всякий раз, когда курсор находится внутри одного из XML-элементов. Дополнительные сведения см. в разделе [Как Сопоставление схем и документов Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) и [как: Сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 Можно также написать код, чтобы реагировать на события любого объекта, включая ведущий элемент управления, приложение и документ. Дополнительные сведения см. в разделе [Пошаговое руководство: Программа реакции на события элементов управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Привязка данных к элементам управления в панели действий
 Возможности привязки данных элементов управления на панели действий аналогичны возможностям элементов управления в формах Windows Forms. Элементы управления можно привязать к источникам данных, таким как наборы данных, типизированные наборы данных и XML-код. Дополнительные сведения см. в разделе [привязка данных и Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Вы можете привязать элементы управления на панели действий и элементы управления в документе к одному набору данных. Например, можно создать иерархическое отношение между элементами управления на панели действий и элементами управления на листе. Дополнительные сведения см. в разделе [Пошаговое руководство: Привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

## <a name="validate-data-in-actions-pane-controls"></a>Проверка данных в элементах управления панели действий
 Если вы показываете окно сообщения в обработчике событий <xref:System.Windows.Forms.Control.Validating> элемента управления на панели действий, это событие может быть вызвано во второй раз при перемещении фокуса с элемента управления на окно сообщения. Чтобы предотвратить это, используйте элемент управления <xref:System.Windows.Forms.ErrorProvider> для отображения сообщений об ошибке проверки.

## <a name="user-control-stacking-order"></a>Порядок расположения пользовательских элементов управления
 Если вы применяете несколько пользовательских элементов управления, можно написать код, чтобы правильно размещать их в панели действий в зависимости от того, закреплена ли она вертикально или горизонтально. Можно задать порядок расположения пользовательских элементов управления на панели действий с помощью перечисления <xref:Microsoft.Office.Tools.StackStyle> свойства <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>. Дополнительные сведения см. в разделе [Как Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)

 Свойство <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> может принимать следующие значения перечисления <xref:Microsoft.Office.Tools.StackStyle>.

|Стиль расположения|Определение|
|--------------------|----------------|
|FromBottom|Размещение от нижней части панели действий.|
|FromLeft|Размещение от левой части панели действий.|
|FromRight|Размещение от правой части панели действий.|
|FromTop|Размещение от верхней части панели действий.|
|Нет|Порядок расположения не определен, он определяется разработчиком.|

 Следующий код задает свойство <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> так, чтобы располагать пользовательские элементы управления в верхней части панели действий.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Привязка элементов управления
 Если пользователь изменяет размер панели действий во время выполнения, можно изменить размер элементов управления с панелью действий. Вы можете использовать свойство <xref:System.Windows.Forms.Control.Anchor%2A> элемента управления Windows Forms, чтобы закрепить элементы управления на панели действий. Таким же образом можно закрепить элементы управления Windows Forms на пользовательском элементе управления. Дополнительные сведения см. в разделе [Как Привязка элементов управления в Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Изменение размера панели действий
 Невозможно напрямую изменить размер <xref:Microsoft.Office.Tools.ActionsPane>, так как <xref:Microsoft.Office.Tools.ActionsPane> внедряется в область задач. Однако можно программно изменить ширину области задач, задав свойство <xref:Microsoft.Office.Core.CommandBar.Width%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач. Вы можете изменить высоту области задач, если она закреплена горизонтально или является перемещаемой.

 Не рекомендуется программно менять размер области задач, поскольку пользователь должен иметь возможность выбрать размер области задач, который наилучшим образом соответствует их потребностям. Однако, если вам необходимо изменить ширину области задач, для этого можно использовать следующий код.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Изменить положение панели действий
 Невозможно изменить положение <xref:Microsoft.Office.Tools.ActionsPane> напрямую, так как он внедрен в область задач. Тем не менее можно программно переместить область задач, задав свойство <xref:Microsoft.Office.Core.CommandBar.Position%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач.

 Не рекомендуется программно перемещать область задач, так как он должна быть возможность выбрать положение на экране, которое наилучшим образом соответствует его или ее потребностям. Однако, если вам все-таки необходимо переместить область задач, для этого можно использовать следующий код.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
>  Пользователи могут в любое время переместить область задач вручную. Нельзя гарантировать, что область задач останется закрепленной в положении, заданном программными средствами. Однако можно проверить изменение ориентации и убедиться, что элементы управления на панели действий располагаются в правильном направлении. Дополнительные сведения см. в разделе [Как Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 Установка <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> и <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> свойства <xref:Microsoft.Office.Tools.ActionsPane> не меняет его позицию, так как <xref:Microsoft.Office.Tools.ActionsPane> объект внедряется в области задач.

 Если область задач не закреплена, можно установить свойства <xref:Microsoft.Office.Core.CommandBar.Top%2A> и <xref:Microsoft.Office.Core.CommandBar.Left%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач. Следующий код перемещает панель задач в верхний левый угол документа.

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]

## <a name="see-also"></a>См. также
- [Использование элементов управления WPF в решениях Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Практическое руководство. Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Пошаговое руководство: Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Пошаговое руководство: Привязка данных к элементам управления в панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Пошаговое руководство: Привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Практическое руководство. Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Пошаговое руководство: Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
