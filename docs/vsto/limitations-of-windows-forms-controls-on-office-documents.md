---
title: Ограничения Windows Forms, элементы управления в документах Office | Документы Microsoft
ms.date: 02/02/2017
ms.technology: office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1136d799bb6bee56f0589c798a7c61fe0879d556
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitations of Windows Forms Controls on Office Documents

Существуют некоторые различия между элементы управления Windows Forms, которые добавляются в документы Microsoft Office Word или листы Microsoft Office Excel и элементы управления Windows Forms, которые были добавлены в Windows Forms. Например, при добавлении <xref:Microsoft.Office.Tools.Word.Controls.Button> элементов управления в документ, свойства, такие как <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, и <xref:System.Windows.Forms.Control.TabIndex> работать не так, как и следует ожидать.

Многие из этих отличий связаны со способом размещенные элементы управления Windows Forms в документах. При добавлении элемента управления Windows Forms в документ [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] встраивает элемент управления ActiveX, размещающий элемент управления Windows Forms в документ. Элемент управления Windows Forms не внедряется непосредственно в документе.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Ограничения методов и свойств элементов управления Windows Forms

Существует несколько методов и свойств элементов управления Windows Forms, которые работают так же, как в документе в форме Windows Forms, и, таким образом, рекомендуется, что они не будут использоваться. Например, такие как установка свойства <xref:System.Windows.Forms.Control.Dock> и <xref:System.Windows.Forms.Control.Anchor> влияет только на положение элемента управления относительно контейнера элемента управления ActiveX, а не в документе. Ниже приведен список неподдерживаемых методов и свойств элементов управления Windows Forms для Word и Excel.

- Неподдерживаемые свойства элементов управления Excel:

    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>

- Неподдерживаемые методы и свойства элементов управления Word:

    - <xref:System.Windows.Forms.Control.Hide%2A>
    - <xref:System.Windows.Forms.Control.Show%2A>
    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>
    - <xref:System.Windows.Forms.Control.Visible>

Также нельзя задать <xref:System.Windows.Forms.Control.Left> или <xref:System.Windows.Forms.Control.Top> свойства элементов управления Windows Forms, в тексте в документе Word. Элементы управления Windows Forms добавляются в текст в следующих случаях:

- Программно добавить элемент управления в документ Word и использовать метод, который определяет диапазон для расположения.

- Добавление элемента управления Windows Forms в документ Word во время разработки. Это можно изменить путем изменения элемента управления в конструкторе.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Различия элементов управления Windows Forms в документах Office

Элементы управления Windows Forms обычно имеют такое же поведение в документ Office, как они в форме Windows, но существуют некоторые различия. Следующая таблица описывает различия, которые существуют для элементов управления Windows Forms в документах Office.

