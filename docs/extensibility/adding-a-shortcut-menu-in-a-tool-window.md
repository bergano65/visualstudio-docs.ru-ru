---
title: "Добавление контекстного меню в окне инструментов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ab921bec73528be7207baebdf9cb31885e2253fd
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Добавление контекстного меню в окне инструментов
В этом пошаговом руководстве помещает контекстное меню в окне инструментов. Контекстное меню является меню, которое открывается при щелчке кнопки, текстового поля или фона окна. Команды контекстного меню так же, как команды на другие меню или панели инструментов. Для поддержки контекстное меню, укажите его в файл .vsct и отображения его в ответ на правой кнопки мыши.  
  
 Окно инструментов состоит из пользовательского элемента управления WPF в классе окна пользовательский инструмент, который наследует <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
 В этом пошаговом руководстве демонстрируется создание контекстного меню в меню Visual Studio, объявление элементов меню в файле .vsct, а затем с помощью платформа управляемых пакетов для их реализации в классе, который определяет окно инструментов. Этот подход облегчает доступ к командам Visual Studio, элементы пользовательского интерфейса и объектной модели автоматизации.  
  
 Кроме того, если контекстное меню не будет доступа к функциям Visual Studio, можно использовать <xref:System.Windows.FrameworkElement.ContextMenu%2A>Свойства элемента XAML в пользовательском элементе управления.</xref:System.Windows.FrameworkElement.ContextMenu%2A> Дополнительные сведения см. в разделе [ContextMenu](http://msdn.microsoft.com/Library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Создание контекстного меню средства окно пакета  
  
1.  Создайте проект VSIX с именем `TWShortcutMenu` и добавьте шаблон окно инструментов с именем **контекстномменю** к нему. Дополнительные сведения о создании окна средства просмотра [создания расширения с окном инструмента](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Указание в контекстном меню  
 Контекстное меню, таких как показано в этом пошаговом руководстве позволяет пользователю выбрать из списка цветов, которые используются для заполнения фона окна инструментов.  
  
1.  Найдите в элементе GuidSymbol с именем guidShortcutMenuPackageCmdSet в ShortcutMenuPackage.vsct и объявите контекстное меню, контекстное меню группы и пункты меню. Элемент GuidSymbol теперь должен выглядеть следующим образом:  
  
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
  
2.  Непосредственно перед элементом кнопки Создать элемент меню, а затем определить контекстное меню в ней.  
  
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
  
3.  Создать элемент группы с элементом группы, содержащий элементы контекстного меню, группу и свяжите ее с помощью контекстного меню.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  В элементе кнопки Определите отдельные команды, которые будут отображаться в контекстном меню. Элемент кнопки должны выглядеть следующим образом:  
  
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
  
5.  В ShortcutMenuPackageGuids.cs добавьте набор определений для команды GUID, в контекстном меню и пунктов меню.  
  
    ```c#  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Это же идентификаторы команд, определенных в разделе "символы" файла ShortcutMenuPackage.vsct. Контекст группы не включается здесь так, как это требуется только в файл .vsct.  
  
## <a name="implementing-the-shortcut-menu"></a>Реализация в контекстном меню  
 В этом разделе реализует контекстное меню и команд.  
  
1.  В ShortcutMenu.cs окно инструментов можно получить службы команды меню, но в элементах управления, содержащихся в нем. Ниже показано, как сделать службы команды меню в пользовательский элемент управления.  
  
2.  В ShortcutMenu.cs, добавьте следующие операторы using:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Переопределите метод Initialize() окно инструмента для получения служба команд меню и добавлять элементы управления, передав службы команды меню в конструктор:  
  
    ```c#  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  В конструкторе окно инструмента контекстномменю удалите строку, которая добавляет элемент управления. Конструктор теперь должен выглядеть следующим образом:  
  
    ```c#  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  В ShortcutMenuControl.xaml.cs добавьте закрытое поле для службы команды меню и измените конструктор элемента управления для использования службы команды меню. Затем можно используйте службы команды меню для добавления команд контекстного меню. Конструктор ShortcutMenuControl должен выглядеть следующим образом. Обработчик команды будут определены в дальнейшем.  
  
    ```c#  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  Добавьте в ShortcutMenuControl.xaml, <xref:System.Windows.UIElement.MouseRightButtonDown>событий на верхний уровень <xref:System.Windows.Controls.UserControl>элемент.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.UIElement.MouseRightButtonDown> Теперь файл XAML должен выглядеть следующим образом:  
  
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
  
7.  В ShortcutMenuControl.xaml.cs добавьте заглушку для обработчика событий.  
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Добавьте следующие операторы using в тот же файл:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Реализуйте `MyToolWindowMouseRightButtonDown` события, как показано ниже.  
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     При этом создается <xref:System.ComponentModel.Design.CommandID>объекта для контекстного меню, определяет положение щелчка мыши и открытие контекстного меню в этом расположении с помощью <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>метод.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> </xref:System.ComponentModel.Design.CommandID>  
  
10. Реализуйте обработчик команды.  
  
    ```c#  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     В этом случае только один метод обработки событий для всех элементов меню, определив <xref:System.ComponentModel.Design.CommandID>и соответствующим образом задавая цвет фона.</xref:System.ComponentModel.Design.CommandID> Если элементы меню содержит несвязанных команд, должны быть созданы в отдельных обработчиках событий для каждой команды.  
  
## <a name="testing-the-tool-window-features"></a>Функции окна средства тестирования  
  
1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
2.  В экспериментальном экземпляре выберите **представления и другие окна**, а затем нажмите кнопку **контекстномменю**. Таким образом, вы увидите окно средства.  
  
3.  Щелкните правой кнопкой мыши внутри окна инструмента. Появится контекстное меню, который имеет список цветов.  
  
4.  Выберите цвет из контекстного меню. Цвет фона окна инструментов должны изменяться для выбранного цвета.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)
