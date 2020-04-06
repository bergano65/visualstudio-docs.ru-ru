---
title: Добавление меню ярлыка в окне инструмента (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740280"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Добавить меню ярлыка в окне инструмента
Это пошаговое походе помещает меню ярлыка в окно инструмента. Меню ярлыка — это меню, которое появляется, когда пользователь справа нажимает кнопку, текстовый ящик или фон окна. Команды в меню ярлыков ведут себя так же, как команды в других меню или панели инструментов. Чтобы поддержать меню быстрого обеспечения, укажите его в файле *.vsct* и отобразите его в ответ на правый щелчок мыши.

Окно инструмента состоит из управления пользователем WPF в специальном <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>классе окна инструмента, который наследует от .

В этом пошаговом показании, как создать меню ярлыка в виде меню Visual Studio, объявив элементы меню в *файле .vsct,* а затем используя рамку управляемого пакета для их реализации в классе, определяющем окно инструментов. Этот подход облегчает доступ к командам Visual Studio, элементам uI и модели объектов автоматизации.

Кроме того, если меню shortcut не будет доступно для <xref:System.Windows.FrameworkElement.ContextMenu%2A> функций Visual Studio, в управлении пользователем можно использовать свойство элемента XAML. Для получения дополнительной информации [см.](/dotnet/framework/wpf/controls/contextmenu)

## <a name="prerequisites"></a>Предварительные требования
Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, см [Установка Визуальной студии SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Создание пакета меню ярлыка окна окна инструмента

1. Создайте проект VSIX под названием `TWShortcutMenu` и добавьте в него шаблон окна инструмента под названием **ShortcutMenu.** Для получения дополнительной информации о создании окна инструмента [см.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="specifying-the-shortcut-menu"></a>Определение меню ярлыка
Меню ярлыка, такое как меню, указанное в этом пошаговом промеделе, позволяет пользователю выбрать из списка цветов, которые используются для заполнения фона окна инструмента.

1. В *shortcutMenuPackage.vsct*, найти в элементе GuidSymbol под названием guidShortcutMenuPackageCmdSet, и объявить меню ярлыка, ярлык меню группы, и параметры меню. Элемент GuidSymbol теперь должен выглядеть следующим образом:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Непосредственно перед элементом кнопки создайте элемент Меню, а затем определите меню ярлыка в нем.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Меню ярлыка не имеет родителей, потому что оно не является частью меню или панели инструментов.

3. Создайте элемент группы с элементом группы, который содержит элементы меню ярлыка, и свяжете группу с меню ярлыка.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. В элементе кнопки определите отдельные команды, которые будут отображаться в меню ярлыка. Элемент кнопки должен выглядеть следующим образом:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. В *ShortcutMenuCommand.cs*добавьте определения для набора команд GUID, меню ярлыков и элементов меню.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Это те же иные иди команд, которые определены в разделе Символы *файла ShortcutMenuPackage.vsct.* Контекстная группа не включена здесь, поскольку она требуется только в *файле .vsct.*

## <a name="implementing-the-shortcut-menu"></a>Реализация меню ярлыка
 В этом разделе реализуется меню ярлыка и его команды.

1. В *ShortcutMenu.cs*окно инструмента может получить службу командменю меню, но элемент управления, который он содержит, не может. Следующие шаги показывают, как сделать службу команд меню доступной для управления пользователем.

2. В *ShortcutMenu.cs*добавьте следующие директивы:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Переопределить метод инициализации окна инструмента () для получения службы командного управления меню и добавьте элемент управления, передав командную службу меню конструктору:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. В конструкторе окна окна инструмента ShortcutMenu удалите строку, которая добавляет элемент управления. Конструктор должен теперь выглядеть следующим образом:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. В *ShortcutMenuControl.xaml.cs*добавьте частное поле для службы команд меню и измените конструктор управления, чтобы взять службу команд меню. Затем используйте службу команд меню для добавления команд контекстного меню. Теперь конструктор ShortcutMenuControl должен выглядеть следующим кодом. Обработчик команды будет определен позже.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. В *shortcutMenuControl.xaml*добавьте <xref:System.Windows.UIElement.MouseRightButtonDown> событие в <xref:System.Windows.Controls.UserControl> элемент верхнего уровня. Файл XAML теперь должен выглядеть следующим образом:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. В *ShortcutMenuControl.xaml.cs*добавьте заглушку для обработчика событий.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Добавьте следующие директивы с помощью в тот же файл:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Реализовать `MyToolWindowMouseRightButtonDown` событие следующим образом.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    Это создает <xref:System.ComponentModel.Design.CommandID> объект для меню ярлыка, определяет местоположение щелчка мыши и открывает меню ярлыка <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> в этом месте с помощью метода.

10. Реализация обработчика команд.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    В этом случае только один метод обрабатывает события для всех <xref:System.ComponentModel.Design.CommandID> элементов меню, определяя и устанавливая цвет фона соответственно. Если бы элементы меню содержали несвязанные команды, для каждой команды был бы создан отдельный обработчик событий.

## <a name="test-the-tool-window-features"></a>Проверьте функции окна инструмента

1. Выполните сборку решения и запустите отладку. Появляется экспериментальный экземпляр.

2. В экспериментальном экземпляре нажмите **View / Другие Windows,** а затем нажмите **ShortcutMenu**. При этом следует отобразить окно инструмента.

3. Нажмите правой кнопкой мыши в корпусе окна инструмента. Должно отображаться меню ярлыка, в которое есть список цветов.

4. Нажмите на цвет в меню ярлыка. Цвет фона окна инструмента должен быть изменен на выбранный цвет.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
- [Использование и предоставление услуг](../extensibility/using-and-providing-services.md)
