---
title: Как сделать команды доступными | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 78561db4bbf9517cc3fbcd5d9ac6ca36fcafbe05
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071230"
---
# <a name="making-commands-available"></a>Как сделать команды доступными
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При добавлении нескольких элементов VSPackage в Visual Studio, с помощью команд может стать overcrowded пользовательский интерфейс (UI). Вы можете программировать ваш пакет, чтобы помочь уменьшить эту проблему, следующим образом:  
  
- Программы пакета, чтобы он загружается, только когда пользователь требует его.  
  
- Программный пакет, его команды отображаются только в том случае, если они могут потребоваться в контексте текущего состояния среды разработки (IDE).  
  
## <a name="delayed-loading"></a>Отложенная загрузка  
 Типичный способ включения отложенной загрузки — для разработки VSPackage, чтобы ее команды отображаются в пользовательском Интерфейсе, но сам пакет не будет загружена, пока пользователь нажимает одну из команд. Для этого в vsct-файл, создайте команд, которые имеют не флаги команды.  
  
 В следующем примере показано определение команды меню в vsct-файл. Это команда, созданного шаблона пакета Visual Studio при **команды меню** выбран параметр в шаблоне.  
  
```xml  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 В примере если родительской группы, `MyMenuGroup`, является дочерним для элемента меню верхнего уровня, такие как **средства** меню, команда будет отображаться в соответствующее меню, но не будет загружен пакет, который выполняет команду, пока нажата команды пользователь. Тем не менее, запрограммировав команду, чтобы реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, вы можете включить пакет загружается, если сначала развернутое меню, содержащее команду.  
  
 Обратите внимание на то, что отложенную загрузку, также может повысить производительность при запуске.  
  
## <a name="current-context-and-the-visibility-of-commands"></a>Текущий контекст и подсветку  
 Можно программировать VSPackage команды, чтобы быть видимым или скрытым, в зависимости от текущего состояния данных VSPackage или действия, которые в настоящее время относятся. Вы можете включить VSPackage для задания состояния команд, как правило, используя реализацию <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> метода из <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, но это требует VSPackage для загрузки, прежде чем выполнять код. Вместо этого рекомендуется включить интегрированную среду разработки для управления видимостью команд без загрузки пакета. Чтобы сделать это, в vsct-файле, связать команды с один или несколько специальных контекстов пользовательского интерфейса. Эти контексты пользовательского интерфейса идентифицируются по GUID, известный как *идентификатор GUID контекста команды*.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отслеживает изменения, возникающие в результате действия пользователя, такие как загрузки проекта или собираетесь редактировать стандартных. По мере изменений автоматически изменяется внешний вид интегрированной среды разработки. В следующей таблице показаны четыре основных контекстов интегрированной среды разработки измените, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] мониторов.  
  
|Тип контекста|Описание|  
|---------------------|-----------------|  
|Тип активного проекта|Для большинства типов проектов это `GUID` значение совпадает со значением GUID VSPackage, который реализует проект. Тем не менее [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] проектов используется тип проекта `GUID` как значение.|  
|Активное окно|Как правило это последнего активного документа окна, которое устанавливает текущий контекст пользовательского интерфейса для сочетания клавиш. Тем не менее это может быть окно инструментов, которая содержит таблицу привязки ключей, похожий на внутренний веб-браузер. Для окон документов, с несколькими вкладками, такие как редактор HTML, каждая вкладка имеет другую команду контекст `GUID`.|  
|Active языковой службы|Служба языка, который связан с файлом, который отображается в текущий момент в текстовом редакторе.|  
|Активное окно|Окно инструментов, который открыт и имеет фокус.|  
  
 Пятый области основных контекста — это состояние пользовательского интерфейса интегрированной среды разработки. Контексты пользовательского интерфейса определяются контекстом активной команды `GUID`s, следующим образом:  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>
  
  Эти идентификаторы GUID, помечаются как активное или неактивное, в зависимости от текущего состояния интегрированной среды разработки. Несколько контекстов пользовательского интерфейса может быть активен в то же время.  
  
### <a name="hiding-and-displaying-commands-based-on-context"></a>Скрытие и отображение команд на основе контекста  
 Вы можно отобразить или скрыть команды пакета в интегрированной среде разработки без загрузки сам пакет. Для этого определения команды в vsct-файл пакета с помощью `DefaultDisabled`, `DefaultInvisible`, и `DynamicVisibility` команды флаги и добавление одного или нескольких [VisibilityItem](../../extensibility/visibilityitem-element.md) элементы [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) раздел. Когда контекст указанную команду `GUID` становится активным, команда будет отображаться без загрузки пакета.  
  
### <a name="custom-context-guids"></a>Идентификаторы GUID контекста пользовательского  
 Если контекст соответствующей команды, которые уже не определен идентификатор GUID, можно определить ее в VSPackage и затем запрограммировать его, чтобы быть активными или неактивными, чтобы управлять видимостью ваших команд. Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службу:  
  
- Зарегистрируйте идентификаторы GUID контекста (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> метод).  
  
- Получить состояние контекста `GUID` (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод).  
  
- Включить контекст `GUID`s, включения и отключения (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> метод).  
  
    > [!CAUTION]
    >  Убедитесь, что VSPackage не влияет на состояние любого существующего контекста GUID из-за других пакетов VSPackage может зависеть от них.  
  
## <a name="example"></a>Пример  
 В следующем примере команды VSPackage показано динамическую видимость команды, которая находится под управлением командных контекстов без загрузки VSPackage.  
  
 Команда имеет значение быть включена и отображается каждый раз, когда решение существует; то есть каждый раз, когда один из следующих контекст команды GUID активен:  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>  
  
  В примере обратите внимание на то, что каждый флаг команды — это отдельная [флаг команды](../../extensibility/command-flag-element.md) элемент.  
  
```  
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"   
        priority="0x0100" type="Button">  
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <CommandFlag>DefaultDisabled</CommandFlag>  
  <CommandFlag>DefaultInvisible</CommandFlag>  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <CommandName>cmdidMyCommand</CommandName>  
    <ButtonText>My Command name</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 Также Обратите внимание, что каждый контекст пользовательского интерфейса должны быть заданы в отдельном `VisibilityItem` элемент, как показано ниже.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
  
```  
  
## <a name="see-also"></a>См. также  
 [Команды MenuCommand и OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакеты VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Динамическое добавление элементов меню](../../extensibility/dynamically-adding-menu-items.md)
