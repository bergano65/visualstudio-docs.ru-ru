---
title: Ограничения элементов управления Windows Forms в документах Office
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 610ee5e18054b6da35a3098b851d1585c70b6bc3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863556"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Ограничения элементов управления Windows Forms в документах Office

Существуют некоторые различия между элементами управления Windows Forms, которые добавляются в документы Microsoft Office Word или листы Microsoft Office Excel и элементы управления Windows Forms, которые добавляются в формы Windows Forms. Например, при добавлении <xref:Microsoft.Office.Tools.Word.Controls.Button> элементов управления в документ, свойства, такие как <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, и <xref:System.Windows.Forms.Control.TabIndex> работать не так, как вы могли предположить.

Многие из этих отличий связаны со способом, Windows Forms, элементы управления расположены в документах. При добавлении элемента управления Windows Forms в документ [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] внедряет элемент управления ActiveX, затем размещает элемент управления Windows Forms в документ. Элемент управления Windows Forms не внедряется непосредственно в документе.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Ограничения методов и свойств элементов управления Windows Forms

Существует ряд методов и свойств элементов управления Windows Forms, которые не работают так же, как в документе, как это было бы в Windows Forms, и таким образом, рекомендуется, что они не следует использовать. Например, такие как установка свойств <xref:System.Windows.Forms.Control.Dock> и <xref:System.Windows.Forms.Control.Anchor> влияет только на положение элемента управления по отношению к контейнерный элемент управления ActiveX, а не документа. Ниже приведен список неподдерживаемых методов и свойств элементов управления Windows Forms для Word и Excel:

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

Также нельзя задать <xref:System.Windows.Forms.Control.Left> или <xref:System.Windows.Forms.Control.Top> свойства элементов управления Windows Forms, которые согласованы с текста в документе Word. Элементы управления Windows Forms добавляются в текст в следующих случаях:

- Программное добавление элемента управления в документ Word и использовать метод, который указывает диапазон для расположения.

- Добавьте элемент управления Windows Forms в документ Word во время разработки. Это можно изменить, изменив элемент управления в конструкторе.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Различия в элементах управления Windows Forms в документах Office

Элементы управления Windows Forms обычно ведут себя так же в документ Office как они в Windows Forms, но существуют некоторые различия. Следующая таблица описывает различия, которые существуют для элементов управления Windows Forms в документах Office.

