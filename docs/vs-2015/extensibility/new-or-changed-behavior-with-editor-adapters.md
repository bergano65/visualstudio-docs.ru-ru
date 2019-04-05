---
title: Нового или измененного поведения с помощью редактора адаптеров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79f0a700b64abffe93d79d284ce2f45a76b3e6a3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979507"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Нового или измененного поведения с помощью редактора адаптеров
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если при обновлении кода, написанного для более ранних версиях базовый редактор Visual Studio, и вы планируете использовать адаптеры редактора (или оболочки совместимости) вместо того чтобы использовать новый интерфейс API, следует иметь в виду следующие различия в поведении адаптеров редактора по отношению к предыдущей базовым редактором.  
  
## <a name="features"></a>Компоненты  
  
#### <a name="using-setsite"></a>С помощью SetSite()  
 Необходимо вызвать <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> при выполнить текстовых буферов, представлений текста и кода windows, прежде чем выполнять другие операции с ними. Тем не менее, это не является обязательным при использовании <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> для их создания, так как сами методы этой службы Create() вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Размещение IVsCodeWindow и IVsTextView собственное содержимое  
 Вы можете разместить оба <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в содержимого с помощью Win32 или WPF режиме. Тем не менее следует Имейте в виду, что существуют некоторые различия в двух режимах.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>С помощью версии IVsCodeWindow Win32 и WPF  
 В окне редактора кода является производным от <xref:Microsoft.VisualStudio.Shell.WindowPane>, который реализует старых Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> интерфейс, а также новый элемент управления WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> интерфейс. Можно использовать <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> метод для создания на основе HWND среды размещения или <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> метод для создания среды размещения WPF. Базовый редактор всегда использует WPF, но можно создать тип области окна, подходящий для требований к размещению этой области окна при внедрении непосредственно в собственного содержимого.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>С помощью версии IVsTextView Win32 и WPF  
 Можно задать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в режим Win32 или WPF.  
  
 Если фабрике редактора создает представление текста, по умолчанию, она размещается внутри HWND, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> возвращает HWND. Не следует использовать этот режим для внедрения редакторе внутри элемента управления WPF.  
  
 Установка текстового представления WPF режима, необходимо вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> и передайте <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> как часть инициализации флагом в `InitView` параметра. Вы можете получить <xref:System.Windows.FrameworkElement> путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Режим WPF отличается от режима Win32 двумя способами. Во-первых представление текста может размещаться в контексте WPF. Можно получить доступ к области WPF путем приведения <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> и вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Во-вторых, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> по-прежнему возвращает HWND, но этот HWND может использоваться только для проверки его положение и установить фокус на нем. Нельзя использовать этот HWND реагировать на сообщение WM_PAINT, так как он не затрагивает как редактор закрашивает окно. HWND присутствует только для облегчения перехода на новый редактор кода с помощью адаптеров. Настоятельно рекомендуется, что не следует использовать `VIF_NO_HWND_SUPPORT` Если необходимы для компонента HWND для работы из-за ограничений в HWND, возвращенные `GetWindowHandle` при работе в этом режиме.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Передача массивов в качестве параметров в машинном коде  
 Существует множество методов в редакторе устаревший API, которые имеют параметры, которые включают массива и его счетчик. Примеры:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 При вызове этих методов в машинном коде, необходимо передать только один элемент за раз. Если передать в более чем одного элемента, вызов будут отклонены, из-за проблем с основной реализацией взаимодействия.  
  
 Проблема является более сложным и методы, например <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Каждый раз при вызове этот метод очищает предыдущего списка типов маркеров игнорируются, поэтому можно просто вызвать этот метод три раза с тремя типами разные маркеры. Только рекомендация заключается в вызове этот метод только в управляемом коде.  
  
#### <a name="threading"></a>Потоки  
 Соответствующий адаптер буфера следует всегда вызывать из потока пользовательского интерфейса. Соответствующий адаптер буфера является управляемым объектом, это означает, что его вызова из управляемого кода, будут обходить маршалинг COM и вызов будет не автоматически переправлены в поток пользовательского интерфейса.  Соответствующий адаптер буфера при вызове из фонового потока, необходимо использовать <xref:System.Windows.Threading.Dispatcher.Invoke%2A> или аналогичным способом.  
  
#### <a name="lockbuffer-methods"></a>Методы LockBuffer  
 Все методы LockBuffer() являются устаревшими. Примеры:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Зафиксировать события  
 Зафиксировать события не поддерживаются. Вызов метода, это значит, что для этих событий вызывает метод вернет код ошибки.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents> Больше не работает в Commit(). Вместо этого они срабатывают при каждом изменении текста.  
  
#### <a name="text-markers"></a>Текстовые метки  
 Необходимо вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> объектов при их удалении. В предыдущих версиях вам требуется только для выпуска маркеров.  
  
#### <a name="line-numbers"></a>Номера строк  
 Для различных методов на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, номера строк соответствуют номера строк базового буфера, номера коэффициент структурирование и переноса слов, как и в Visual Studio 2008 не строк.  
  
 Методы, которые затронуты следующие (список не является исчерпывающим):  
  
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
  
#### <a name="outlining"></a>Структуризация  
 Клиенты <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> будут видеть только те области структуры, которые были добавлены с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Он не увидит нерегламентированных регионов, так как они не добавляются с помощью редактора адаптеров. Аналогичным образом эти клиенты не увидят добавленные языки, (включая C# и C++), при использовании нового редактора кода, а не адаптеров редактора областей структуры.  
  
#### <a name="line-heights"></a>Значения высоты строки  
 В новом редакторе строк текста может иметь разной высоты, в зависимости от размера шрифта и преобразования возможных строк, которые могут быть перемещены линии относительно других строк. Высота строки, возвращаемые методами, такими как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> является высота строки, с помощью размер шрифта по умолчанию с помощью преобразований не строки. Это может или может не отражать фактическую высоту строки в представлении.  
  
#### <a name="eventing-and-undo"></a>Регистрации событий и отмены  
 В новом редакторе представление продолжает выполнять операции, такие как подготовка к просмотру и вызов событий постоянно, в том случае, даже в том случае, когда кластер отмены открыт. Это поведение отличается от предыдущих версий представлений, которые не удалось выполнить эти операции до и после закрывающего кластера отмены.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Метод завершится с ошибкой при передаче в классе, который не реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Всплывающие окна настраиваемых Win32 рисуемый владельцем, больше не поддерживаются.  
  
#### <a name="smarttags"></a>Смарт-тегов  
 Отсутствует поддержка адаптера для смарт-тегов, созданных с помощью, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> интерфейсов.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> Не реализован.  
  
## <a name="unimplemented-methods"></a>Нереализованные методы  
 Некоторые методы не были реализованы на адаптер текстового буфера, адаптер представления текста и адаптер слой текста.  
  
|Интерфейс|Не реализовано|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` Не реализован.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> реализуется сетевые адаптеры, но игнорируется интерфейсом структуры пользовательского интерфейса.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> реализуется сетевые адаптеры, но игнорируется интерфейсом структуры пользовательского интерфейса.|
