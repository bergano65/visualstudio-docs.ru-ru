---
title: "Константы интегрированной среды разработки | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интегрированная среда разработки, ошибки"
  - "логические представления"
  - "ошибки [Visual Studio], интегрированной среды разработки"
  - "Константы контекста пользовательского интерфейса"
  - "константы, интегрированной среды разработки Visual Studio"
  - "Интегрированная среда разработки, константы"
  - "физические представления"
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Константы интегрированной среды разработки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.VSConstants> Класс предоставляет константы, которые относятся к интегрированной среде разработки \(IDE\) и которые были ранее определены только в файлах заголовков.  
  
## Логические и физические представления  
  
|Значение|Описание|  
|--------------|--------------|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики следует передавать значение <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **Открыть с помощью** диалоговом в данном случае на возможные представления кода.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **Открыть с помощью** диалогового окна, в этом случае заполняется возможные <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging> отладку представлений, которые сопоставляются с тем же самым представлением как <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Designer>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **Открыть с помощью** окно, в данном случае для **Просмотр формы** представления конструктора.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Primary>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **Открыть с помощью** диалоговом в данном случае представление по умолчанию источник фабрики редактора.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_TextView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, чтобы получить **Открыть с помощью** диалогового окна для документа или данных представление текстового редактора.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_UserChooseView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` обработчики передает это значение для <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод, который предлагает пользователю выбрать пользовательские представления для использования.|  
  
## Флаги фабрики редактора  
  
|Значение|Описание|  
|--------------|--------------|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>|Устаревшие флаг в сочетании побитового как первый параметр <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метода.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENASNEW>|Побитовый оператор, как первый параметр в сочетании <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, метод, это указывает фабрики редактора следует выполнить необходимые исправления.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENFILE>|Побитовый оператор, как первый параметр в сочетании <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> метода, этот флаг имеет взаимно exclusive <xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_SILENT>|Побитовый оператор, как первый параметр в сочетании <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> это указывает фабрики редактора следует создать редактор без отображения пользовательского интерфейса \(UI\).|  
  
## Ошибки в Visual Studio  
  
|Значение|Описание|  
|--------------|--------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Константа, возвращенных интерфейсы для работы в асинхронном режиме при нужного объекта в уже занят.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Ошибки HRESULT, который относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для «несовместимый документ данных».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Ошибки HRESULT, который относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Пакет не загружен».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Ошибки HRESULT, который относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и которая указывает на то, что «Проект уже существует.»|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Ошибки HRESULT, который относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «ошибка конфигурации проекта».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Ошибки HRESULT, который относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Не загружен проект».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Ошибки HRESULT, который относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Решение уже открыто».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Ошибки HRESULT, который относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Решений не открыто».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Возвращаемый построения интерфейсов, которые имеют параметры для указания массива из <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> интерфейс, но реализацию можно применять только метод для всех выходных данных.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Метод возвращает это значение, если документ имеет формат, который не может быть открыт в редакторе.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Значение HRESULT, указывающее, что пользователь нажатия кнопки "Назад" в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] мастера.|  
  
## Константы Visual Studio  
  
|Значение|Описание|  
|--------------|--------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Ошибки HRESULT, который относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и указывает «Пересылаются проект».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для «маркером элементов».|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для широковещательной рассылки сообщения уведомления через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, который обозначает начало модальность.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для широковещательной рассылки сообщения уведомления через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, который указывает конец модальность.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для широковещательной рассылки сообщения уведомления через <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> метод, указывающее, что метрики командной строки были изменены.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Константа, которая относится к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] указывающее, что файл cookie не задано.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] идентификатор элемента, который представляет отсутствие элемента проекта. Это значение используется, если нет текущего выделенного фрагмента.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] идентификатор элемента, который представляет корень иерархии проекта и используется для идентификации всей иерархии, в отличие от одного элемента.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] идентификатор элемента, который представляет текущий выбранный элемент или элементы, которые могут включать корень иерархии.|  
  
## IVsSelectionEvents  
 Описывает, каким компонентом IDE только после выбора в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> вызова, например.  
  
|Константа|Значение|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.VSConstants.DocumentFrame>|0x2|  
|<xref:Microsoft.VisualStudio.VSConstants.PropertyBrowserSID>|0x4|  
|<xref:Microsoft.VisualStudio.VSConstants.StartupProject>|0x3|  
|<xref:Microsoft.VisualStudio.VSConstants.UndoManager>|0x0|  
|<xref:Microsoft.VisualStudio.VSConstants.UserContext>|0x5|  
|<xref:Microsoft.VisualStudio.VSConstants.WindowFrame>|0x1|  
  
## VSSELELEMID  
 Константы, используемые для указания нового состояния выделения.  
  
|Константа|Значение|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## Константы диалоговое окно выбора компонентов  
  
|Константа|Значение|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM\_USER \+ 1280|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM\_USER \+ 1281|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM\_USER \+ 1290|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM\_USER \+ 1287|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM\_USER \+ 1285|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM\_USER \+ 1288|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM\_USER \+ 1286|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM\_USER \+ 1289|  
  
## См. также  
 [Команды, определенные в интегрированной среде разработки, для расширения системы проектов](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)