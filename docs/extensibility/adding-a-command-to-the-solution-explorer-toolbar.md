---
title: Добавление команды на панель инструментов обозреватель решений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99a21a4dd4c39a4cefdf6be30171c503fc2ce005
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187105"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Добавление команды на панель инструментов обозреватель решений
В этом пошаговом руководстве показано, как добавить кнопку на панель инструментов **Обозреватель решений** .

 Любая команда на панели инструментов или меню называется кнопкой в Visual Studio. При нажатии кнопки выполняется код в обработчике команды. Как правило, связанные команды группируются, образуя одну группу. Меню или панели инструментов служат контейнерами для групп. Приоритет определяет порядок, в котором отдельные команды в группе отображаются в меню или на панели инструментов. Можно запретить отображение кнопки на панели инструментов или в меню, управляя ее видимостью. Команда, указанная в `<VisibilityConstraints>` разделе файла *. vsct* , отображается только в связанном контексте. Видимость не может быть применена к группам.

 Дополнительные сведения о меню, командах панелей инструментов и файлах *vsct* см. в разделе [команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Используйте файлы таблицы команд XML (*vsct*) вместо файлов конфигурации командной таблицы ( *. CTC*), чтобы определить, как меню и команды отображаются в пакетах VSPackage. Дополнительные сведения см. в разделе [Командная таблица Visual Studio (. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Необходимые компоненты
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню
 Создайте проект VSIX с именем `SolutionToolbar`. Добавьте шаблон пункта команды меню с именем **ToolbarButton**. Сведения о том, как это сделать, см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Добавление кнопки на панель инструментов обозреватель решений
 В этом разделе пошагового руководства показано, как добавить кнопку на панель инструментов **Обозреватель решений** . При нажатии кнопки выполняется код в методе обратного вызова.

1. В файле *тулбарбуттонпаккаже. vsct* перейдите к разделу `<Symbols>`. Узел `<GuidSymbol>` содержит группу меню и команду, созданную с помощью шаблона пакета. Добавьте элемент `<IDSymbol>` в этот узел, чтобы объявить группу, в которой будет содержаться команда.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. В разделе `<Groups>` после существующей записи группы определите новую группу, объявленную на предыдущем шаге.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Если задать для пары родительский идентификатор GUID: ID значение `guidSHLMainMenu` и `IDM_VS_TOOL_PROJWIN` поместит эту группу на панели инструментов **Обозреватель решений** и задать значение с высоким приоритетом, оно помещается после других групп команд.

3. В разделе `<Buttons>` измените родительский идентификатор созданной записи `<Button>`, чтобы она отражала группу, определенную на предыдущем шаге. Измененный элемент `<Button>` должен выглядеть следующим образом:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

     На панели инструментов **Обозреватель решений** должна отобразиться Кнопка Новая команда справа от существующих кнопок. Значок кнопки — это зачеркивание.

5. Нажмите кнопку Создать.

     Должно отобразиться диалоговое окно с сообщением **Тулбарбуттонпаккаже внутри солутионтулбар. ToolbarButton. менуитемкаллбакк ()** .

## <a name="control-the-visibility-of-a-button"></a>Управление видимостью кнопки
 В этом разделе пошагового руководства показано, как управлять видимостью кнопки на панели инструментов. Установив контекст для одного или нескольких проектов в разделе `<VisibilityConstraints>` файла *солутионтулбар. vsct* , вы ограничиваете кнопку, чтобы она отображалась только в том случае, если проект или проекты открыты.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Отображение кнопки при открытии одного или нескольких проектов

1. В разделе `<Buttons>` *тулбарбуттонпаккаже. vsct*добавьте два флага команды в существующий элемент `<Button>` между тегами `<Strings>` и `<Icons>`.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Чтобы записи в разделе `<VisibilityConstraints>` вступили в силу, необходимо задать флаги `DefaultInvisible` и `DynamicVisibility`.

2. Создайте раздел `<VisibilityConstraints>` с двумя записями `<VisibilityItem>`. Разместите новый раздел сразу после закрывающего тега `</Commands>`.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    Каждый элемент видимости представляет условие, при котором отображается указанная кнопка. Чтобы применить несколько условий, необходимо создать несколько записей для одной и той же кнопки.

3. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

    Панель инструментов **Обозреватель решений** не содержит кнопку зачеркивание.

4. Откройте любое решение, содержащее проект.

    Кнопка зачеркнутый появляется на панели инструментов справа от существующих кнопок.

5. В меню **файл** выберите пункт **Закрыть решение**. Кнопка исчезает с панели инструментов.

   Видимость кнопки управляется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] до загрузки VSPackage. После загрузки VSPackage видимость кнопки управляется пакетом VSPackage.  Дополнительные сведения см. в разделе [команды MenuCommand и олеменукоммандс](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)