|Функция|Различие|
|-------------------|----------------|
|Последовательность табуляции элемента управления|Нельзя осуществлять переход между элементов управления, помещенных в лист Excel или документе Word.|
|Группирование элементов управления|Нельзя использовать <xref:System.Windows.Forms.GroupBox> элемент управления для размещения других элементов управления в документ Office. При добавлении нескольких переключателей непосредственно к документу, переключатели не являются взаимоисключающими. Можно написать код, чтобы сделать переключателей взаимно исключают друг друга; Тем не менее рекомендуется добавить кнопки-переключатели в пользовательский элемент управления, а затем добавить пользовательский элемент управления в документ. Дополнительные сведения см. в разделе Пример элементов управления Word или Excel пример элементов управления в [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).|
|Тип элемента управления|Элементы управления Windows Forms, используемые в документах, упаковываются в класс, предоставляемый [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , обеспечивает элементы управления функции, характерные для листа Excel или документ Word. Например, если у вас есть **кнопку** управления на листе Excel, не забудьте указать тот тип, что <xref:Microsoft.Office.Tools.Excel.Controls.Button> вместо <xref:System.Windows.Forms.Button> при создании ссылки или приведение объекта.|
|Размер и размещение элементов управления|Размер и положение элемента управления определяется свойствами, которые являются частью контейнера элемента управления ActiveX. Свойства элемента управления ActiveX принимать различные значения эквивалентных свойств элемента управления Windows Forms. При задании `Top`, `Left`, `Height`, или `Width` свойства элемента управления, это значение измеряется в точках, вместо того чтобы пикселей.|
|Положение элемента управления в документах Word|При добавлении элементов управления в потоковый макет, имейте в виду, что элементы управления будет проходить с содержимым при изменении содержимого. Не удается прикрепить элемент управления абзаца, перетаскивая его из **элементов** так, как элемент управления добавляется в документ Word в текстовой строке. Если вы используете другой метод для добавления элемента управления, например при двойном щелчке элемента управления, элемент управления вставляется в соответствии с параметром слово, которое вы задали для вставки изображения.<br /><br /> Невозможно задать `Left` или `Top` свойства элемента управления, в тексте.<br /><br /> Не удается разместить элементы управления, в верхний или нижний колонтитул или внутри вложенного документа.|
|События элементов управления|При выборе элемента управления, он создает события в следующем порядке:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Если элемент управления выбран, он создает события в следующем порядке:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Масштабирование элемента управления|Если изменить настройку масштаба документа только на 100%, элементы управления отключены, несмотря на то, что у них могут масштабировать с документом. Например, если щелкнуть кнопки при заданном значении масштаба 130%, появится сообщение об отключении управления пока масштаб равен 100%. Элементы управления будут работать правильно при изменении масштаба 100%.|
|Значения свойств элементов управления|Несмотря на то, что свойства элементов управления в форме Windows присваивается целочисленное значение, они устанавливаются в один для элементов управления в документ Word. В Excel задаются значения свойств элементов управления, к типу double. Если `Height` и `Width` свойства элемента управления на листе превышает размер листа или экрана, значение будет усечено.|
|Изменение размера элемента управления|При изменении размера элемента управления с помощью одного из восьми маркеров, новые размеры элемента управления не отражаются в **свойства** окно, пока не будет повторно элемента управления.|
|Поведение элемента управления|Элементы управления на листе Excel может работать непредсказуемым образом, при разбиении окно листа. Например, доступ к <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> на листе могут быть доступны только в одном из windows.|
|Имена элементов управления.|Нельзя использовать зарезервированные слова к элементам управления имя. Например, если вы добавите <xref:Microsoft.Office.Tools.Excel.Controls.Button> на лист и измените имя на **системы**, при сборке проекта возникнут ошибки.|
|Программное добавление элементов управления|Не используйте конструктор элемента управления для добавления элемента управления в документ во время выполнения. Вместо этого используйте вспомогательные методы, предоставляемые [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Например, использовать <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> метод, чтобы добавить кнопку на лист. Если вы хотите добавить элемент управления, который не поддерживается в эти вспомогательные методы, можно использовать `AddControl` метод. Дополнительные сведения см. в разделе [добавить элементы управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Копирование элементов управления|При копировании элемента управления Windows Forms и вставьте его в документ во время выполнения, в документ вставляется пустой контейнер элемента управления ActiveX. Элемент управления Windows Forms не отображается в новом месте и кода программной части исходный элемент управления не копируется в контейнер элемента управления ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Ограничения в проектах уровня документа

Некоторые ограничения на использование элементов управления Windows Forms в документах уникальны для проектов уровня документа.

### <a name="control-support-at-design-time"></a>Поддержка элементов управления во время разработки

Некоторые элементы управления Windows Forms будут удалены из **элементов** при листе Excel или документ Word в конструкторе Visual Studio. Это из-за технических ограничений или потому, что эта функция уже доступна в Word или Excel. Проекты Excel и Word поддерживают все элементы управления Windows Forms и другие компоненты, отображаемые в **элементов** Если документ имеет фокус, а также можно добавить элементы управления сторонних лист или документ.

> [!NOTE]
> Все элементы управления будут удалены из **элементов** когда документ защищен. Сведения о защите документа см. в разделе [защита в решениях уровня документа документов](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Сторонние элементы управления должны иметь <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут **true** для использования в решении Office.

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

При создании проекта Office уровня документа, использующего существующего документа Word или книги Excel, которая содержит элементы управления ActiveX, функциональные возможности элементов управления ActiveX не поддерживается. Тем не менее не поддерживается для добавления новых элементов управления ActiveX в документы из среды Visual Studio. Например, если документ имеет кнопку из **управления** панели Visual Basic для приложений (VBA), она будет продолжать макроса после использования документа в проекте Office. Тем не менее рекомендуется удалить элементы управления ActiveX и макросы VBA и заменить их с элементами управления Windows Forms и управляемого кода.

## <a name="see-also"></a>См. также

- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Элементы управления Windows Forms на общие сведения о документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)