|Функция|Различие|
|-------------------|----------------|
|Последовательность перехода элемента управления|Нельзя осуществлять переход между элементами управления на листе Excel или документе Word.|
|Группирование элементов управления|Нельзя использовать <xref:System.Windows.Forms.GroupBox> управления содержать другие элементы управления в документ Office. При добавлении нескольких переключателей непосредственно документа, переключатели не являются взаимоисключающими. Можно написать код, чтобы переключатели взаимоисключающими; Тем не менее рекомендуется внести переключатели в пользовательский элемент управления, а затем добавить пользовательский элемент управления в документ. Дополнительные сведения см. Пример элементов управления Word или Excel примере в [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).|
|Тип элемента управления|Используемые в документах элементы управления Windows Forms упаковываются в класс, предоставляемый [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , обеспечивает элементы функции, характерные для листа Excel или документа Word. Например, если у вас есть **кнопку** управления на листе Excel, необходимо указать тип как <xref:Microsoft.Office.Tools.Excel.Controls.Button> вместо <xref:System.Windows.Forms.Button> при создании ссылки или приведение объекта.|
|Размер и размещение элементов управления|Размер и положение элемента управления определяется свойствами, которые являются частью контейнера элемента управления ActiveX. Свойства элемента управления ActiveX принимать различные значения эквивалентных свойств элемента управления Windows Forms. При задании `Top`, `Left`, `Height`, или `Width` свойства элемента управления, измеряется в пунктах, а не в пикселях.|
|Положение элемента управления в документы Word|При добавлении элементов управления в потоковый макет Имейте в виду, что элементы управления будут предлагаться с содержимым при изменении содержимого. Не удается прикрепить элемент управления абзаца, перетащите его из **элементов** , поскольку элемент управления добавляется в документ Word в тексте. Если используется другой метод для добавления элемента управления, такие как двойной щелчок на элементе управления вставляется в соответствии с параметром Word, заданных для вставки изображения.<br /><br /> Не удается задать `Left` или `Top` свойства элемента управления, в тексте.<br /><br /> Не удается поместить элементы управления в верхний или нижний колонтитул или внутри вложенного документа.|
|События элементов управления|При выборе элемента управления, события возникают в следующем порядке:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Если элемент управления выбран, события возникают в следующем порядке:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Масштабирование элемента управления|При изменении значения масштабирования документа на отличное от 100%, элементы управления отключены, несмотря на то, что они выглядят как масштабировать вместе с документом. Например, при нажатии кнопки при заданном значении масштаба 130% будет отображать сообщение об отключении элемента управления до масштабирования до значения 100%. Элементы управления будут работать правильно при изменении масштаба на 100%.|
|Значения свойств элементов управления|Несмотря на то, что свойства элементов управления в форме Windows устанавливаются в целочисленное значение, они устанавливаются в один для элементов управления в документе Word. В Excel значения свойств элементов управления, присваивается значение типа double. Если `Height` и `Width` свойства элемента управления на листе превышает размер листа или экрана, значение усекается.|
|Изменение размера элемента управления|Если элемент управления с помощью одного из восьми маркеров изменения размера, новые размеры элемента управления не отражаются в **свойства** окна, пока не будет повторно элемента управления.|
|Поведение элемента управления|Элементы управления на листе Excel могут вести себя непредсказуемым образом, при разбиении окно листа. Например, доступ к <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> на листе может предоставляться только в одном из windows.|
|Имена элементов управления.|Нельзя использовать зарезервированные слова для именования элементов управления приложения. Например, при добавлении <xref:Microsoft.Office.Tools.Excel.Controls.Button> на лист и измените имя на **системы**, возникают ошибки при построении проекта.|
|Добавление элементов управления программными средствами|Не используйте конструктор элемента управления для добавления элемента управления в документ во время выполнения. Вместо этого используйте вспомогательные методы, предоставляемые [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Например, используйте <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> метод, чтобы добавить кнопку на лист. Если вы хотите добавить элемент управления, который не поддерживается в эти вспомогательные методы, можно использовать метод AddControl. Для получения дополнительной информации см. [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Копирование элементов управления|При копировании элемента управления Windows Forms и вставьте его в документ во время выполнения, в документ будет вставлен пустой контейнер элемента управления ActiveX. Элемент управления Windows Forms не отображается в новом месте, а код, содержащий исходный элемент управления не копируется в контейнер элемента управления ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Ограничения в проектах уровня документа

Некоторые ограничения использования элементов управления Windows Forms в документах уникальны для проектов уровня документа.

### <a name="control-support-at-design-time"></a>Поддержка элементов управления во время разработки

Некоторые элементы управления Windows Forms удаляются из **элементов** при XML-документ Word или листа Excel открыта в конструкторе Visual Studio. Это из-за технических ограничений или потому, что эти функциональные возможности уже доступны в Word или Excel. Проекты Excel и Word поддерживают все элементы управления Windows Forms и другие компоненты, отображаемые в **элементов** при документ имеет фокус, а также можно добавить элементы управления сторонних разработчиков, лист или документ.

> [!NOTE]
> Все элементы управления удаляются из **элементов** когда документ защищен. Сведения о защите документа см. в разделе [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Элементы управления сторонних разработчиков должен иметь <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибута **true** для использования в решении Office.

Следующие элементы управления и компоненты недоступны в **элементов**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Поддержка существующих элементов управления ActiveX

При создании проекта Office уровня документа, использующего существующего документа Word или книги Excel, которая содержит элементы управления ActiveX, функциональные возможности элементов управления ActiveX не поддерживается. Тем не менее не поддерживается для добавления новых элементов управления ActiveX в документах в Visual Studio. Например, если документ Word имеет кнопку из **управления** элементов под управлением Visual Basic для приложений (VBA), она будет продолжать выполняться макрос после использования документа в проекте Office. Тем не менее рекомендуется удалить элементы управления ActiveX и макросы VBA и заменить их элементы управления Windows Forms и управляемого кода.

## <a name="see-also"></a>См. также

- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Общие сведения об использовании элементов управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)