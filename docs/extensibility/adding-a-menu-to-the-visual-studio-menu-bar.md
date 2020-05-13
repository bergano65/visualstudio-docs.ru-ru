---
title: Добавление меню в меню Visual Studio Bar Документы Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740309"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Добавьте меню в панель меню Visual Studio

В этом пошаговом слове показано, как добавить меню в панель меню интегрированной среды разработки Visual Studio (IDE). Панель меню IDE содержит такие категории меню, как **файл,** **отодевать,** **посмотреть,** **окно**и **справку.**

Прежде чем добавлять новое меню в панель меню Visual Studio, подумайте, следует ли размещать команды в существующем меню. Для получения дополнительной информации о [размещении](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)команд см.

Меню заявлено в файле *.vsct* проекта. Для получения дополнительной информации о меню и файлах *.vsct* смотрите [команды, меню и панели инструментов.](../extensibility/internals/commands-menus-and-toolbars.md)

Выполнив это пошаговое пошаговое, вы можете создать меню под названием **TestMenu,** содержащее одну команду.

> [!NOTE]
> В VS 2019 меню верхнего уровня, вносимые расширениями, размещаются в меню **Расширений.**

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Создайте проект VSIX с пользовательским шаблоном элемента команд

1. Создайте проект VSIX под названием `TopLevelMenu`. Шаблон проекта VSIX можно найти в диалоге **нового проекта,** ища "vsix".  Для получения дополнительной информации [см. Создать расширение с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Когда проект откроется, добавьте шаблон пользовательского элемента командпод названием **TestCommand.** В **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** >  **новый пункт**. В диалоге **Добавить новый элемент,** перейдите на **Visual C / Расширяемость** и выберите **пользовательские команды**. В поле **«Имя»** в нижней части окна измените имя файла команды на *TestCommand.cs.*

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Создание меню в панели меню IDE

::: moniker range="vs-2017"

1. В **Solution Explorer**, открыть *TestCommandPackage.vsct*.

    В конце файла находится> \<узла символов, \<содержащего несколько узлов GuidSymbol>. В уде под названием guidTestCommandPackageCmdSet добавьте новый символ следующим образом:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Создайте \<пустое меню> \<узла в> узлах команд, как раз перед \<> групп. В \<> узла меню добавьте узла> \<меню следующим образом:

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

    В `guid` `id` меню и значениях указаны набор команд и конкретное меню в наборе команд.

    Значение `guid` `id` и значения родительского положения меню в разделе меню Visual Studio, содержащем меню «Инструменты» и «Дополнения».

    Значение строки `CommandName` указывает на то, что текст должен отображаться в пункте меню.

3. В \<разделе «Группы \<>» найдите \<групповую> и измените элемент родительского>, чтобы указать на меню, в меню, в который мы только что добавили:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Это делает группу частью нового меню.

::: moniker-end

::: moniker range=">=vs-2019"

1. В **Solution Explorer**, открыть *TopLevelMenuPackage.vsct*.

    В конце файла находится> \<узла символов, \<содержащего несколько узлов GuidSymbol>. В уде под названием guidTopLevelMenuPackageCmdSet добавьте новый символ следующим образом:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Создайте \<пустое меню> \<узла в> узлах команд, как раз перед \<> групп. В \<> узла меню добавьте узла> \<меню следующим образом:

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

    В `guid` `id` меню и значениях указаны набор команд и конкретное меню в наборе команд.

    Значение `guid` `id` и значения родительского положения меню в разделе меню Visual Studio, содержащем меню «Инструменты» и «Дополнения».

    Значение строки `CommandName` указывает на то, что текст должен отображаться в пункте меню.

3. В \<разделе «Группы \<>» найдите \<групповую> и измените элемент родительского>, чтобы указать на меню, в меню, в который мы только что добавили:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Это делает группу частью нового меню.

::: moniker-end

4. Найдите раздел `Buttons`. Обратите внимание, что [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] шаблон `Button` пакета создал элемент, `MyMenuGroup`который имеет свой родительский набор. В результате эта команда отображается в меню.

## <a name="build-and-test-the-extension"></a>Сборка и тестирование расширения

1. Выполните сборку решения и запустите отладку. Должен появиться экземпляр экспериментального экземпляра.

::: moniker range="vs-2017"

2. Панель меню в экспериментальном экземпляре должна содержать меню **TestMenu.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Меню **расширений** в экспериментальном экземпляре должно содержать меню **TestMenu.**

::: moniker-end

3. В меню **TestMenu** нажмите **Кнопка Команды тестирования Invoke.**

     Окно сообщений должно отображаться и отображать сообщение "Пакет TestCommand внутри TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>См. также

- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
