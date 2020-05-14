---
title: Обеспечение доступности команд (ru) Документы Майкрософт
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707332"
---
# <a name="making-commands-available"></a>Обеспечение доступности команд

Когда несколько VSPackages добавляются в Visual Studio, пользовательский интерфейс (UI) может быть переполнен командами. Вы можете запрограммировать свой пакет, чтобы помочь уменьшить эту проблему, следующим образом:

- Программа пакет так, что он загружается только тогда, когда пользователь требует его.

- Программа пакет, так что его команды отображаются только тогда, когда они могут потребоваться в контексте текущего состояния интегрированной среды разработки (IDE).

## <a name="delayed-loading"></a>Задержка погрузки

Типичный способ включить задержку загрузки — спроектировать VSPackage таким образом, чтобы его команды отображались в пользовательском интерфейсе, но сам пакет не загружается до тех пор, пока пользователь не нажмет одну из команд. Для достижения этой цели в файле .vsct создайте команды, не имеющие флагов команд.

В следующем примере показано определение команды меню из файла .vsct. Это команда, генерируемая шаблоном пакета Visual Studio при выборе опции **Menu Command** в шаблоне.

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

В примере, если родительская группа `MyMenuGroup`является ребенком меню верхнего уровня, такого как меню **«Инструменты»,** в этом меню будет видно, но пакет, выполняющий команду, не будет загружен до тех пор, пока команда не нажмет на кнопку пользователя. Однако, запрограммировав команду <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> для реализации интерфейса, можно включить загрузку пакета при первом расширении меню, содержащего команду.

Обратите внимание, что задержка загрузки может также улучшить производительность запуска.

## <a name="current-context-and-the-visibility-of-commands"></a>Текущий контекст и видимость команд

Команды VSPackage можно запрограммировать на видимые или скрытые команды VSPackage в зависимости от текущего состояния данных VSPackage или действий, которые в настоящее время актуальны. Можно включить VSPackage для настройки состояния своих команд, как правило, с помощью реализации <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> метода из <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса, но это требует загрузки VSPackage, прежде чем он сможет выполнить код. Вместо этого мы рекомендуем IDE управлять видимостью команд без загрузки пакета. Для этого в файле .vsct связывайкоманды команд с одним или одним из специальных контекстов uI. Эти контексты uI идентифицируются GUID, известным как *GUID командного контекста.*

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]отслеживает изменения, которые возникают в результате действий пользователя, таких как загрузка проекта или переход от редактирования к зданию. По мере изменения внешний вид IDE автоматически изменяется. В следующей таблице показаны четыре основных контекста изменения IDE, которые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отслеживаются.

| Тип контекста | Описание |
|-------------------------| - |
| Тип активного проекта | Для большинства типов `GUID` проектов это значение такое же, как GUID VSPackage, который реализует проект. Однако [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] проекты используют `GUID` тип проекта в качестве значения. |
| Активное окно | Как правило, это последнее активное окно документа, которое устанавливает текущий контекст единоборств для ключевых привязок. Тем не менее, это также может быть окно инструмента, которое имеет ключевой таблицы связывания, которая напоминает внутренний веб-браузер. Для многоэлементных окон документов, таких как HTML-редактор, `GUID`каждая вкладка имеет другой контекст команды. |
| Служба активного языка | Языковая служба, связанная с файлом, который в настоящее время отображается в текстовом редакторе. |
| Окно активного инструмента | Окно инструмента, которое открыто и имеет фокус. |

Пятая важная область контекста — состояние миз-вопросов IDE. Контексты uI идентифицируются `GUID`активным контекстом командования следующим образом:

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

Эти GUID помечены как активные или неактивные, в зависимости от текущего состояния IDE. Несколько контекстов uI могут быть активны одновременно.

### <a name="hide-and-display-commands-based-on-context"></a>Скрыть и отобразить команды в зависимости от контекста

Вы можете отобразить или скрыть команду пакета в IDE без загрузки самого пакета. Для этого определите команду в файле .vsct `DefaultDisabled`пакета, `DefaultInvisible`используя `DynamicVisibility` флаги, а также командуйте флагами и добавляя один или несколько элементов [VisibilityItem](../../extensibility/visibilityitem-element.md) в раздел [VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md) Когда определенный `GUID` контекст команды становится активным, команда отображается без загрузки пакета.

### <a name="custom-context-guids"></a>Пользовательские графические интерфейсы контекста

Если уже определен соответствующий контекст команды GUID, можно определить его в VSPackage, а затем запрограммировать его на активную или неактивную видимость команд. Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> услугу для:

- Регистрация контекста GUIDs <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (по звонку метода).

- Получите состояние контекста `GUID` (позвонив по методу). <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>

- Включите и выключите `GUID` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> контекст (позвонив по методу).

    > [!CAUTION]
    > Убедитесь, что ваш VSPackage не влияет на состояние любого существующего контекста GUID, потому что другие VSPackages могут зависеть от них.

## <a name="example"></a>Пример

Следующий пример команды VSPackage демонстрирует динамическую видимость команды, которая управляется контекстами команд без загрузки VSPackage.

Команда устанавливается для включения и отображения всякий раз, когда существует решение; то есть, когда один из следующих контексте команды GUIDs активен:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

В примере обратите внимание, что каждый флаг команды является отдельным элементом [флага командования.](../../extensibility/command-flag-element.md)

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

Также обратите внимание, что каждый контекст `VisibilityItem` uI должен быть приведен в отдельном элементе, а именно.

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

- [Добавление команды в панель инструментов Solution Explorer](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Маршрутизация команд в пакетах VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Динамическое добавление элементов меню](../../extensibility/dynamically-adding-menu-items.md)
