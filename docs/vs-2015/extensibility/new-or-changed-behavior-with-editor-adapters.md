---
title: Новое или измененное поведение с помощью адаптеров редактора | Документация Майкрософт
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
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194179"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Новое или измененное поведение с адаптерами редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если вы обновляете код, написанный для более ранних версий редактора Visual Studio Core, и планируете использовать адаптеры редактора (или оболочки) вместо использования нового API, следует помнить о следующих различиях в поведении адаптеров редактора по отношению к предыдущему основному редактору.  
  
## <a name="features"></a>Компоненты  
  
#### <a name="using-setsite"></a>Использование SetSite ()  
 Необходимо вызывать <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> при создании текстовых буферов, текстовых представлений и окон кода перед выполнением других операций с ними. Однако это необязательно, если вы используете <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> для создания, так как сами методы Create () этой службы вызывают <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Размещение Ивскодевиндов и IVsTextView в своем содержимом  
 Можно размещать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> и, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> в собственном содержимом, используя режим Win32 или WPF. Однако следует помнить, что в двух режимах есть некоторые различия.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Использование версий Ивскодевиндов для Win32 и WPF  
 Окно кода редактора является производным от <xref:Microsoft.VisualStudio.Shell.WindowPane> , который реализует старый интерфейс Win32, а <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> также новый <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> интерфейс WPF. Можно использовать <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> метод для создания среды размещения на основе HWND или <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> метод для создания среды размещения WPF. Базовый редактор всегда использует WPF, но вы можете создать область окна, которая соответствует вашим требованиям к размещению, если вы внедряете эту область окна непосредственно в свое содержимое.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Использование версий IVsTextView для Win32 и WPF  
 Можно задать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> режим Win32 или режим WPF.  
  
 Когда фабрика редактора создает текстовое представление, по умолчанию она размещается внутри HWND и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> ВОЗВРАЩАЕТ HWND. Не следует использовать этот режим для внедрения редактора в элемент управления WPF.  
  
 Чтобы присвоить текстовому представлению режим WPF, необходимо вызвать метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> и передать в <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> качестве одного из флагов инициализации в `InitView` параметре. Вы можете получить, <xref:System.Windows.FrameworkElement> вызвав <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 Режим WPF отличается от режима Win32 двумя способами. Во-первых, текстовое представление может размещаться в контексте WPF. Доступ к панели WPF осуществляется путем приведения <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> к <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> и вызова метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . Во-вторых, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> все равно ВОЗВРАЩАЕТ HWND, но этот HWND можно использовать только для проверки его расположения и установки фокуса на него. Этот HWND не следует использовать для реагирования на WM_PAINT сообщение, так как оно не влияет на прорисовку окна редактором. Этот HWND доступен только для того, чтобы упростить переход к новому коду редактора с помощью адаптеров. Настоятельно рекомендуется не использовать, `VIF_NO_HWND_SUPPORT` Если для работы компонента требуется дескриптор HWND из-за ограничений в HWND, возвращаемом в `GetWindowHandle` этом режиме.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Передача массивов в качестве параметров в машинном коде  
 В устаревшем API редактора существует множество методов, которые имеют параметры, включающие массив и его количество. Примеры:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 При вызове этих методов в машинном коде необходимо передавать только один элемент за раз. Если передать более одного элемента, вызов будет отклонен из-за проблем с основной реализацией взаимодействия.  
  
 Проблема усложняется с помощью таких методов, как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . При каждом вызове этого метода удаляется предыдущий список игнорируемых типов маркеров, поэтому невозможно просто вызвать этот метод три раза с тремя различными типами маркеров. Единственное решение — вызвать этот метод только в управляемом коде.  
  
#### <a name="threading"></a>Потоки  
 Следует всегда вызывать адаптер буфера из потока пользовательского интерфейса. Буферный адаптер является управляемым объектом. Это означает, что вызов в него из управляемого кода будет обходить COM-упаковку, а вызов не будет автоматически упакован в поток пользовательского интерфейса.  При вызове адаптера буфера из фонового потока необходимо использовать <xref:System.Windows.Threading.Dispatcher.Invoke%2A> или аналогичный метод.  
  
#### <a name="lockbuffer-methods"></a>Методы Локкбуффер  
 Все методы Локкбуффер () являются устаревшими. Примеры:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>События фиксации  
 События фиксации не поддерживаются. Вызов метода, который рекомендует эти события, приводит к тому, что метод возвращает код ошибки.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>текстедиторевентс  
 <xref:EnvDTE.TextEditorEvents>Больше не срабатывает при фиксации (). Вместо этого они срабатывают при каждом изменении текста.  
  
#### <a name="text-markers"></a>Текстовые маркеры  
 Необходимо вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> объектов при их удалении. В предыдущих версиях требуется только освободить маркеры.  
  
#### <a name="line-numbers"></a>Номера строк  
 Для различных методов в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> номера строк соответствуют базовым номерам строк буфера, а не номерам строк, которые являются коэффициентами в структурировании и переносом по словам, как в Visual Studio 2008.  
  
 К рассматриваемым методам относятся следующие (список не является исчерпывающим):  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Структуризация  
 Клиенты увидят <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> только те регионы структуры, которые были добавлены с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> или <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> . Они не будут видеть нерегламентированные регионы, так как они не добавляются через адаптеры редактора. Аналогичным образом эти клиенты не увидят областей структурирования, добавленных языками (включая C# и C++), которые используют новый код редактора, а не адаптеры редактора.  
  
#### <a name="line-heights"></a>Высота строк  
 В новом редакторе текстовые строки могут иметь разные значения высоты в зависимости от размера шрифта и возможных преобразований строк, которые могут перемещать линию относительно других линий. Высота строки, возвращаемая такими методами, как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> , является высотой строки с использованием размера шрифта по умолчанию без примененных преобразований линий. Эта высота может быть или не отражать фактическую высоту строки в представлении.  
  
#### <a name="eventing-and-undo"></a>События и Отмена  
 В новом редакторе представление продолжит выполнять такие операции, как визуализация и вызов событий постоянно, даже если открыт кластер отмены. Это поведение отличается от предыдущих представлений, которые не выполняли эти операции до закрытия кластера отмены.  
  
#### <a name="intellisense"></a>технология IntelliSense  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A>Метод завершится ошибкой, если передать класс, который не реализует, либо <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . Пользовательские всплывающие окна, отображаемые владельцем Win32, больше не поддерживаются.  
  
#### <a name="smarttags"></a>смарттагс  
 Смарт-теги, созданные с помощью интерфейсов,, и, не поддерживаются адаптерами <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> .  
  
#### <a name="dte"></a>ЦИФР  
 <xref:EnvDTE80.IncrementalSearch> не реализован.  
  
## <a name="unimplemented-methods"></a>Нереализованные методы  
 Некоторые методы не были реализованы в адаптере текстового буфера, адаптере текстового представления и адаптере текстового слоя.  
  
|Интерфейс|Не реализовано|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` не реализован.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> реализуется в адаптерах, но игнорируется в пользовательском интерфейсе структурирования.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> реализуется в адаптерах, но игнорируется в пользовательском интерфейсе структурирования.|
