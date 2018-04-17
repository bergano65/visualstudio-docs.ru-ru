---
title: Предоставление команды | Документы Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e20fd9b1b13dfc8159181ee2cb8f5d8966f6faf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="making-commands-available"></a>Предоставление команд
При добавлении нескольких пакетов VSPackage для Visual Studio с помощью команд может стать overcrowded пользовательский интерфейс (UI). Вы можете программировать пакета уменьшить эту проблему, как показано ниже:

-   Программа пакета, чтобы она загружается только тогда, когда пользователь требует его.

-   Программный пакет, чтобы его команды отображаются только в том случае, если они могут потребоваться в контексте текущего состояния интегрированной среды разработки (IDE).

## <a name="delayed-loading"></a>Отложенная загрузка
 Типичный способ включения отложенная загрузка — для разработки VSPackage, чтобы его команды отображаются в пользовательском Интерфейсе, но сам пакет не будет загружена, пока пользователь нажимает одну из команд. Для этого в vsct-файле, создание команд, которые имеют флаги не команды.

 В следующем примере показано определение команды меню в vsct-файл. Это команда, который создается Visual Studio шаблон пакета при **команду меню** выбран параметр в шаблоне.

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

 В примере если родительской группы, `MyMenuGroup`, является дочерним элементом меню верхнего уровня, такие как **средства** меню будет видимым в соответствующее меню команды, но пока нажата команда не будет загружен пакет, который выполняет команду пользователь. Однако с помощью программирования команда для реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса, можно включить пакет, чтобы загрузить сначала раскрываться меню, содержащее команду.

 Обратите внимание, что отложенной загрузкой может еще более повысить производительность при запуске.

## <a name="current-context-and-the-visibility-of-commands"></a>Текущий контекст и видимость команды
 Вы можете программировать VSPackage команды быть видимым или скрытым, в зависимости от текущего состояния данных VSPackage или действия, которые важны в настоящее время. Можно включить VSPackage для задания состояния команд, обычно с помощью реализации <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс, но это требует VSPackage для загрузки, прежде чем выполнять код. Вместо этого рекомендуется включить интегрированную среду разработки для управления видимостью команды без загрузки пакета. Для этого в vsct-файле связать команды с специальные контекстах пользовательского интерфейса. Эти контексты пользовательского интерфейса идентифицируются по GUID, известный как *контекста команды GUID*.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отслеживает изменения, возникающие в результате действия пользователя, например загрузки проекта или собираетесь редактировать построение. При возникновении изменений, автоматически изменяется внешний вид интегрированной среды разработки. В следующей таблице показаны четыре основных контекстов интегрированной среды разработки изменить [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] мониторов.

|Тип контекста|Описание|
|---------------------|-----------------|
|Тип активного проекта|Для большинства типов проектов это `GUID` значение совпадает со значением GUID из пакета VSPackage, реализующий проекта. Тем не менее [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] проектов используйте тип проекта `GUID` как значение.|
|Активное окно|Как правило это последнего окна активного документа, который устанавливает контекст текущего пользовательского интерфейса для сочетания клавиш. Тем не менее это может быть окно инструментов, которая содержит таблицу привязки ключей похожа на внутренний веб-браузер. Для окон документов, несколькими вкладками, таким как редактор HTML, в каждой табуляции имеет другую команду контекст `GUID`.|
|Активные языковой службы|Служба языка, связанный с файлом, который в настоящее время отображается в текстовом редакторе.|
|Активное окно|Окно инструментов, которое открыт и имеет фокус.|

 Пятый области Основные контекста — это состояние пользовательского интерфейса интегрированной среды разработки. Контексты пользовательского интерфейса идентифицируются активного контекста команд `GUID`s, следующим образом:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

 Эти идентификаторы GUID, помечаются как активным или неактивным, в зависимости от текущего состояния интегрированной среды разработки. Несколько контекстов пользовательского интерфейса может быть активен одновременно.

### <a name="hiding-and-displaying-commands-based-on-context"></a>Скрытие и отображение команд в зависимости от контекста
 Вы можно отобразить или скрыть команду пакет в среде разработки без загрузки сам пакет. Для этого определения команды в vsct-файле пакета с помощью `DefaultDisabled`, `DefaultInvisible`, и `DynamicVisibility` команда флаги и добавить один или несколько [VisibilityItem](../../extensibility/visibilityitem-element.md) элементы [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) раздела. Если контекст указанную команду `GUID` становится активным, команда отображается без загрузки пакета.

### <a name="custom-context-guids"></a>Пользовательский контекст GUID
 Если соответствующую команду контекста GUID еще не определен, можно определить ее в VSPackage и затем программировать быть активным или неактивным при необходимости для контроля видимости вашей команды. Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> службы:

-   Зарегистрируйте идентификаторы GUID контекста (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> метода).

-   Получает состояние контекста `GUID` (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метода).

-   Включить контекст `GUID`s и выключить (путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> метода).

    > [!CAUTION]
    > Убедитесь, что VSPackage не влияет на состояние любого существующего контекста GUID из-за других пакетов VSPackage может зависят от них.

## <a name="example"></a>Пример
 В следующем примере команды VSPackage показано динамическую видимость команды, которая управляется контексты команду без загрузки VSPackage.

 Команда имеет значение должен быть включен и отображен всякий раз, когда существует решение; то есть каждый раз, когда один из следующих контекст командной строки GUID активна:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>

В примере обратите внимание, что каждый флаг команды отдельного [флаг команды](../../extensibility/command-flag-element.md) элемента.

```xml
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

Также Обратите внимание, что каждый контекст пользовательского интерфейса должен быть присвоен в отдельном `VisibilityItem` элемента, как показано ниже.

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

- [Команды MenuCommand и OleMenuCommand](../../extensibility/menucommands-vs-olemenucommands.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Маршрутизация команд в пакетах VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Динамическое добавление элементов меню](../../extensibility/dynamically-adding-menu-items.md)