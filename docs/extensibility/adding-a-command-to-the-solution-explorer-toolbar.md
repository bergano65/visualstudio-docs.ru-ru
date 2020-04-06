---
title: Добавление команды в панель инструментов Solution Explorer Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740333"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Добавление команды в панель инструментов Solution Explorer
В этом пошаговом показании, как добавить кнопку в панель инструментов **Solution Explorer.**

 Любая команда в панели инструментов или меню называется кнопкой в Visual Studio. При нажатии кнопки выполняется код в обработчике команд. Как правило, связанные команды объединяются для формирования одной группы. Меню или панели инструментов служат контейнерами для групп. Приоритет определяет порядок, в котором отдельные команды в группе отображаются в меню или на панели инструментов. Можно предотвратить отображение кнопки на панели инструментов или в меню, контролируя ее видимость. Команда, указанная `<VisibilityConstraints>` в разделе файла *.vsct,* отображается только в связанном контексте. Видимость не может быть применена к группам.

 Для получения дополнительной информации о меню, командах панели инструментов и файлах *.vsct* [см.](../extensibility/internals/commands-menus-and-toolbars.md)

> [!NOTE]
> Используйте файлы XML Command Table *(.vsct)* вместо конфигурации командной таблицы *(.ctc)* для определения того, как меню и команды отображаются в ваших VSPackages. Для получения дополнительной информации [см. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, см [Установка Визуальной студии SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Создание расширения с командой меню
 Создайте проект VSIX под названием `SolutionToolbar`. Добавьте шаблон элемента элемента меню под названием **ToolbarButton.** Для получения информации о том, как это сделать, [см. Создать расширение с командой меню.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Добавьте кнопку в панель инструментов Solution Explorer
 В этом разделе пошагового представления показано, как добавить кнопку в панель инструментов **Solution Explorer.** При нажатии кнопки код в методе обратного вызова запущен.

1. В файле *ToolbarButtonPackage.vsct* перейдите в `<Symbols>` раздел. Узла `<GuidSymbol>` содержится группа меню и команда, сгенерированная шаблоном пакета. Добавьте `<IDSymbol>` элемент в этот узлы, чтобы объявить группу, которая будет удерживать вашу команду.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. В `<Groups>` разделе после вступления в существующую группу определите новую группу, объявленную на предыдущем этапе.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Установка родительской пары GUID:ID и `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` помещает эту группу на панель инструментов Solution **Explorer** и устанавливает высокоприоритетное значение, ставит ее в следы других групп команд.

3. В `<Buttons>` разделе измените родительский идентификатор генерируемой `<Button>` записи, чтобы отразить группу, определенную на предыдущем этапе. Измененный `<Button>` элемент должен выглядеть следующим образом:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр.

     Панель инструментов **Solution Explorer** должна отображать новую кнопку команды справа от существующих кнопок. Значок кнопки является ударным.

5. Нажмите на новую кнопку.

     Диалоговое окно, которое имеет сообщение **ToolbarButtonPackage Внутри SolutionToolbar.ToolbarButton.MenuItemCallback ()** должны быть отображены.

## <a name="control-the-visibility-of-a-button"></a>Управление видимостью кнопки
 В этом разделе пошагового представления показано, как контролировать видимость кнопки на панели инструментов. Устанавливая контекст для одного или `<VisibilityConstraints>` нескольких проектов в разделе файла *SolutionToolbar.vsct,* вы ограничиваете кнопку, чтобы отойти только при открытии проекта или проектов.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Отобразить кнопку, когда один или несколько проектов открыты

1. В `<Buttons>` разделе *ToolbarButtonPackage.vsct*добавьте два флага `<Button>` команды к `<Strings>` `<Icons>` существующему элементу между тегами и тегами.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    `DefaultInvisible` Флаги `DynamicVisibility` и флаги должны быть `<VisibilityConstraints>` установлены таким образом, чтобы записи в разделе могли вс-венчиться.

2. Создайте `<VisibilityConstraints>` раздел с `<VisibilityItem>` двумя записями. Поместите новый раздел `</Commands>` сразу после закрытия тега.

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

    Каждый элемент видимости представляет собой условие, при котором отображается указанная кнопка. Чтобы применить несколько условий, необходимо создать несколько записей для одной и той же кнопки.

3. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр.

    Панель инструментов **Solution Explorer** не содержит кнопку strikethrough.

4. Откройте любое решение, содержащее проект.

    Кнопка strikethrough отображается на панели инструментов справа от существующих кнопок.

5. В меню **Файл** выберите пункт **Закрыть решение**. Кнопка исчезает из панели инструментов.

   Видимость кнопки контролируется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] до загрузки VSPackage. После загрузки VSPackage видимость кнопки контролируется VSPackage.  Для получения дополнительной информации [см. MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
