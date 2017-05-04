---
title: "Общие сведения о панели действий | Microsoft Docs"
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
  - "панели действий [разработка решений Office в Visual Studio]"
  - "панели действий [разработка решений Office в Visual Studio], сведения о панелях действий"
  - "смарт-документы [разработка решений Office в Visual Studio]"
  - "пользовательские элементы управления [разработка решений Office в Visual Studio], панели действий"
ms.assetid: 1b9b7db5-b19f-44ea-a774-f0962ca03bd2
caps.latest.revision: 101
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 100
---
# Общие сведения о панели действий
  Панель действий — это настраиваемая область задач **Действия с документами**, присоединенная к определенному документу Microsoft Office Word или книге Microsoft Office Excel.  Она размещается внутри области задач Office вместе с другими встроенными областями задач, такими как область задач **Источник XML** в Excel или область задач **Стили и форматирование** в Word.  Для разработки пользовательского интерфейса панели действий можно использовать элементы управления Windows Forms или элементы управления WPF.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Панель действий можно создать только в настройке на уровне документа Word или Excel.  Невозможно создать панель действий в надстройке VSTO.  Дополнительные сведения см. в разделе [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Панель действий отличается от настраиваемых областей задач.  Настраиваемые области задач связаны с приложением, а не с конкретным документом.  Вы можете создавать настраиваемые области задач в надстройках VSTO для некоторых приложений Microsoft Office.  Дополнительные сведения см. в разделе [Настраиваемые области задач](../vsto/custom-task-panes.md).  
  
 ![ссылка на видео](../vsto/media/playvideo.png "ссылка на видео") Связанный демонстрационный видеоролик можно просмотреть в статье [Как использовать элементы управления WPF в панели действий Excel](http://go.microsoft.com/fwlink/?LinkId=132763).  
  
## Отображение панели действий  
 Панель действий представлена классом <xref:Microsoft.Office.Tools.ActionsPane>.  При создании проекта на уровне документа экземпляр данного класса доступен в коде с помощью поля `ActionsPane` класса `ThisWorkbook` \(для Excel\) или `ThisDocument` \(для Word\) в проекте.  Чтобы отобразить панель действий, добавьте элемент управления Windows Forms в свойство <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> поля `ActionsPane`.  Следующий пример кода добавляет элемент управления с именем `actions` на панель действий.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
 Панель действий становится видимой во время выполнения, как только вы явно добавляете на нее элемент управления.  После отображения панели действий вы можете динамически добавлять или удалять элементы управления в ответ на действия пользователя.  Как правило, вы добавляете код, чтобы показать панель действий, в обработчик событий `Startup` для `ThisDocument` или `ThisWorkbook`, чтобы панель действий отображалась при первом открытии документа.  Однако вам может потребоваться отобразить панель действий только в ответ на действия пользователя в документе.  Например, можно добавить код в событие `Click` элемента управления в документе.  
  
### Добавление нескольких элементов управления на панель действий  
 При добавлении нескольких элементов управления на панель действий в большинстве случаев следует объединить их в пользовательском элементе управления, а затем добавить его в свойство <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>.  Этот процесс состоит из следующих шагов.  
  
1.  Создайте пользовательский интерфейс панели действий, добавив элемент **Панель действий** или **Пользовательский элемент управления** в проект.  Оба эти элемента включают пользовательский класс <xref:System.Windows.Forms.UserControl> Windows Forms.  Элементы **Элемент управления панели действий** и **Пользовательский элемент управления** эквивалентны; единственное отличие заключается в их именах.  
  
2.  Добавление элементов управления Windows Forms в <xref:System.Windows.Forms.UserControl> с помощью конструктора или кода.  
  
    > [!NOTE]  
    >  Можно также добавить элементы управления WPF на панель действий, добавив WPF <xref:System.Windows.Controls.UserControl> в <xref:System.Windows.Forms.UserControl> Windows Forms.  Дополнительные сведения см. в статье [Использование элементов управления WPF в решениях Office](../vsto/using-wpf-controls-in-office-solutions.md).  
  
3.  Добавьте экземпляр настраиваемого пользовательского элемента управления к элементам управления, которые содержатся в поле `ActionsPane` класса `ThisWorkbook` \(для Excel\) или `ThisDocument` \(для Word\) в проекте.  
  
 Примеры, демонстрирующие этот процесс более подробно, см. в разделе [Практическое руководство. Добавление области действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
## Скрытие панели действий  
 Хотя класс <xref:Microsoft.Office.Tools.ActionsPane> содержит метод <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> и свойство <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, панель действий невозможно удалить из пользовательского интерфейса с помощью членов класса <xref:Microsoft.Office.Tools.ActionsPane>.  Вызов метода <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> или установка для свойства <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> значения **false** скрывает только элементы управления на панели действий, но не область задач.  
  
 Существует несколько способов скрыть область задач в решении.  
  
-   В Word задайте для свойства <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> объекта <xref:Microsoft.Office.Interop.Word.TaskPane>, представляющего область задач «Действия с документами», значение **false**.  Код в следующем примере должен выполняться из класса `ThisDocument` в проекте.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#34)]  
  
-   Для Excel присвойте свойству <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> объекта <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> значение **false**.  Код в следующем примере должен выполняться из класса `ThisWorkbook` в проекте.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#11)]  
  
-   Для Word или Excel в качестве альтернативы можно задать для свойства <xref:Microsoft.Office.Core.CommandBar.Visible%2A> панели команд, представляющей область задач, значение **false**.  Код в следующем примере должен выполняться из класса `ThisDocument` или `ThisWorkbook` в проекте.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#9)]  
  
### Очистка панели действий при открытии документа  
 Если пользователь сохраняет документ, когда панель действий видима, она отображается при каждом открытии документа независимо от того, содержит ли панель действий элементы управления.  Если вы хотите управлять отображением панели действий, вызовите метод <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> поля `ActionsPane` в обработчике событий `Startup` для `ThisDocument` или `ThisWorkbook`, чтобы убедиться, что панель действий невидима при открытии документа.  
  
### Определение закрытия панели действий  
 При закрытии панели действий события не инициируются.  Хотя класс <xref:Microsoft.Office.Tools.ActionsPane> содержит событие <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, оно не возникает, когда пользователь закрывает панель действий.  Вместо этого событие инициируется, когда элементы управления на панели действий скрываются при вызове метода <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> или установке для свойства <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> значения **false**.  
  
 Если пользователь закрывает панель действий, он может отобразить ее повторно, выполнив одну из следующих процедур в пользовательском интерфейсе приложения.  
  
##### Отображение панели действий с помощью пользовательского интерфейса Word или Excel  
  
1.  На ленте перейдите на вкладку **Вид**.  
  
2.  В группе **Показать или скрыть** щелкните переключатель **Действия с документами**.  
  
## Программирование событий панели действий  
 Вы можете добавить несколько элементов управления на панель действий и затем написать код для реагирования на события в документе, отображая и скрывая пользовательские элементы управления.  Если сопоставить элементы схемы XML с вашим документом, вы сможете показывать определенные пользовательские элементы управления в панели действий всякий раз, когда курсор находится внутри одного из XML\-элементов.  Дополнительные сведения см. в разделах [Практическое руководство. Сопоставление схем и документов Word в Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) и [Практическое руководство. Сопоставление схем и листов внутри Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  
  
 Можно также написать код, чтобы реагировать на события любого объекта, включая ведущий элемент управления, приложение и документ.  Дополнительные сведения см. в разделе [Пошаговое руководство. Программирование реакции на события элементов управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
## Привязка данных к элементам управления в панели действий  
 Возможности привязки данных элементов управления на панели действий аналогичны возможностям элементов управления в формах Windows Forms.  Элементы управления можно привязать к источникам данных, таким как наборы данных, типизированные наборы данных и XML\-код.  Дополнительные сведения см. в разделе [Связывание данных и Windows Forms](../Topic/Data%20Binding%20and%20Windows%20Forms.md).  
  
 Вы можете привязать элементы управления на панели действий и элементы управления в документе к одному набору данных.  Например, можно создать иерархическое отношение между элементами управления на панели действий и элементами управления на листе.  Дополнительные сведения см. в разделе [Пошаговое руководство. Привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
## Проверка данных в элементах управления панели действий  
 Если вы показываете окно сообщения в обработчике событий <xref:System.Windows.Forms.Control.Validating> элемента управления на панели действий, это событие может быть вызвано во второй раз при перемещении фокуса с элемента управления на окно сообщения.  Чтобы предотвратить это, используйте элемент управления <xref:System.Windows.Forms.ErrorProvider> для отображения сообщений об ошибке проверки.  
  
## Порядок расположения пользовательских элементов управления  
 Если вы применяете несколько пользовательских элементов управления, можно написать код, чтобы правильно размещать их в панели действий в зависимости от того, закреплена ли она вертикально или горизонтально.  Можно задать порядок расположения пользовательских элементов управления на панели действий с помощью перечисления <xref:Microsoft.Office.Tools.StackStyle> свойства <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>.  Дополнительные сведения см. в разделе [Практическое руководство. Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md).  
  
 Свойство <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> может принимать следующие значения перечисления <xref:Microsoft.Office.Tools.StackStyle>.  
  
|Стиль расположения|Определение|  
|------------------------|-----------------|  
|FromBottom|Размещение от нижней части панели действий.|  
|FromLeft|Размещение от левой части панели действий.|  
|FromRight|Размещение от правой части панели действий.|  
|FromTop|Размещение от верхней части панели действий.|  
|None|Порядок расположения не определен, он определяется разработчиком.|  
  
 Следующий код задает свойство <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> так, чтобы располагать пользовательские элементы управления в верхней части панели действий.  
  
 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#10)]  
  
## Привязка элементов управления  
 Если пользователь изменяет размер панели действий во время выполнения, размеры элементов управления могут изменяться вместе с ней.  Вы можете использовать свойство <xref:System.Windows.Forms.Control.Anchor%2A> элемента управления Windows Forms, чтобы закрепить элементы управления на панели действий.  Таким же образом можно закрепить элементы управления Windows Forms на пользовательском элементе управления.  Дополнительные сведения см. в разделе [Практическое руководство. Привязка элементов управления в формах Windows Forms](../Topic/How%20to:%20Anchor%20Controls%20on%20Windows%20Forms.md).  
  
## Изменение размера панели действий  
 Невозможно напрямую изменить размер <xref:Microsoft.Office.Tools.ActionsPane>, так как <xref:Microsoft.Office.Tools.ActionsPane> внедряется в область задач.  Однако можно программно изменить ширину области задач, задав свойство <xref:Microsoft.Office.Core.CommandBar.Width%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач.  Вы можете изменить высоту области задач, если она закреплена горизонтально или является перемещаемой.  
  
 Обычно не рекомендуется программно менять размер области задач, так как у пользователя должна быть возможность выбрать размер области, который наилучшим образом соответствует его или ее потребностям.  Однако, если вам необходимо изменить ширину области задач, для этого можно использовать следующий код.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#102)]  
  
## Изменение положения панели действий  
 Невозможно изменить положение <xref:Microsoft.Office.Tools.ActionsPane> напрямую, так как он внедрен в область задач.  Тем не менее можно программно переместить область задач, задав свойство <xref:Microsoft.Office.Core.CommandBar.Position%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач.  
  
 Обычно не рекомендуется программно перемещать область задач, так как у пользователя должна быть возможность выбрать положение области, которое наилучшим образом соответствует его или ее потребностям.  Однако, если вам все\-таки необходимо переместить область задач, для этого можно использовать следующий код.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#100)]  
  
> [!NOTE]  
>  Пользователи могут в любое время переместить область задач вручную.  Нельзя гарантировать, что область задач останется закрепленной в положении, заданном программными средствами.  Однако можно проверить изменение ориентации и убедиться, что элементы управления на панели действий располагаются в правильном направлении.  Дополнительные сведения см. в разделе [Практическое руководство. Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md).  
  
 Установка свойств <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> и <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> объекта <xref:Microsoft.Office.Tools.ActionsPane> не меняет его позицию, так как объект <xref:Microsoft.Office.Tools.ActionsPane> внедрен в область задач.  
  
 Если область задач не закреплена, можно установить свойства <xref:Microsoft.Office.Core.CommandBar.Top%2A> и <xref:Microsoft.Office.Core.CommandBar.Left%2A> объекта <xref:Microsoft.Office.Core.CommandBar>, представляющего область задач.  Следующий код перемещает панель действий в верхний левый угол документа.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#101)]  
  
## См. также  
 [Использование элементов управления WPF в решениях Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Практическое руководство. Добавление области действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Пошаговое руководство. Привязка данных к элементам управления в панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Пошаговое руководство. Привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Практическое руководство. Управление структурой элементов управления в панели действий](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Пошаговое руководство. Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  