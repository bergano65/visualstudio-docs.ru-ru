---
title: Константы IDE Документы Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710503"
---
# <a name="ide-constants"></a>Константы IDE

Класс <xref:Microsoft.VisualStudio.VSConstants> предоставляет константы, специфичные для интегрированной среды разработки (IDE) и ранее определяемые только в файлах заголовка.

## <a name="logical-and-physical-views"></a>Логические и физические взгляды

|Значение|Описание|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` обработчики должны передать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> это значение методу, чтобы получить **Open With** диалоговое поле, в данном случае на возможные представления кода.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` обработчики передают <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> это значение методу, чтобы получить **Open With** диалоговые окна, в этом случае населенные возможными <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> отладки представлений, которые отображают на тот же вид, как <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` обработчики передают <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> это значение методу, чтобы получить **Open With** диалоговую коробку, в данном случае для просмотра представления раценок **формы.**|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` обработчики передают <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> это значение методу, чтобы получить **Open With** диалоговые окна, в данном случае по умолчанию/основное представление фабрики редактора.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` обработчики передают <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> это значение методу, чтобы получить **open With** dialog, в этом для представления редактора текста документа или текста данных.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` обработчики передают <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> это значение методу, который побуждает пользователя выбирать, какое представление, определяемое пользователем, использовать.|

## <a name="editor-factory-flags"></a>Флаги фабрики редактора

|Значение|Описание|
|-----------|-----------------|
|[Cef. КлонФайл](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Устаревший флаг, комбинированный битомпоз в качестве первого параметра метода. <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>|
|[Cef. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Комбинированный битвр в <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>качестве первого параметра метода, это означает, что фабрика редактора должна выполнить необходимые исправления.|
|[Cef. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|В сочетании битва <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> в качестве первого параметра метода, этот флаг является взаимоисключающим [CEF. КлонФил .](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|
|[Cef. Молчание](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|В сочетании битва <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> в качестве первого параметра метода, это означает, что фабрика редактора должна создать редактор без отображения пользовательского интерфейса (UI).|

## <a name="visual-studio-errors"></a>Ошибки визуальной студии

|Значение|Описание|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Постоянное возвращение интерфейсами к асинхронному поведению, когда объект, о котором идет речь, уже занят|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Ошибка HRESULT, специфичная для Visual Studio для "Несовместимых данных документа".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Ошибка HRESULT, которая специфична для Visual Studio и указывает на "Пакет не загружен".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Ошибка HRESULT, которая специфична для Visual Studio, и это указывает на то, что "Проект уже существует".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Ошибка HRESULT, специфичная для Visual Studio и указываюа на «конфигурацию проекта не удалось».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Ошибка HRESULT, которая специфична для Visual Studio и указывает на "Проект не загружен".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Ошибка HRESULT, которая специфична для Visual Studio и указывает на "Решение уже открыто".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Ошибка HRESULT, которая специфична для Visual Studio и указывает на "Решение не открывается".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Возвращается путем создания интерфейсов, которые имеют <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> параметры для определения массива из интерфейса, но реализация может применяться только ко всем выводам.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Метод <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> возвращает это значение, если документ имеет формат, который не может быть открыт в редакторе.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Значение HRESULT, указывававо, что пользователь нажмет кнопку «Назад» в мастере Visual Studio.|

## <a name="visual-studio-constants"></a>Константы визуальной студии

|Значение|Описание|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Ошибка HRESULT, которая специфична для Visual Studio и указывает на "Проект направляется".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Константа, специфичная для Visual Studio для "маркера Toolbox".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Константа, специфичная для Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Studio для трансляции сообщения уведомлений с помощью метода, указывающем начало модальности.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Константа, специфичная для Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Studio для трансляции сообщения уведомлений с помощью метода, указывающем конец модальности.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Константа, специфичная для Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> Studio для трансляции сообщения уведомлений с помощью метода, указывающего на изменение метрик панели команд.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Константа, специфичная для Visual Studio, указывает на то, что файл cookie не установлен.|
|[ВСИТЕМИД. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Идентификатор элемента Visual Studio, представляющий отсутствие элемента проекта. Это значение используется, когда нет текущего выбора.|
|[ВСИТЕМИД. Корневой](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Идентификатор элемента Visual Studio, представляющий корень иерархии проекта и используемый для идентификации всей иерархии, в отличие от одного элемента.|
|[ВСИТЕМИД. Выбор](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Идентификатор элемента Visual Studio, представляющий выбранный в настоящее время элемент или элементы, который может включать корень иерархии.|

## <a name="ivsselectionevents"></a>IVsВыборСобытий
 Описывает, какой компонент IDE только что <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> был выбран, например, в вызове.

|Константа|Значение|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Константы, используемые для обозначения нового состояния выбора.

|Константа|Значение|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Константы диалога селектора компонентов

|Константа|Значение|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER No 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER No 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER No 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER No 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER No 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER No 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER No 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER No 1289|

## <a name="see-also"></a>См. также

- [Определяющие IDE команды для расширения проектных систем](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
