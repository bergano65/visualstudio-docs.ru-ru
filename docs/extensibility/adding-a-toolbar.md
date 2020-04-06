---
title: Добавление панели инструментов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740217"
---
# <a name="add-a-toolbar"></a>Добавление панели инструментов
В этом пошаговом слове показано, как добавить панель инструментов в Visual Studio IDE.

 Панель инструментов представляет собой горизонтальную или вертикальную полосу, содержащую кнопки, привязанные к командам. В зависимости от его реализации панель инструментов в IDE может быть перемещена, пристыкована на любой стороне основного окна IDE или сделана, чтобы остаться перед другими окнами.

 Кроме того, пользователи могут добавлять команды в панель инструментов или удалять их из нее с помощью окна **настраиваемых** диалогов. Как правило, панели инструментов в VSPackages настраиваются на пользователя. IDE обрабатывает все настройки, а VSPackage реагирует на команды. VSPackage не должен знать, где находится команда физически.

 Для получения дополнительной информации [Commands, menus, and toolbars](../extensibility/internals/commands-menus-and-toolbars.md)о меню см.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-toolbar"></a>Создание расширения с помощью панели инструментов
 Создайте проект VSIX под названием `IDEToolbar`. Добавьте шаблон элемента элемента меню под названием **ToolbarTestCommand.** Для получения информации о том, как это сделать, [см. Создать расширение с командой меню.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="create-a-toolbar-for-the-ide"></a>Создание панели инструментов для IDE

1. В *ToolbarTestCommandPackage.vsct*ищите раздел Символы. В элементе GuidSymbol под названием guidToolbarTestCommandPackageDSet добавьте декларации для панели инструментов и группы инструментов следующим образом.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. В верхней части раздела Команд создайте раздел Меню. Добавьте элемент меню в раздел Меню, чтобы определить панель инструментов.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Toolbars не могут быть вложены как submenus. Таким образом, вам не нужно назначать родительскую группу. Кроме того, вам не придется устанавливать приоритет, потому что пользователь может перемещать панели инструментов. Как правило, начальное размещение панели инструментов определяется программно, но последующие изменения пользователем сохраняются.

3. В разделе [Группы](../extensibility/groups-element.md) после вступления в группу определите элемент [группы](../extensibility/group-element.md) для содержащего команды для панели инструментов.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Сделайте кнопку отображаемым на панели инструментов. В разделе Кнопки замените родительский блок в кнопке на панель инструментов. Получившийся блок кнопки должен выглядеть следующим образом:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     По умолчанию, если панель инструментов не имеет команд, она не отображается.

5. Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен появиться.

6. Нажмите правой кнопкой визуальной студии меню бар, чтобы получить список инструментов. Выберите **панель тестов.**

7. Теперь панель инструментов должна рассматриваться как значок справа от значка «Найти в файлах». При нажатии на значок, вы должны увидеть окно сообщений, что говорит **ToolbarTestCommandPackage. Внутри IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
