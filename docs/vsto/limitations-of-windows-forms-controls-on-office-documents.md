---
title: Ограничения элементов управления Windows Forms в документах Office
description: Сведения об ограничениях методов и свойств элементов управления Windows Forms в документах Microsoft Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cc507d31f791a3f3d7addbcffc0b9b87963d443f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888723"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Ограничения элементов управления Windows Forms в документах Office

Существуют некоторые различия между Windows Formsными элементами управления, которые добавляются в Microsoft Office документы Word или Microsoft Office листы Excel, а также Windows Forms элементы управления, добавленные в Windows Forms. Например, при добавлении <xref:Microsoft.Office.Tools.Word.Controls.Button> элемента управления в документ такие свойства, как <xref:System.Windows.Forms.Control.Dock> , <xref:System.Windows.Forms.Control.Anchor> и, <xref:System.Windows.Forms.Control.TabIndex> не ведут себя так, как вы можете ожидать.

Многие из этих различий вызваны способом размещения Windows Forms элементов управления в документах. При добавлении элемента управления Windows Forms в документ [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] внедряет элемент управления ActiveX, который затем размещает в документе элемент управления Windows Forms. Элемент управления Windows Forms не внедряется непосредственно в документ.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Ограничения методов и свойств элементов управления Windows Forms

Существует ряд методов и свойств элементов управления Windows Forms, которые не работают одинаково в документе, как в Windows Forms, и поэтому рекомендуется не использовать их. Например, установка таких свойств, как <xref:System.Windows.Forms.Control.Dock> и, <xref:System.Windows.Forms.Control.Anchor> влияет только на расположение элемента управления по отношению к контейнеру элемента управления ActiveX, а не к документу. Ниже приведен список неподдерживаемых методов и свойств элементов управления Windows Forms для Word и Excel.

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

Также нельзя задать <xref:System.Windows.Forms.Control.Left> <xref:System.Windows.Forms.Control.Top> свойство или элементов управления Windows Forms, которые находятся в строке текста в документе Word. Windows Forms элементы управления добавляются в строку с текстом в следующих случаях:

- Вы программно добавляете элемент управления в документ Word и используете метод, указывающий диапазон для расположения.

- Элемент управления Windows Forms добавляется в документ Word во время разработки. Это можно изменить, изменив элемент управления в конструкторе.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Различия в элементах управления Windows Forms в документах Office

Windows Forms элементы управления обычно имеют такое же поведение в документе Office, как и в Windows Forms, но некоторые различия существуют. В следующей таблице описаны различия, которые существуют для Windows Forms элементов управления в документах Office.

