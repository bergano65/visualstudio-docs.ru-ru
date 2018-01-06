---
title: "Нового или измененного поведения с помощью редактора адаптеров | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c24b8c5520befcc204b59609b116d9d16ee26281
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Нового или измененного поведения с помощью редактора адаптеров
Если вы планируете использовать редактор адаптеры (или оболочки) вместо того чтобы использовать новый API обновление кода, написанного для более ранних версиях Visual Studio базового редактора, следует иметь в виду следующие различия в поведении редактора адаптеров по отношению к предыдущей базового редактора.  
  
## <a name="features"></a>Функции  
  
#### <a name="using-setsite"></a>С помощью SetSite()  
 Необходимо вызвать метод <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> при метод CoCreate текстовых буферов, представлениям текста и кода windows, прежде чем выполнять другие операции над ними. Однако это не требуется, если вы используете <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> их создания, так как вызов методов Create() эта служба самостоятельно <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Размещение IVsCodeWindow и IVsTextView собственное содержимое  
 Как можно разместить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в контент с помощью Win32 или режиме WPF. Тем не менее необходимо иметь в виду, что существуют некоторые различия в двух режимах.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>С помощью версии IVsCodeWindow Win32 и WPF  
 В окне редактора кода является производным от <xref:Microsoft.VisualStudio.Shell.WindowPane>, который реализует старую Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс, а также новый WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> интерфейса. Можно использовать <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> метод для создания на основе HWND среды размещения или <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> метод для создания среды размещения WPF. Редактор базовых всегда использует WPF, но можно создать тип область окна, который подходит для требований к размещению при внедрении непосредственно в собственное содержимое этой панели окна.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>С помощью версии IVsTextView Win32 и WPF  
 Можно задать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в режиме Win32 или WPF.  
  
 Когда фабрикой редакторов создает представления текста, по умолчанию она размещается внутри HWND, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> возвращает объект HWND. Не следует использовать этот режим, чтобы внедрить редакторе внутри элемента управления WPF.  
  
 Установка режима WPF представления текста, необходимо вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> и передайте <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> как один из инициализацию флагов в `InitView` параметра. Вы можете получить <xref:System.Windows.FrameworkElement> путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Режим WPF, отличается от Win32 двумя способами. Во-первых в контексте WPF может размещаться представления текста. Доступ к области WPF путем приведения <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> и вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Во-вторых, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> по-прежнему возвращает HWND, но этот HWND может использоваться только для проверки его положение и установить фокус на нем. Нельзя использовать HWND реагировать на сообщения WM_PAINT, так как это не повлияет на как редактор закрашивает окна. HWND присутствует только для того, чтобы упростить переход на новый редактор кода с помощью адаптеров. Настоятельно рекомендуется, что не следует использовать `VIF_NO_HWND_SUPPORT` Если требуются HWND для работы из-за ограничений в HWND, возвращенные `GetWindowHandle` при работе в этом режиме.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Передача массивов в качестве параметров в машинном коде  
 Существует множество методов в редакторе прежних версий API, которые имеют параметры, которые включают массива и его счетчик. Примеры:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 При вызове этих методов в машинном коде, необходимо передать только один элемент за раз. Если передано более одного элемента, вызов будет отклонена, из-за проблем с реализацией основного взаимодействия.  
  
 Проблема усложняется с методами таких как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Каждый раз при вызове этого метода очищает вышеупомянутых типов маркеров игнорируется, поэтому невозможно просто для того вызвать данный метод с тремя типами разные маркеры в три раза. Единственным средством является вызвать этот метод только в управляемом коде.  
  
#### <a name="threading"></a>Потоки  
 Адаптер буфера всегда следует вызывать из потока пользовательского интерфейса. Адаптер буфера — управляемого объекта, это означает, что вызов его из управляемого кода будут обходить маршалинг COM и вызов будет не автоматически маршалировать в потоке пользовательского интерфейса.  Адаптер буфера при вызове из фонового потока, необходимо использовать <xref:System.Windows.Threading.Dispatcher.Invoke%2A> или аналогичным способом.  
  
#### <a name="lockbuffer-methods"></a>Методы LockBuffer  
 Все методы LockBuffer() являются устаревшими. Примеры:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Фиксация событий  
 Зафиксировать события не поддерживаются. Вызов метода, который будет указано, для этих событий заставляет метод вернуть код ошибки.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Больше не срабатывают при выполнении Commit(). Вместо этого они срабатывают при каждом изменении текста.  
  
#### <a name="text-markers"></a>Текстовых маркеров:  
 Необходимо вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> объекты после их удаления. В предыдущих версиях требуется только для освобождения маркеров.  
  
#### <a name="line-numbers"></a>Номера строк  
 Для различных методов в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, номера строки соответствуют базового номера строк буфера, не строка номера коэффициент структурирование и перенос слов, как в Visual Studio 2008.  
  
 Затронутые методы включают следующее (список не является исчерпывающим):  
  
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
  
#### <a name="outlining"></a>структуризация  
 Клиенты <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> будет отображаться только для структурных областей, которые были добавлены с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Они не будут видеть нерегламентированных регионов, так как они не добавляются с помощью редактора адаптеров. Аналогичным образом эти клиенты не увидят добавленные языки (включая C# и C++), использующие новый редактор кода, а не адаптеров редактор областей структуры.  
  
#### <a name="line-heights"></a>Высота строки  
 В новом редакторе строк текста может иметь разные значения высоты, в зависимости от размера шрифта и возможные строки преобразования, может переместить линию относительно других строк. Высота строки, возвращаемые методами, такими как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> имеет высоту строки, с помощью размер шрифта по умолчанию с помощью преобразований нет строки. Это может или могут не отражать фактическую высоту строки в представлении.  
  
#### <a name="eventing-and-undo"></a>Обработка событий и отмены  
 В новом редакторе представления по-прежнему операций, таких как отрисовки и вызов событий постоянно, даже в том случае, если кластер отмены открыт. Это поведение отличается от прежних версий представлений, которые не выполнил этих операций до и после закрывающего кластера отмены.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Метод завершится с ошибкой при передаче в классе, который не реализует либо <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Больше не поддерживаются пользовательские всплывающие окна — определяемый владельцем Win32.  
  
#### <a name="smarttags"></a>Смарт-теги  
 Не поддерживается адаптер для смарт-тегов, созданных с помощью, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> интерфейсов.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch>не реализовано.  
  
## <a name="unimplemented-methods"></a>Нереализованные методы  
 Некоторые методы не были реализованы в адаптер текстового буфера, адаптер представления текста и текста слоя адаптера.  
  
|Интерфейс|Не реализовано|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)`не реализовано.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A>реализуется сетевые адаптеры, но игнорируется для структурирования пользовательского интерфейса.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A>реализуется сетевые адаптеры, но игнорируется для структурирования пользовательского интерфейса.|