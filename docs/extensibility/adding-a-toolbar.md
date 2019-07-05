---
title: Добавление панели инструментов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12fcf63c09d805f23fcbf0d041ab41ede7f85f32
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352350"
---
# <a name="add-a-toolbar"></a>Добавить панель инструментов
В этом пошаговом руководстве показано, как добавить панель инструментов в интегрированной среде разработки Visual Studio.

 Панель инструментов представляет собой горизонтальную или вертикальную полосу, содержит кнопки, которые привязаны к командам. В зависимости от его реализации панели инструментов в интегрированной среде разработки можно перемещать, закрепить с любой стороны главного окна интегрированной среды разработки или делать оставаться поверх других окон.

 Кроме того, пользователи могут добавлять команды на панель инструментов или удалить их из него с помощью **Настройка** диалоговое окно. Как правило панелей инструментов в пакеты VSPackage — настраиваемые пользователем. Среда IDE обрабатывает все настройки и VSPackage отвечает на команды. Пакет VSPackage не нужно знать, где физически находятся команды.

 Дополнительные сведения о меню, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Создание расширения с помощью панели инструментов
 Создайте проект VSIX с именем `IDEToolbar`. Добавление шаблона элемента команды меню с именем **ToolbarTestCommand**. Сведения о том, как это сделать, см. в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Создать панель инструментов для интегрированной среды разработки

1. В *ToolbarTestCommandPackage.vsct*, найдите в разделе "символы". В GuidSymbol элемент с именем guidToolbarTestCommandPackageCmdSet добавьте объявления для панели инструментов и группу инструментов, следующим образом.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. В верхней части области команд создайте раздел меню. Добавьте элемент меню в раздел меню для определения панели инструментов.

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

     Панели инструментов не могут быть вложенными как подменю. Таким образом у вас нет для назначения родительской группы. Кроме того у вас нет установить приоритет, поскольку пользователь может перемещать панели инструментов. Как правило исходное размещение панель инструментов определяется программным способом, но последующие изменения пользователем, сохраняются.

3. В [группы](../extensibility/groups-element.md) разделе после существующую запись группы, определить [группы](../extensibility/group-element.md) элемент, который будет содержать команды для панели инструментов.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Кнопка на панели инструментов. В разделе кнопки замените родительского блока кнопки панели инструментов. Полученные кнопки должны выглядеть следующим образом:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     По умолчанию если нет команд на панели инструментов он не отображается.

5. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

6. Щелкните правой кнопкой мыши в строке меню Visual Studio, чтобы получить список панелей инструментов. Выберите **тестирования инструментов**.

7. Теперь вы увидите на панели инструментов значок справа от Find в значок файлов. Если щелкнуть значок, появится окно сообщения с текстом **ToolbarTestCommandPackage. Внутри IDEToolbar.ToolbarTestCommand.MenuItemCallback()** .

## <a name="see-also"></a>См. также
- [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)