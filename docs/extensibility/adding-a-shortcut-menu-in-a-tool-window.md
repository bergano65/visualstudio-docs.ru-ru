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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 661e31f32f176e48ea69ae92f23ecdde7911456b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Добавление контекстного меню в окне инструментов
В этом пошаговом руководстве помещает контекстное меню в окне инструментов. Контекстное меню — меню, которое открывается при щелчке кнопки, текстовое поле или фона окна. Команды контекстного меню работают так же, как команды на других меню или панели инструментов. Для поддержки контекстное меню, укажите его в vsct-файле и отобразить их в ответ на правой кнопки мыши.  
  
 Окно инструментов состоит из пользовательского элемента управления WPF в класс окна пользовательский инструмент, который наследует от <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.  
  
 В этом пошаговом руководстве демонстрируется создание контекстное меню в меню Visual Studio, путем объявления элементов меню в vsct-файле и затем с помощью Managed Package Framework для их реализации в классе, который определяет окно инструментов. Такой подход упрощает доступ к командам Visual Studio, элементы пользовательского интерфейса и объектная модель автоматизации.  
  
 Кроме того, если контекстное меню не будет доступа к функциям Visual Studio, можно использовать <xref:System.Windows.FrameworkElement.ContextMenu%2A> свойства элемента XAML в элементе управления. Дополнительные сведения см. в разделе [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Создание контекстного меню средства окна пакета  
  
1.  Создайте проект VSIX с именем `TWShortcutMenu` и добавьте шаблон окно инструментов с именем **контекстномменю** к нему. Дополнительные сведения о создании окно инструментов см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Указание в контекстном меню  
 Контекстное меню, таких как показано в этом пошаговом руководстве дает пользователю возможность выбрать из списка цветов, которые используются для заполнения фона окна инструментов.  
  
1.  В ShortcutMenuPackage.vsct найдите в элементе GuidSymbol с именем guidShortcutMenuPackageCmdSet и объявления контекстное меню, контекстное меню группы и параметры меню. Элемент GuidSymbol теперь должна выглядеть следующим образом:  
  
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
  
2.  Непосредственно перед элементом кнопки создайте элемент меню, а затем определите контекстное меню в нем.  
  
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
  
     Контекстное меню не имеет родительский элемент, так как он не является частью меню или панели инструментов.  
  
3.  Создайте элемент группы с элементом группы, содержащий элементы контекстного меню и свяжите группу с помощью контекстного меню.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  В элементе кнопки определяют отдельных команд, которые будут отображаться в контекстном меню. Элемент кнопки должен выглядеть следующим образом:  
  
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
  
5.  В ShortcutMenuPackageGuids.cs добавьте набор определений для команды GUID, в контекстном меню и элементов меню.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Это же идентификаторы команд, определенных в разделе символы ShortcutMenuPackage.vsct файла. Контекст группы не включается здесь так как он необходим только в vsct-файле.  
  
## <a name="implementing-the-shortcut-menu"></a>Реализация в контекстном меню  
 В этом разделе реализует контекстное меню и команд.  
  
1.  В ShortcutMenu.cs окна инструментов можно получить службу команд меню, но элемент управления, содержащихся в нем нельзя. Ниже показано, как сделать службу команд меню, доступными в пользовательский элемент управления.  
  
2.  В ShortcutMenu.cs, добавьте следующие операторы using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Переопределите метод Initialize() окна инструментов, чтобы получить службу команд меню и добавить элемент управления, передача службу команд меню в конструктор:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  В конструкторе окно инструмента контекстномменю удалите строку, который добавляет элемент управления. Конструктор должен выглядеть следующим образом:  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  В ShortcutMenuControl.xaml.cs добавьте закрытое поле для службы команды меню и измените конструктор элемента управления для использования службу команд меню. Затем можно используйте службу команд меню для добавления команд контекстного меню. Конструктор ShortcutMenuControl должен выглядеть как следующий код. Обработчик команд будут определены позже.  
  
    ```csharp  
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
  
6.  Добавьте в ShortcutMenuControl.xaml, <xref:System.Windows.UIElement.MouseRightButtonDown> событий на верхний уровень <xref:System.Windows.Controls.UserControl> элемента. Файл XAML должен выглядеть следующим образом:  
  
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
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Добавьте следующие инструкции using и тот же файл:  
  
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
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     При этом создается <xref:System.ComponentModel.Design.CommandID> объекта для контекстного меню, определяет положение щелчка мыши и открывается контекстное меню в этом расположении с помощью <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> метод.  
  
10. Реализуйте обработчик команд.  
  
    ```csharp  
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
  
     В этом случае только один метод обработки событий для всех элементов меню путем выявления <xref:System.ComponentModel.Design.CommandID> и соответствующим образом задание цвета фона. Если элементы меню содержит несвязанных команд, будет создан отдельный обработчик для каждой команды.  
  
## <a name="testing-the-tool-window-features"></a>Тестирование функций окна инструментов  
  
1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
2.  В экспериментальном экземпляре выберите **представления и другие окна**, а затем нажмите кнопку **контекстномменю**. Таким образом отображать окна инструментов.  
  
3.  Щелкните правой кнопкой мыши тело окна инструментов. Появится контекстное меню, которое содержит список цветов.  
  
4.  Выберите цвет из контекстного меню. Цвет фона окна инструментов должны изменяться для выбранного цвета.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)
