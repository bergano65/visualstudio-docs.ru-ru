---
title: Добавление контекстного меню в окне инструментов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eede5f76a9689f79e769d23572a1d92f3ae3a867
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681482"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Добавление контекстного меню в окне инструментов
В этом пошаговом руководстве помещает контекстное меню в окне инструментов. Контекстное меню является меню, которое открывается при щелчке кнопки, текстовое поле или фона окна. Команды контекстного меню ведут себя так же, как команды на другие меню или панели инструментов. Для поддержки контекстное меню, укажите его в *.vsct* файла и отображения его в ответ на правой кнопки мыши.

Окно инструментов состоит из пользовательского элемента управления WPF в класс окна пользовательский инструмент, который наследует от <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.

В этом пошаговом руководстве показано, как создать контекстное меню, как меню Visual Studio, объявив пунктов меню в *.vsct* файл, а затем с помощью Managed Package Framework для их реализации в классе, который определяет окно инструментов. Этот подход облегчает доступ к Visual Studio команды, элементы пользовательского интерфейса и объектной модели автоматизации.

Кроме того, если контекстное меню не затронет функциональность Visual Studio, можно использовать <xref:System.Windows.FrameworkElement.ContextMenu%2A> свойства элемента XAML для пользовательского элемента управления. Дополнительные сведения см. в разделе [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Предварительные требования
Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Создание пакета меню ярлык для окна инструментов

1. Создайте проект VSIX с именем `TWShortcutMenu` и добавьте шаблон окно инструментов с именем **контекстномменю** к нему. Дополнительные сведения о создании окна инструментов, см. в разделе [создание расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Указание в контекстном меню
Контекстное меню, таких как показано в этом пошаговом руководстве позволяет пользователю выбрать из списка цветов, которые используются для заливки фона окна инструментов.

1. В *ShortcutMenuPackage.vsct*GuidSymbol элемента с именем guidShortcutMenuPackageCmdSet и в объявления контекстное меню, контекстное меню группы и параметры меню. Элемент GuidSymbol теперь должен выглядеть следующим образом:

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

2. Непосредственно перед элементом кнопок создайте элемент меню, а затем определите контекстное меню в нем.

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

    Контекстное меню не имеет родительского, так как он не является частью меню или панели инструментов.

3. Создайте элемент группы с элементом группы, содержащий пункты контекстного меню и связать группы с помощью контекстного меню.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. В элементе кнопки Определите отдельные команды, которые будут отображаться в контекстном меню. Элемент кнопки должны выглядеть следующим образом:

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

5. В *ShortcutMenuCommand.cs*, добавьте определения для набора команд GUID, в контекстном меню и пунктов меню.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Это те же идентификаторы команд, которые определены в разделе "символы" *ShortcutMenuPackage.vsct* файла. В группе контекстного здесь не так как он необходим только в *.vsct* файла.

## <a name="implementing-the-shortcut-menu"></a>Реализация в контекстном меню
 В этом разделе реализует контекстное меню и команд.

1. В *ShortcutMenu.cs*, окна инструментов можно получить службу команд меню, но не содержит элемент управления. Ниже показано, как сделать службу команд меню, доступными в пользовательский элемент управления.

2. В *ShortcutMenu.cs*, добавьте следующие операторы using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Переопределите метод Initialize() окна инструментов, чтобы получить службу команд меню и добавьте элемент управления, передав конструктору службу команд меню:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. В конструкторе окно инструмента контекстномменю удалите строку, которая добавляет элемент управления. Конструктор теперь должен выглядеть следующим образом:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. В *ShortcutMenuControl.xaml.cs*, добавьте закрытое поле для службу команд меню и измените конструктор элемента управления, чтобы воспользоваться службу команд меню. Затем можно используйте службу команд меню для добавления команды контекстного меню. Конструктор ShortcutMenuControl должен выглядеть аналогично следующему коду. Обработчик команд будут определены позже.

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

6. В *ShortcutMenuControl.xaml*, добавьте <xref:System.Windows.UIElement.MouseRightButtonDown> событий на верхний уровень <xref:System.Windows.Controls.UserControl> элемент. Файл XAML теперь должен выглядеть следующим образом:

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

7. В *ShortcutMenuControl.xaml.cs*, добавьте заглушку для обработчика событий.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Добавьте следующие операторы using в тот же файл:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Реализуйте `MyToolWindowMouseRightButtonDown` событие следующим образом.

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

    При этом создается <xref:System.ComponentModel.Design.CommandID> объекта для контекстного меню, определяет расположение щелчка мыши и откроется контекстное меню в выбранном расположении с помощью <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> метод.

10. Реализуйте обработчик команды.

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

    В этом случае только один метод обработки событий для всех элементов меню путем выявления <xref:System.ComponentModel.Design.CommandID> и соответствующим образом задания цвета фона. Если элементы меню содержит несвязанных команд, будет создан в отдельных обработчиках событий для каждой команды.

## <a name="test-the-tool-window-features"></a>Тестирование функций окна инструментов

1. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

2. В экспериментальном экземпляре выберите **представления / Other Windows**, а затем нажмите кнопку **контекстномменю**. Таким образом следует отобразить вашего окна инструментов.

3. Щелкните правой кнопкой мыши, в тексте окна инструментов. Контекстное меню, которое содержит список цветов должны отображаться.

4. Выберите в контекстном меню. Цвет фона окна инструментов должны изменяться для выбранного цвета.

## <a name="see-also"></a>См. также
- [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
- [Использование и предоставление служб](../extensibility/using-and-providing-services.md)
