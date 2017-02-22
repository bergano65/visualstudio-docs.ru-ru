---
title: "Доступность команд | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "меню [Visual Studio SDK] команды"
  - "Советы и рекомендации, команд меню и панели инструментов"
  - "рекомендации по использованию панели инструментов [Visual Studio]"
  - "команды меню, советы и рекомендации"
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 35
caps.handback.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
---
# Доступность команд
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

При добавлении нескольких пакетов VSPackages для Visual Studio с помощью команд может стать overcrowded пользовательский интерфейс \(UI\). Вы можете программировать пакета поможет уменьшить эту проблему, следующим образом:  
  
-   Программа пакета, чтобы он загружается, только когда пользователь требует его.  
  
-   Программный пакет, чтобы его команды отображаются только в том случае, если они могут понадобиться в контексте текущего состояния интегрированную среду разработки \(IDE\).  
  
## Отложенная загрузка  
 Типичный способ включить отложенная загрузка — для разработки VSPackage, чтобы его команды отображаются в пользовательском Интерфейсе, но сам пакет не будет загружена, пока пользователь нажимает одну из команд. Для этого в файле .vsct создайте команд, которые имеют флаги не команды.  
  
 Следующий пример показывает определение команды меню из файла .vsct. Это команда, который создается Visual Studio шаблон пакета при **команды меню** флажок в шаблоне.  
  
 [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
 В примере Если родительская группа `MyMenuGroup`, является дочерним для элемента меню верхнего уровня, таких как **средства** меню, команда будет отображаться в меню, но не будет загружен пакет, который выполняет команду, пока пользователь щелкает команду. Однако по программированию команду, чтобы реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, можно включить пакет загрузки сначала раскрываться меню, содержащее команду.  
  
 Обратите внимание, что отложенной загрузки может привести к повышению производительности при запуске.  
  
## Текущий контекст и подсветку синтаксиса  
 Можно запрограммировать VSPackage команды быть видимым или скрытым, в зависимости от текущего состояния данных VSPackage и действиях, которые в данный момент относятся. Можно включить VSPackage для задания состояния команд, обычно с помощью реализации <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, но это требует VSPackage для загрузки, прежде чем выполнять код. Вместо этого рекомендуется включить интегрированную среду разработки для управления видимостью команды без загрузки пакета. Для этого в файле .vsct сопоставления команд с помощью специальных контекстов пользовательского интерфейса. Эти контексты пользовательского интерфейса идентифицируются по GUID, известный как *контекст командной строки GUID*.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отслеживает изменения, возникающие в результате действия пользователя, такие как загрузке проекта или планируется создание редактирование. По мере изменений автоматически изменяется внешний вид интегрированной среды разработки. В следующей таблице показаны четыре основных контексты среды IDE, изменить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] мониторов.  
  
|Тип контекста|Описание|  
|-------------------|--------------|  
|Тип активного проекта|Для большинства типов проектов это `GUID` значение будет совпадать с GUID VSPackage, который реализует проекта. Однако [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] проектов использовать тип проекта `GUID` как значение.|  
|Активное окно|Как правило это окна последнего активного документа, который устанавливает контекст текущего пользовательского интерфейса для привязки клавиш. Тем не менее это может быть окна инструментов, которое содержит таблицу привязки клавиш, подобное внутреннего веб\-обозревателя. Для документов с несколькими вкладками windows как редактор HTML, каждая вкладка имеет контекст другой команде `GUID`.|  
|Служба Active языка|Служба языка, связанный с файлом, который в текущий момент отображается в текстовом редакторе.|  
|Активное окно|Окно инструментов, которое является открытым и имеет фокус.|  
  
 Пятый область основного контекста является состояние пользовательского интерфейса интегрированной среды разработки. Контексты пользовательского интерфейса определяются активного контекста команд `GUID`s, как показано ниже:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 Эти идентификаторы GUID, помечаются как активным или неактивным, в зависимости от текущего состояния интегрированной среды разработки. В то же время может быть активной нескольких контекстов пользовательского интерфейса.  
  
### Скрытие и отображение команд в зависимости от контекста  
 Можно отобразить или скрыть команды package в Интегрированной среде разработки без загрузки сам пакет. Для этого определите команды в файле .vsct пакета с помощью `DefaultDisabled`, `DefaultInvisible`, и `DynamicVisibility` команда флаги и добавить один или несколько [VisibilityItem](../../extensibility/visibilityitem-element.md) элементы [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) раздел. Когда контекста указанной команды `GUID` становится активным, эта команда будет отображаться без загрузки пакета.  
  
### Идентификаторы GUID пользовательского контекста  
 Если соответствующую команду контекста GUID еще не определен, можно определить ее в VSPackage и затем ей быть активными или неактивными, необходимые для управления видимостью вашей команды. Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы:  
  
-   Зарегистрируйте идентификаторы GUID контекста \(путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> метод\).  
  
-   Получить состояние контекста `GUID` \(путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод\).  
  
-   Включение контекста `GUID`s и отключать \(путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> метод\).  
  
    > [!CAUTION]
    >  Убедитесь, что VSPackage не влияет на состояние любого существующего контекста GUID поскольку их могут зависеть другие пакеты VSPackage.  
  
## Пример  
 В следующем примере команды VSPackage показано динамическое видимость команды, которая управляется контекстов команду без загрузки VSPackage.  
  
 Набор команд должен быть включен и отображен всякий раз, когда решение существует; то есть всякий раз, когда один из следующих контекст командной строки GUID активен:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 В этом примере обратите внимание, что каждый флаг команды отдельные [флаг команды](../../extensibility/command-flag-element.md) элемента.  
  
 [!CODE [DynamicVisibility#01](DynamicVisibility#01)]  
  
 Также Обратите внимание, что каждый контекст пользовательского интерфейса должно быть задано в отдельном `VisibilityItem` элемента, как показано ниже.  
  
 [!CODE [DynamicVisibility#02](DynamicVisibility#02)]  
  
## См. также  
 [команды MenuCommand и OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакеты VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Динамическое добавление элементов меню](../../extensibility/dynamically-adding-menu-items.md)