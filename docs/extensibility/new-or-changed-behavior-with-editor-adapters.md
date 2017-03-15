---
title: "Нового или измененного поведения с помощью редактора адаптеров | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - поведение адаптера"
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Нового или измененного поведения с помощью редактора адаптеров
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если вы обновляете код, написанный для более ранних версий базового редактора Visual Studio, и вы планируете использовать адаптеры редактора \(или оболочки\) вместо нового API, следует учитывать следующие различия в поведении относительно предыдущего базового редактора адаптеров редактора.  
  
## Возможности  
  
#### С помощью SetSite\(\)  
 Необходимо вызвать метод <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> при CoCreate текстовых буферов, текстовых представлений и код windows, прежде чем выполнять другие операции с ними. Однако это необязательно при использовании <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> их создания, поскольку эта служба Create\(\) методов сами вызывают <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### Размещение IVsCodeWindow и IVsTextView собственное содержимое  
 Можно разместить как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в содержимого с помощью Win32 или WPF режиме. Однако следует иметь в виду, что существуют некоторые различия в двух режимах.  
  
##### С помощью версии IVsCodeWindow Win32 и WPF  
 В окне редактора кода является производным от <xref:Microsoft.VisualStudio.Shell.WindowPane>, реализующий старых Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс, а также новый WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> интерфейса. Можно использовать <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> метод для создания на основе HWND среде размещения или <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> метод для создания среды размещения WPF. Основной редактор всегда использует WPF, но можно создать тип области окна, отвечающих требованиям требований к размещению при внедрении этот панель окна непосредственно в собственное содержимое.  
  
##### С помощью версии IVsTextView Win32 и WPF  
 Можно задать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в режиме Win32 или WPF.  
  
 Когда фабрика редактора создает текстовое представление по умолчанию, она размещается внутри HWND, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> возвращает HWND. Не следует использовать этот режим, чтобы внедрить редакторе внутри элемента управления WPF.  
  
 Установка текстового представления WPF режима, необходимо вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> и передать в <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> как один инициализацию флагов в `InitView` параметр. Можно получить <xref:System.Windows.FrameworkElement> путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Режим WPF отличается от режима Win32 двумя способами. Во\-первых текстовое представление может размещаться в контексте WPF. Доступ к области WPF путем приведения <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> и вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Во\-вторых, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> по\-прежнему возвращает HWND, но HWND может использоваться только для проверки его положение и установить на него фокус. Нельзя использовать этот HWND ответить на сообщение WM\_PAINT, так как она не повлияет, как редактор рисует окно. HWND присутствует только для облегчения перехода на новый редактор кода с помощью адаптеров. Настоятельно рекомендуется, что не следует использовать `VIF_NO_HWND_SUPPORT` Если компонента требуется HWND для работы из\-за ограничений в HWND, возвращенный `GetWindowHandle` оставаясь в этом режиме.  
  
#### Передача массивов в качестве параметров в машинном коде  
 Существует множество методов в редакторе устаревшего API, которые имеют параметры, включающие массива и его счетчик. Ниже приведены примеры.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 При вызове этих методов в машинном коде, необходимо передать только один элемент за раз. Если передать более одного элемента, вызов отклоняется, из\-за проблем с основной реализации взаимодействия.  
  
 Проблема более сложные методы, такие как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. При каждом вызове этого метода очищает вышеупомянутых типов маркеров игнорируется, поэтому не можно просто вызвать этот метод три раза с тремя типами другой маркер. Единственным средством является вызывать этот метод только в управляемом коде.  
  
#### Работа с потоками  
 Следует всегда вызывать соответствующий адаптер буфера из потока пользовательского интерфейса. Адаптер буфера является управляемым объектом, это означает, что вызов его из управляемого кода будет выполнять маршалинг COM и вызов будет не автоматически переправлены в поток пользовательского интерфейса.  При вызове адаптер буфера из фонового потока, необходимо использовать <xref:System.Windows.Threading.Dispatcher.Invoke%2A> или аналогичным способом.  
  
#### Методы LockBuffer  
 Все методы LockBuffer\(\) являются устаревшими. Ниже приведены примеры.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### Фиксация событий  
 Фиксировать события не поддерживаются. Вызов метода, который предлагает для этих событий вызывает метод вернет код ошибки.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Больше не работает в Commit\(\). Вместо этого они срабатывают при каждом изменении.  
  
#### Маркеры текста  
 Необходимо вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> объекты после их удаления. В предыдущих версиях требуется только для выпуска маркеров.  
  
#### Номера строк  
 Для различных методов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, номера строк соответствуют номера строк базового буфера, номера коэффициент структурирование и перенос слов, как в Visual Studio 2008 не строк.  
  
 Методы, которые затронуты следующие \(список не является исчерпывающим\):  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### Структура  
 Клиенты <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> будет отображаться только для структурирования областей, которые были добавлены с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Он не увидит нерегламентированных областей, так как они не добавляются с помощью редактора адаптеров. Аналогично эти клиенты не увидят добавленные языки \(включая C\# и C\+\+\), использующие новый редактор кода, а не к адаптерам редактор областей структуры.  
  
#### Высота строки  
 В новый редактор строк текста может быть разной в зависимости от размера шрифта и возможные строки преобразования, которые могут перемещаться строки относительно других строк. Высота строки, возвращаемые методами, такими как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> имеет высоту строки, с помощью размер шрифта по умолчанию с помощью преобразований нет строки. Это может или может не отражать фактическую высоту строки в представлении.  
  
#### Регистрации событий и отмены  
 В новом редакторе представления продолжает выполнять операции, такие как отрисовки и вызов событий непрерывно, даже в том случае, если кластер отмены открыт. Это поведение отличается от прежних версий представлений, которые не удалось выполнить эти операции до и после закрывающего отмены кластера.  
  
#### IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Метод завершится с ошибкой при передаче в классе, который не реализует либо <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Всплывающие окна пользовательских Win32 определяемые владельцем больше не поддерживаются.  
  
#### Смарт\-теги  
 Не поддерживается адаптер для смарт\-теги, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> интерфейсов.  
  
#### DTE  
 <xref:EnvDTE80.IncrementalSearch> не реализовано.  
  
## Нереализованные методы  
 Некоторые методы не были реализованы на адаптер текстового буфера, адаптер представления текста и текста слоев адаптера.  
  
|Интерфейс|Не реализовано|  
|---------------|--------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` не реализовано.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> реализуется сетевые адаптеры, но игнорируется для структурирования пользовательского интерфейса.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> реализуется сетевые адаптеры, но игнорируется для структурирования пользовательского интерфейса.|