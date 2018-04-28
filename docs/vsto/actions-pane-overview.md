---
title: Общие сведения о панели действий | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 50f39b6fc292bba2081d8eb5c3bc87d6f9041b49
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2018
---
# <a name="actions-pane-overview"></a>Общие сведения о панели действий
  Панель действий — это настраиваемая **действия с документами** область задач, подключенные к определенному документу Microsoft Office Word или книге Microsoft Office Excel. Панель действий размещается внутри области задач Office вместе с другими встроенными областями задач, таких как **XML-источник** в Excel или **стили и форматирование** области задач в Word. Для разработки пользовательского интерфейса панели действий можно использовать элементы управления Windows Forms или элементы управления WPF.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

 Панель действий можно создать только в настройке на уровне документа Word или Excel. Невозможно создать панель действий в надстройке VSTO. Дополнительные сведения см. в разделе [Доступность возможностей по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  

> [!NOTE]  
>  Панель действий отличается от настраиваемых областей задач. Настраиваемые области задач связаны с приложением, а не с конкретным документом. Вы можете создавать настраиваемые области задач в надстройках VSTO для некоторых приложений Microsoft Office. Дополнительные сведения см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md).  

 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [как сделать I: использования WPF элементов управления в панели действий Excel?](http://go.microsoft.com/fwlink/?LinkId=132763).

## <a name="displaying-the-actions-pane"></a>Отображение панели действий  
 Панель действий представлена классом <xref:Microsoft.Office.Tools.ActionsPane>. При создании проекта на уровне документа экземпляр данного класса доступен в коде с помощью поля `ActionsPane` класса `ThisWorkbook` (для Excel) или `ThisDocument` (для Word) в проекте. Чтобы отобразить панель действий, добавьте элемент управления Windows Forms в свойство <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> поля `ActionsPane`. Следующий пример кода добавляет элемент управления с именем `actions` на панель действий.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  

 Панель действий становится видимой во время выполнения, как только вы явно добавляете на нее элемент управления. После отображения панели действий вы можете динамически добавлять или удалять элементы управления в ответ на действия пользователя. Как правило, вы добавляете код, чтобы показать панель действий, в обработчик событий `Startup` для `ThisDocument` или `ThisWorkbook`, чтобы панель действий отображалась при первом открытии документа. Однако вам может потребоваться отобразить панель действий только в ответ на действия пользователя в документе. Например, можно добавить код в событие `Click` элемента управления в документе.  

### <a name="adding-multiple-controls-to-the-actions-pane"></a>Добавление нескольких элементов управления на панель действий  
 При добавлении нескольких элементов управления на панель действий, необходимо объединить элементы управления в пользовательском элементе управления и затем добавьте элемент управления, чтобы <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> свойство. Этот процесс состоит из следующих шагов.  

1.  Создание пользовательского интерфейса (UI) в панели действий, добавив **управления панели действий** или **пользовательский элемент управления** в проект. Оба эти элемента включают пользовательский класс <xref:System.Windows.Forms.UserControl> Windows Forms. **Управления панели действий** и **пользовательский элемент управления** элементы эквивалентны; единственное отличие заключается в их именах.  

2.  Добавление элементов управления Windows Forms в <xref:System.Windows.Forms.UserControl> с помощью конструктора или кода.  

    > [!NOTE]  
    >  Можно также добавить элементы управления WPF на панель действий, добавив WPF <xref:System.Windows.Controls.UserControl> в <xref:System.Windows.Forms.UserControl> Windows Forms. Дополнительные сведения см. в разделе [с помощью элементов управления WPF в решениях Office](../vsto/using-wpf-controls-in-office-solutions.md).  

3.  Добавьте экземпляр настраиваемого пользовательского элемента управления к элементам управления, которые содержатся в поле `ActionsPane` класса `ThisWorkbook` (для Excel) или `ThisDocument` (для Word) в проекте.  

 Примеры, демонстрирующие этот процесс более подробно см. в разделе [как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  

## <a name="hiding-the-actions-pane"></a>Скрытие панели действий  
 Хотя класс <xref:Microsoft.Office.Tools.ActionsPane> содержит метод <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> и свойство <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, панель действий невозможно удалить из пользовательского интерфейса с помощью членов класса <xref:Microsoft.Office.Tools.ActionsPane>. Вызов <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> метод или параметр <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> свойства **false** скрывает только элементы управления на панели действий, не скрывает область задач.  

 Существует несколько способов скрыть область задач в решении.  

-   В Word задайте <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> свойство <xref:Microsoft.Office.Interop.Word.TaskPane> объекта, представляющего область задач действия с документами в **false**. Код в следующем примере должен выполняться из класса `ThisDocument` в проекте.  

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  

-   Для Excel присвойте <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> свойство <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> объект **false**. Код в следующем примере должен выполняться из класса `ThisWorkbook` в проекте.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  

-   Для Word или Excel, в качестве альтернативы можно задать <xref:Microsoft.Office.Core.CommandBar.Visible%2A> свойства командной строки, представляющей область задач, чтобы **false**. Код в следующем примере должен выполняться из класса `ThisDocument` или `ThisWorkbook` в проекте.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  

### <a name="clearing-the-actions-pane-when-the-document-is-opened"></a>Очистка панели действий при открытии документа  
 Когда пользователь сохраняет документ, когда панель действий видима, панель действий отображается каждый раз при открытии документа ли панель действий содержит все элементы управления. Если вы хотите управлять отображением панели действий, вызовите метод <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> поля `ActionsPane` в обработчике событий `Startup` для `ThisDocument` или `ThisWorkbook`, чтобы убедиться, что панель действий невидима при открытии документа.  

### <a name="determining-when-the-actions-pane-is-closed"></a>Определение закрытия панели действий  
 При закрытии панели действий события не инициируются. Хотя класс <xref:Microsoft.Office.Tools.ActionsPane> содержит событие <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, оно не возникает, когда пользователь закрывает панель действий. Вместо этого это событие возникает, когда элементы управления в панели действий скрываются при вызове <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> метода или установив <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> свойства **false**.  

 Когда пользователь закрывает панель действий, пользователь может отобразить ее повторно, выполнив одну из следующих процедур в пользовательском интерфейсе (UI) приложения.  

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Отображение панели действий с помощью пользовательского интерфейса Word или Excel  

1.  На ленте щелкните **представление** вкладки.  

2.  В **Показать или скрыть** щелкните **действия с документами** выключателя.  

## <a name="programming-actions-pane-events"></a>Программирование событий панели действий  
 Вы можете добавить несколько элементов управления на панель действий и затем написать код для реагирования на события в документе, отображая и скрывая пользовательские элементы управления. Если сопоставить элементы схемы XML с вашим документом, вы сможете показывать определенные пользовательские элементы управления в панели действий всякий раз, когда курсор находится внутри одного из XML-элементов. Дополнительные сведения см. в разделе [как: карту схемы в Word документы в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) и [как: сопоставление схем для листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  

 Можно также написать код, чтобы реагировать на события любого объекта, включая ведущий элемент управления, приложение и документ. Дополнительные сведения см. в разделе [Пошаговое руководство. Программирование реакции на события элементов управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  

## <a name="binding-data-to-controls-on-the-actions-pane"></a>Привязка данных к элементам управления в панели действий  
 Возможности привязки данных элементов управления на панели действий аналогичны возможностям элементов управления в формах Windows Forms. Элементы управления можно привязать к источникам данных, таким как наборы данных, типизированные наборы данных и XML-код. Дополнительные сведения см. в разделе [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  

 Вы можете привязать элементы управления на панели действий и элементы управления в документе к одному набору данных. Например, можно создать иерархическое отношение между элементами управления на панели действий и элементами управления на листе. Дополнительные сведения см. в разделе [Пошаговое руководство: привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  

## <a name="validating-data-in-actions-pane-controls"></a>Проверка данных в элементах управления панели действий  
 Если вы показываете окно сообщения в обработчике событий <xref:System.Windows.Forms.Control.Validating> элемента управления на панели действий, это событие может быть вызвано во второй раз при перемещении фокуса с элемента управления на окно сообщения. Чтобы предотвратить это, используйте элемент управления <xref:System.Windows.Forms.ErrorProvider> для отображения сообщений об ошибке проверки.  

## <a name="user-control-stacking-order"></a>Порядок расположения пользовательских элементов управления  
 Если вы применяете несколько пользовательских элементов управления, можно написать код, чтобы правильно размещать их в панели действий в зависимости от того, закреплена ли она вертикально или горизонтально. Можно задать порядок расположения пользовательских элементов управления на панели действий с помощью перечисления <xref:Microsoft.Office.Tools.StackStyle> свойства <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>. Дополнительные сведения см. в разделе [как: Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)  

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

## <a name="anchoring-controls"></a>Привязка элементов управления  
 Если пользователь изменяет размер панели действий во время выполнения, размеры элементов управления могут изменяться вместе с ней. Вы можете использовать свойство <xref:System.Windows.Forms.Control.Anchor%2A> элемента управления Windows Forms, чтобы закрепить элементы управления на панели действий. Таким же образом можно закрепить элементы управления Windows Forms на пользовательском элементе управления. Дополнительные сведения см. в разделе [как: закрепить элементы управления в формах Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  

## <a name="resizing-the-actions-pane"></a>Изменение размера панели действий  
 Невозможно напрямую изменить размер <xref:Microsoft.Office.Tools.ActionsPane>, так как <xref:Microsoft.Office.Tools.ActionsPane> внедряется в область задач. Однако можно программно изменить ширину области задач, задав свойство <xref:Microsoft.Office.Core.CommandBar.Width%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач. Вы можете изменить высоту области задач, если она закреплена горизонтально или является перемещаемой.  

 Не рекомендуется программно менять в области задач, так как пользователь должен иметь возможность выбрать размер области, который наилучшим образом соответствует их потребностям. Однако, если вам необходимо изменить ширину области задач, для этого можно использовать следующий код.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  

## <a name="repositioning-the-actions-pane"></a>Изменение положения панели действий  
 Невозможно изменить положение <xref:Microsoft.Office.Tools.ActionsPane> напрямую, так как он внедрен в область задач. Тем не менее можно программно переместить область задач, задав свойство <xref:Microsoft.Office.Core.CommandBar.Position%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач.  

 Обычно не рекомендуется программно перемещать область задач, так как у пользователя должна быть возможность выбрать положение области, которое наилучшим образом соответствует его или ее потребностям. Однако, если вам все-таки необходимо переместить область задач, для этого можно использовать следующий код.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  

> [!NOTE]  
>  Пользователи могут в любое время переместить область задач вручную. Нельзя гарантировать, что область задач останется закрепленной в положении, заданном программными средствами. Однако можно проверить изменение ориентации и убедиться, что элементы управления на панели действий располагаются в правильном направлении. Дополнительные сведения см. в разделе [как: Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md).  

 Установка <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> и <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> свойства <xref:Microsoft.Office.Tools.ActionsPane> не меняет его позицию, так как <xref:Microsoft.Office.Tools.ActionsPane> объект внедрен в область задач.  

 Если область задач не закреплена, можно установить свойства <xref:Microsoft.Office.Core.CommandBar.Top%2A> и <xref:Microsoft.Office.Core.CommandBar.Left%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач. Следующий код перемещает панель задач в верхний левый угол документа.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  

## <a name="see-also"></a>См. также  
 [Использование элементов управления WPF в решениях Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Пошаговое руководство: Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Пошаговое руководство: Привязка данных к элементам управления в панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Пошаговое руководство: Привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Как: Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
