---
title: Добавление панели инструментов в окно инструментов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740245"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Добавление панели инструментов в окно инструмента
В этом пошаговом показании, как добавить панель инструментов в окно инструмента.

 Панель инструментов представляет собой горизонтальную или вертикальную полосу, содержащую кнопки, привязанные к командам. Длина панели инструментов в окне инструмента всегда такая же, как ширина или высота окна инструмента, в зависимости от того, где панель инструментов пристыкована.

 В отличие от панели инструментов в IDE, панель инструментов в окне инструмента должна быть пристыкована и не может быть перемещена или настроена. Если VSPackage записан в коде umanaged, панель инструментов может быть пристыкована на любом краю.

 Для получения дополнительной информации о том, как добавить панель инструментов, [см.](../extensibility/adding-a-toolbar.md)

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, см [Установка Визуальной студии SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Создание панели инструментов для окна инструмента

1. Создайте проект VSIX под названием, `TWToolbar` который имеет как команду меню под названием **TWTestCommand,** так и окно инструментов под названием **TestToolWindow.** Для получения дополнительной информации [см. Создать расширение с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md) и создать расширение с [окном инструмента.](../extensibility/creating-an-extension-with-a-tool-window.md) Перед добавлением шаблона окна инструмента необходимо добавить шаблон элемента команды.

2. В *TWTestCommandPackage.vsct*ищите раздел Символы. В узло GuidSymbol под названием guidTWTestCommandPackageDSet объявляете панель инструментов и группу инструментов следующим образом.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. В верхней `Commands` части раздела `Menus` создайте раздел. Добавьте `Menu` элемент для определения панели инструментов.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Инструменты не могут быть вложены, как подменю. Таким образом, вам не нужно назначать родителей. Кроме того, вам не нужно устанавливать приоритет, потому что пользователь может перемещать панели инструментов. Как правило, начальное размещение панели инструментов определяется программно, но последующие изменения пользователем сохраняются.

4. В разделе Группы определите группу, содержащую команды для панели инструментов.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. В разделе Кнопки измените родительский элемент существующей кнопки в группу панели инструментов, чтобы панель инструментов была отображана.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     По умолчанию, если панель инструментов не имеет команд, она не отображается.

     Поскольку новая панель инструментов не добавляется автоматически в окно инструмента, панель инструментов должна быть добавлена явно. Этот метод будет рассмотрен в следующем разделе.

## <a name="add-the-toolbar-to-the-tool-window"></a>Добавьте панель инструментов в окно инструмента

1. В *TWTestCommandPackageGuids.cs* добавить следующие строки.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. В *TestToolWindow.cs* добавить следующее заявление с использованием.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. В конструктор TestToolWindow добавьте следующую строку.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Проверьте панель инструментов в окне инструмента

1. Выполните сборку решения и запустите отладку. Экспериментальная инстанция Visual Studio должна появиться.

2. В **представлении / Другие** меню Windows нажмите **Test ToolWindow,** чтобы отобразить окно инструмента.

     Панель инструментов (похоже на значок по умолчанию) находится в левом верхнем верхнем отоке инструмента, чуть ниже заголовка.

3. На панели инструментов нажмите значок, чтобы отобразить сообщение **TWTestCommandPackage внутри TWToolbar.TWTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>См. также
- [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)
