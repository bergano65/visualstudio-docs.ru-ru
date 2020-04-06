---
title: Добавление окна инструмента Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740264"
---
# <a name="add-a-tool-window"></a>Добавление окна инструмента

В этом пошаговом шаге вы узнаете, как создать окно инструментов и интегрировать его в Visual Studio следующим образом:

- Добавьте элемент управления в окно инструмента.

- Добавьте панель инструментов в окно инструмента.

- Добавьте команду в панель инструментов.

- Реализация команд.

- Установите положение по умолчанию для окна инструмента.

## <a name="prerequisites"></a>Предварительные требования

Визуальная студия SDK включена в качестве дополнительной функции в установке Visual Studio. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tool-window"></a>Создание окна инструмента

1. Создайте проект под названием **FirstToolWin** с помощью шаблона VSIX и добавьте пользовательский шаблон элемента окна инструмента под названием **FirstToolWindow.**

    > [!NOTE]
    > Для получения дополнительной информации о создании расширения с окном инструмента [см. Создать расширение с окном инструмента.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="add-a-control-to-the-tool-window"></a>Добавление элемента управления в окно инструмента

1. Удалите элемент управления по умолчанию. Откройте *FirstToolWindowControl.xaml* и удалите **Click Me!** .

2. В **наборе инструментов**расширьте раздел **All WPF Controls** и перетащите элемент **мультимедиа** в форму **FirstToolWindowControl.** Выберите элемент управления, и в окне **свойств** назовите этот элемент **mediaElement1.**

## <a name="add-a-toolbar-to-the-tool-window"></a>Добавление панели инструментов в окно инструмента
Добавляя панель инструментов следующим образом, вы гарантируете, что ее градиенты и цвета соответствуют остальной части IDE.

1. В **Solution Explorer**, открыть *FirstToolWindowPackage.vsct*. Файл *.vsct* определяет графический пользовательский интерфейс (GUI) элементов в окне инструмента с помощью XML.

2. В `<Symbols>` разделе найдите `<GuidSymbol>` узла, атрибутом которого `name` является `guidFirstToolWindowPackageCmdSet`. Добавьте следующие два `<IDSymbol>` элемента в список элементов `<IDSymbol>` в этом узлах, чтобы определить панель инструментов и группу панели инструментов.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Чуть выше `<Buttons>` раздела, `<Menus>` создать раздел, который напоминает это:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Есть несколько различных видов меню. Это меню представляет собой панель инструментов в `type` окне инструмента, определяемую его атрибутом. `guid` Настройки `id` и настройки составляют полностью квалифицированный идентификатор панели инструментов. Как правило, `<Parent>` меню является содержащей группой. Тем не менее, панель инструментов определяется как его собственный родитель. Таким образом, один и тот `<Menu>` `<Parent>` же идентификатор используется для элементов и элементов. Атрибут `priority` просто '0'.

4. Панели инструментов во многом напоминают меню. Например, так же, как в меню могут быть группы команд, панели инструментов могут также иметь группы. (В меню командные группы разделены горизонтальными линиями. На панели инструментов группы не разделены визуальными разделителями.)

    Добавьте `<Groups>` раздел, `<Group>` содержащий элемент. Это определяет группу, идентификатор которой вы объявили `<Symbols>` в разделе. Добавьте `<Groups>` раздел сразу `<Menus>` после раздела.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Установив родительский GUID и идентификатор на GUID и идентификатор панели инструментов, вы добавляете группу в панель инструментов.

## <a name="add-a-command-to-the-toolbar"></a>Добавление команды в панель инструментов

Добавьте команду в панель инструментов, которая отображается в виде кнопки.

1. В `<Symbols>` разделе объявите следующие элементы IDSymbol сразу после деклараций группы инструментов и панели инструментов.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Добавьте элемент кнопки в секцию. `<Buttons>` Этот элемент появится на панели инструментов в окне инструмента с значком **Поиска** (увеличительное стекло).

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. Откройте *FirstToolWindowCommand.cs* и добавьте следующие строки в классе сразу после существующих полей.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Это делает ваши команды доступными в коде.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Добавление свойства MediaPlayer в FirstToolWindowControl
Из обработчиков событий для управления панелью инструментов ваш код должен иметь доступ к управлению Media Player, который является ребенком класса FirstToolWindowControl.

В **Solution Explorer**, правой кнопкой *кнопкой FirstToolWindowControl.xaml*, нажмите Просмотр **кода**, и добавить следующий код в классе FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Мгновенное окно инструмента и панель инструментов
Добавьте панель инструментов и команду меню, которая вызывает диалог **Open File** и воспроизводит выбранный файл мультимедиа.

1. Откройте *FirstToolWindow.cs* и `using` добавьте следующие директивы:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. В классе FirstToolWindow добавьте общедоступную ссылку на элемент управления FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. В конце конструктора установите эту переменную элемента управления на вновь созданный элемент управления.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Мгновенное воспроизведение панели инструментов внутри конструктора.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. На данный момент конструктор FirstToolWindow должен выглядеть следующим образом:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Добавьте команду меню в панель инструментов. В FirstToolWindowCommand.cs классе добавьте следующую директиву с использованием:

    ```csharp
    using System.Windows.Forms;
    ```

7. В классе FirstToolWindowCommand добавьте следующий код в конце метода ShowToolWindow() Команда ButtonHandler будет реализована в следующем разделе.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Реализация команды меню в окне инструмента

1. В классе FirstToolWindowCommand добавьте метод ButtonHandler, который вызывает диалог **Open File.** Когда файл выбран, он воспроизводит файл мультимедиа.

2. В классе FirstToolWindowCommand добавьте приватную ссылку на окно FirstToolWindow, созданное в методе FindToolWindow()

    ```csharp
    private FirstToolWindow window;
    ```

3. Измените метод ShowToolWindow() для установки окна, которое вы определили выше (чтобы обработчик команды ButtonHandler мог получить доступ к управлению окном. Вот полный метод ShowToolWindow() .

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. Добавьте метод ButtonHandler. Он создает OpenFileDialog для пользователя, чтобы указать файл мультимедиа для воспроизведения, а затем воспроизводит выбранный файл.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Установите положение по умолчанию для окна инструмента

Затем укажите местоположение по умолчанию в IDE для окна инструмента. Информация о конфигурации для окна инструмента находится в *файле FirstToolWindowPackage.cs.*

1. В *FirstToolWindowPackage.cs,* <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> найти атрибут `FirstToolWindowPackage` на класс, который передает тип FirstToolWindow к конструктору. Чтобы указать положение по умолчанию, необходимо добавить дополнительные параметры к следующему примеру конструктора.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Первый названный `Style` параметр `Tabbed`и его значение, что означает, что окно будет вкладка в существующем окне. Положение стыковки `Window` определяется параметром, n этот случай, GUID **из solution Explorer**.

    > [!NOTE]
    > Для получения дополнительной информации о типах <xref:EnvDTE.vsWindowType>окон в IDE см.

## <a name="test-the-tool-window"></a>Протестировать окно инструмента

1. Нажмите **F5,** чтобы открыть новый экземпляр экспериментальной сборки Visual Studio.

2. В меню **View** укажите на **другие окна,** а затем нажмите **«Первое окно инструмента».**

    Окно инструмента медиаплеера должно открываться в том же положении, что и **Solution Explorer.** Если он по-прежнему отображается в том же положении, что и раньше, сбросить макет окна (**Окно / Сбросить окно Layout**).

3. Нажмите кнопку (она имеет значок **поиска)** в окне инструмента. Выберите поддерживаемый звуковой или видеофайл, например, *C: «окна»media-chimes.wav*, затем нажмите **Открыть**.

    Вы должны услышать звук перезвона.

## <a name="see-also"></a>См. также
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