|Функциональность|Разность|
|-------------------|----------------|
|Последовательность табуляции элементов управления|Нельзя перемещаться по элементам управления, размещенным на листе Excel или в документе Word.|
|Группирование элементов управления|Нельзя использовать <xref:System.Windows.Forms.GroupBox> элемент управления для размещения других элементов управления в документе Office. При добавлении нескольких переключателей непосредственно в документ переключатели не являются взаимоисключающими. Можно написать код, чтобы сделать переключатели взаимоисключающими. Однако предпочтительным подходом является добавление переключателей в пользовательский элемент управления, а затем Добавление пользовательского элемента управления в документ. Дополнительные сведения см. в разделе примеры элементов управления Word или примеры элементов управления Excel в примерах [разработки Office и пошаговых руководствах](../vsto/office-development-samples-and-walkthroughs.md).|
|Тип элемента управления|Windows Forms элементы управления, используемые в документах, упаковываются в класс, предоставляемый, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] который предоставляет элементам управления дополнительные функциональные возможности, характерные для листа Excel или документа Word. Например, если на листе Excel имеется элемент управления **Button** , обязательно укажите тип, <xref:Microsoft.Office.Tools.Excel.Controls.Button> а не <xref:System.Windows.Forms.Button> при ссылке или приведении объекта.|
|Расположение и размер элемента управления|Размер и расположение элемента управления определяются свойствами, которые являются частью элемента управления ActiveX контейнера. Свойства элемента управления ActiveX отличаются от значений эквивалентных свойств элемента управления Windows Forms. При задании `Top` свойств, `Left` , `Height` или `Width` элемента управления он измеряется в точках, а не в пикселях.|
|Расположение элемента управления в документах Word|При добавлении элементов управления в макет на основе потока следует помнить, что элементы управления будут передаваться вместе с содержимым при изменении содержимого. Нельзя привязать элемент управления к абзацу при перетаскивании его из **панели элементов** , поскольку элемент управления добавляется в документ Word в строке текста. Если для добавления элемента управления используется другой метод, например двойной щелчок элемента управления, элемент управления вставляется в соответствии с параметром Word, установленным для вставки изображений.<br /><br /> Нельзя задать `Left` `Top` свойство или элемента управления, который встроен в текст.<br /><br /> Нельзя размещать элементы управления в верхнем или нижнем колонтитуле или внутри вложенного документа.|
|События элемента управления|При выборе элемента управления он вызывает события в следующем порядке:<br /><br /> одного.  `Enter`<br />открыт.  `GotFocus`<br /><br /> При выборе элемента управления он вызывает события в следующем порядке:<br /><br /> одного.  `Leave`<br />открыт.  `Validating`<br />3-5.  `Validated`<br />четырех.  `LostFocus`|
|Масштабирование элемента управления|При изменении параметра масштаба документа на значение, отличное от 100%, элементы управления отключаются, хотя они отображаются вместе с документом. Например, если нажать кнопку, когда документ находится на 130% Zoom, будет отображено сообщение о том, что элемент управления был отключен до тех пор, пока для свойства Zoom не будет задано значение 100%. При изменении масштаба до 100% элементы управления будут работать правильно.|
|Управление значениями свойств|Несмотря на то, что свойства элементов управления в Windows Forms устанавливаются в целочисленное значение, для элементов управления в документе Word задается один элемент. В Excel значениям свойств элементов управления присваивается значение Double. Если `Height` свойство и `Width` элемента управления на листе превышает размер листа или экрана, значение усекается.|
|Изменение размера элемента управления|Если изменить размер элемента управления в документе с помощью одного из восьми маркеров изменения размера, новые измерения элемента управления не отражаются в окне **Свойства** до тех пор, пока элемент управления не будет выбран повторно.|
|Поведение элемента управления|При разбиении окна листа элементы управления на листе Excel могут работать непредсказуемым образом. Например, доступ к на <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> листе может быть доступен только в одном из окон.|
|Именование элементов управления|Зарезервированные слова нельзя использовать для именования элементов управления. Например, если добавить на <xref:Microsoft.Office.Tools.Excel.Controls.Button> лист и изменить имя на **System**, ошибки возникают при построении проекта.|
|Добавление элементов управления программными средствами|Не используйте конструктор элемента управления, чтобы добавить элемент управления в документ во время выполнения. Вместо этого используйте вспомогательные методы, предоставляемые [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Например, используйте метод, <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> чтобы добавить кнопку на лист. Если требуется добавить элемент управления, который не поддерживается этими вспомогательными методами, можно использовать `AddControl` метод. Дополнительные сведения см. [в разделе Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Копирование элементов управления|Если скопировать Windows Forms элемент управления и вставить его в документ во время выполнения, в документ будет вставлен пустой контейнер элемента управления ActiveX. Элемент управления Windows Forms не отображается в новом расположении, а код, лежащий в основе исходного элемента управления, не копируется в контейнерный элемент управления ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Ограничения в проектах уровня документа

Некоторые ограничения использования элементов управления Windows Forms в документах уникальны для проектов уровня документа.

### <a name="control-support-at-design-time"></a>Поддержка элементов управления во время разработки

Некоторые Windows Forms элементы управления удаляются из **панели элементов** при открытии листа Excel или документа Word в конструкторе Visual Studio. Это обусловлено техническими ограничениями или тем, что функциональность уже доступна в Word или Excel. Проекты Excel и Word поддерживают все элементы управления Windows Forms и другие компоненты, отображаемые на **панели элементов** , когда документ имеет фокус, а также можно добавлять сторонние элементы управления на лист или в документ.

> [!NOTE]
> При защите документа все элементы управления удаляются из **панели элементов** . Сведения о защите документов см. [в статье Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Для элементов управления сторонних разработчиков атрибут должен иметь значение <xref:System.Runtime.InteropServices.ComVisibleAttribute> **true** , чтобы их можно было использовать в решении Office.

Следующие элементы управления и компоненты недоступны на **панели элементов**:

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

### <a name="support-for-legacy-activex-controls"></a>Поддержка устаревших элементов управления ActiveX

При создании проекта Office на уровне документа, который использует существующий документ Word или книгу Excel, содержащую элементы управления ActiveX, функциональные возможности элементов управления ActiveX не теряются. Однако в Visual Studio не поддерживается добавление новых элементов управления ActiveX в документы. Например, если в документе Word есть кнопка из панели элементов « **элементы управления** », которая запускает макрос Visual Basic для приложений (VBA), он продолжит выполнение макроса после того, как документ будет использован в проекте Office. Однако рекомендуется удалить элементы управления ActiveX и макросы VBA и заменить их Windows Forms элементами управления и управляемым кодом.

## <a name="see-also"></a>См. также раздел

- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Общие сведения об элементах управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Добавление Windows Forms элементов управления в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
