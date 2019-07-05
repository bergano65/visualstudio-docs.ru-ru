---
title: Добавление меню в строке меню Visual Studio | Документация Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a28e7f69ed8e9a76e11d8892ee677435f75c99b2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349796"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Добавить меню в строке меню Visual Studio

В этом пошаговом руководстве показано, как добавлять меню в строку меню среды разработки Visual Studio (IDE). Интегрированная среда разработки строка меню содержит меню категории, такие как **файл**, **изменить**, **представление**, **окно**, и **помочь** .

Перед добавлением нового меню в строке меню Visual Studio, учитывать ли ваши команды должно размещаться в существующее меню. Дополнительные сведения о размещении команды, см. в разделе [меню и команд для Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Меню объявляются в *.vsct* файл проекта. Дополнительные сведения о меню и *.vsct* файлы, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).

Выполнив это пошаговое руководство, можно создать меню с именем **TestMenu** , содержащий одну команду.

> [!NOTE]
> В VS 2019 г., меню верхнего уровня, порожденного расширения помещаются в **расширения** меню.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Создание проекта VSIX, который содержит шаблон элемента настраиваемую команду

1. Создайте проект VSIX с именем `TopLevelMenu`. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, выполняя поиск «vsix».  Дополнительные сведения см. в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. При открытии проекта, Добавление пользовательской команды шаблона элемента с именем **тестовую команду**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить** >  **новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя командного файла для *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Создание меню в строке меню интегрированной среды разработки

::: moniker range="vs-2017"

1. В **обозревателе решений**откройте *TestCommandPackage.vsct*.

    В конце файла, не существует \<символы > узел, который содержит несколько \<GuidSymbol > узлов. В узле с именем guidTestCommandPackageCmdSet добавьте новый символ, следующим образом:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Создать пустой \<меню > узел в \<команды > узел, непосредственно перед \<группы >. В \<меню > узел, добавьте \<меню >, как показано ниже:

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid` И `id` значения меню задают набор команд и меню в набор команд.

    `guid` И `id` значения родительского размещения меню в разделе меню Visual Studio, содержащий меню «Сервис» и «Add-ins.

    Значение `CommandName` строка указывает, что текст должен отображаться в элементе меню.

3. В \<группы > найдите \<группы > и измените \<родительского > элемент меню, который мы только что добавили:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    В результате группа частью нового меню.

::: moniker-end

::: moniker range=">=vs-2019"

1. В **обозревателе решений**откройте *TopLevelMenuPackage.vsct*.

    В конце файла, не существует \<символы > узел, который содержит несколько \<GuidSymbol > узлов. В узле с именем guidTopLevelMenuPackageCmdSet добавьте новый символ, следующим образом:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Создать пустой \<меню > узел в \<команды > узел, непосредственно перед \<группы >. В \<меню > узел, добавьте \<меню >, как показано ниже:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid` И `id` значения меню задают набор команд и меню в набор команд.

    `guid` И `id` значения родительского размещения меню в разделе меню Visual Studio, содержащий меню «Сервис» и «Add-ins.

    Значение `CommandName` строка указывает, что текст должен отображаться в элементе меню.

3. В \<группы > найдите \<группы > и измените \<родительского > элемент меню, который мы только что добавили:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    В результате группа частью нового меню.

::: moniker-end

4. Найти `Buttons` раздел. Обратите внимание, что [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создала шаблон пакета `Button` элемент, имеющий родительского присвоено `MyMenuGroup`. Таким образом эта команда появляется в меню.

## <a name="build-and-test-the-extension"></a>Сборка и тестирование расширения

1. Выполните сборку решения и запустите отладку. Экземпляр экспериментального экземпляра должна появиться.

::: moniker range="vs-2017"

2. В строке меню в экспериментальном экземпляре должен содержать **TestMenu** меню.

::: moniker-end

::: moniker range=">=vs-2019"

2. **Расширения** меню в экспериментальном экземпляре должен содержать **TestMenu** меню.

::: moniker-end

3. На **TestMenu** меню, щелкните **вызвать команду проверки**.

     Появится окно сообщения с отображения сообщения «Тестовую команду пакета внутри TopLevelMenu.TestCommand.MenuItemCallback()».

## <a name="see-also"></a>См. также

- [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)