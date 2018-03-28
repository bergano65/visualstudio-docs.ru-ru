---
title: Константы интегрированной среды разработки | Документы Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0184cd4654f07b407a12ca12f0ff9da39c9ec890
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="ide-constants"></a>Константы интегрированной среды разработки

<xref:Microsoft.VisualStudio.VSConstants> Класс содержит константы, относящихся к интегрированной среды разработки (IDE), ранее были определены только в файлах заголовков.

## <a name="logical-and-physical-views"></a>Логические и физические представления

|Значение|Описание|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики следует передать это значение, чтобы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **открыть с помощью** диалоговое окно «», в данном случае на возможные представления кода.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **открыть с помощью** диалоговое окно, в этом случае заполняется возможные <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> отладки представления, которые сопоставляются с тем же самым представлением как <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **открыть с помощью** диалоговое окно «», в данном случае для **Просмотр формы** представления конструктора.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **открыть с помощью** диалоговое окно «», в данном случае представление по умолчанию источник фабрики редактора.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **открыть с помощью** диалогового окна для документа или данных представление текстового редактора.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, который предлагает пользователю выбрать пользовательские представления для использования.|

## <a name="editor-factory-flags"></a>Флаги фабрики редактора

|Значение|Описание|
|-----------|-----------------|
|[CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Устаревшие флаг побитового первого параметра вместе <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метод.|
|[CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Побитовый оператор, как первый параметр в сочетании <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, метод, это указывает фабрику редактора должен выполнить необходимые исправления.|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Побитовый оператор, как первый параметр в сочетании <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метода, этот флаг имеет взаимно exclusive [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF. Автоматическая](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Побитовый оператор, как первый параметр в сочетании <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> , это указывает фабрики редакторов следует создать редактор без отображения пользовательского интерфейса (UI).|

## <a name="visual-studio-errors"></a>Ошибки в Visual Studio

|Значение|Описание|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Константа, возвращенных интерфейсы для работы в асинхронном режиме при рассматриваемый в объект уже занят|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Значение HRESULT, относящиеся к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для «несовместимый документ данных».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Значение HRESULT, относящиеся к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Пакет не загружен».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Значение HRESULT, относящиеся к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и которая указывает на то, что «Проект уже существует.»|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Значение HRESULT, относящиеся к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «ошибка конфигурации проекта».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Значение HRESULT, относящиеся к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Не загружен проект».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Значение HRESULT, относящиеся к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Решения уже открыта.»|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Значение HRESULT, относящиеся к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Решение не открыто».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Возвращаемый построения интерфейсами, которые имеют параметры для указания массива из <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> интерфейса, но при реализации только метод можно применять все выходные данные.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Метод возвращает это значение, если документ имеет формат, который не может быть открыт в редакторе.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Значение HRESULT, указывающее, что пользователь нажатия кнопки "Назад" в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] мастера.|

## <a name="visual-studio-constants"></a>Константы Visual Studio

|Значение|Описание|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Значение HRESULT, относящиеся к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Перенаправленных проект».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для «маркера элементов».|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для широковещательной рассылки сообщения уведомления через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, который обозначает начало модальность.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для широковещательной рассылки сообщения уведомления через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, который указывает конец модальность.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для широковещательной рассылки сообщения уведомления через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, указывающее, что метрики командной строки были изменены.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , указывающее, что файл cookie не задано.|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Объект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] идентификатор элемента, которое представляет отсутствующий элемент проекта. Это значение используется в том случае, если нет текущего выделенного фрагмента.|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Объект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] идентификатор элемента, который представляет корень иерархии проекта и используется для идентификации всей иерархии, в отличие от одного элемента.|
|[VSITEMID. Выделенный фрагмент](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Объект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] идентификатор элемента, который представляет текущий выбранный элемент или элементы, которые могут включать корень иерархии.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Описывает, какие компоненты интегрированной среды разработки только что был выбран, в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> вызвать, например.

|Константа|Значение|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Константы, используемые для указания новое состояние выбора.

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

## <a name="component-selector-dialog-constants"></a>Константы диалоговое окно выбора компонентов

|Константа|Значение|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>См. также

- [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)