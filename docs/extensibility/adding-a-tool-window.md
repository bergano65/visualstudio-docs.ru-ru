---
title: Добавление окна инструментов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5ffcc334a69a38da4869532d633960cfac7260d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317137"
---
# <a name="add-a-tool-window"></a>Добавление окна инструментов
В этом пошаговом руководстве вы узнаете, как создать окно инструментов и интегрировать его в Visual Studio одним из следующих способов:

- Добавьте элемент управления для окна инструментов.

- Добавление панели инструментов окна инструментов.

- Добавление команды на панели инструментов.

- Реализации этих команд.

- Задание положения по умолчанию для окна инструментов.

## <a name="prerequisites"></a>Предварительные требования
Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Создать окно инструментов

1. Создайте проект с именем **FirstToolWin** с помощью шаблона VSIX и добавление шаблона элемента окна пользовательского инструмента с именем **FirstToolWindow**.

    > [!NOTE]
    > Дополнительные сведения о создании расширения с окном инструментов, см. в разделе [создание расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Добавление элемента управления окна инструментов

1. Удаление элемента управления по умолчанию. Откройте *FirstToolWindowControl.xaml* и удалить **Click Me!** .

2. В **элементов**, разверните **все элементы управления WPF** раздела и перетащите **элемент мультимедиа** управления **FirstToolWindowControl** формы. Выберите элемент управления, а затем в **свойства** окна, назовите этот элемент **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Добавление панели инструментов окна инструментов
Добавление панели инструментов следующим образом, вы гарантировать его градиенты и цвета согласования с остальной частью интегрированной среды разработки.

1. В **обозревателе решений**откройте *FirstToolWindowPackage.vsct*. *.Vsct* файл определяет элементы графического пользовательского интерфейса (GUI) в окно инструментов с помощью XML.

2. В `<Symbols>` найдите `<GuidSymbol>` узел которого `name` атрибут `guidFirstToolWindowPackageCmdSet`. Добавьте следующие два `<IDSymbol>` элементы в список `<IDSymbol>` элементы на этом узле для определения панель инструментов и панель инструментов группы.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Непосредственно над `<Buttons>` разделе, создайте `<Menus>` раздел, который выглядит следующим образом:

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

    Существует несколько разных меню. Это меню — это панель инструментов в окне инструментов, определяется его `type` атрибута. `guid` И `id` параметры составляют полный идентификатор панели инструментов. Как правило `<Parent>` меню является объемлющей группы. Тем не менее панель инструментов определяется как его родительский элемент. Таким образом, используется тот же идентификатор для `<Menu>` и `<Parent>` элементы. `priority` Составляет лишь "0".

4. Меню во многом похожи на панели инструментов. Например так же, как меню могут иметь группы команд, панелей инструментов также использовать группы. (В меню, группы команд разделяются горизонтальных линий. На панели инструментов, группы, не разделенных visual разделителей.)

    Добавить `<Groups>` раздел, содержащий `<Group>` элемент. Определяет группы, идентификатор которого объявлен в `<Symbols>` разделе. Добавить `<Groups>` разделе сразу после `<Menus>` раздел.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Задать родительский GUID и идентификатор GUID и идентификатор панели инструментов, добавьте группу на панель инструментов.

## <a name="add-a-command-to-the-toolbar"></a>Добавление команды на панели инструментов
 Добавление команды на панели инструментов, которая отображается в виде кнопки.

1. В `<Symbols>` разделе, можно объявить следующие элементы IDSymbol сразу после инструментов и панель инструментов группы объявления.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Добавьте элемент кнопки внутри `<Buttons>` раздел. Этот элемент будет отображаться на панели инструментов в окне инструментов с **поиска** значок (с увеличительным стеклом).

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

    Это делает доступными в коде вашей команды.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Добавить свойство MediaPlayer FirstToolWindowControl
Из обработчиков событий для элементов управления панели инструментов ваш код должен быть способен для доступа к управления проигрыватель мультимедиа, который является потомком класса FirstToolWindowControl.

В **обозревателе решений**, щелкните правой кнопкой мыши *FirstToolWindowControl.xaml*, нажмите кнопку **просмотреть код**и добавьте следующий код к классу FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Создать окно инструментов и панели инструментов
Добавить панель инструментов и команды меню, который вызывает **открыть файл** диалоговое окно и воспроизводит файл мультимедиа.

1. Откройте *FirstToolWindow.cs* и добавьте следующие `using` инструкций.

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Внутри класса FirstToolWindow Добавьте открытый ссылку на элемент управления FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. В конце конструктора задайте эту переменную элемента управления в только что созданный элемент управления.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Создать экземпляр панели инструментов в конструктор.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. На этом этапе конструктор FirstToolWindow должен выглядеть следующим образом:

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

6. Добавьте команду меню в панели инструментов. В классе FirstToolWindowCommand.cs, добавьте следующий оператор using

    ```csharp
    using System.Windows.Forms;
    ```

7. В классе FirstToolWindowCommand добавьте следующий код в конце метода ShowToolWindow(). Команда ButtonHandler будет реализована в следующем разделе.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Реализация команды меню в окне инструментов

1. Добавьте в класс FirstToolWindowCommand ButtonHandler методу, вызывающему **открыть файл** диалоговое окно. При выборе файла его воспроизведение файла мультимедиа.

2. В классе FirstToolWindowCommand добавьте закрытый ссылку на окно FirstToolWindow, который создается в методе FindToolWindow().

    ```csharp
    private FirstToolWindow window;
    ```

3. Измените метод ShowToolWindow(), чтобы задать период, определенный выше (таким образом, обработчик команд ButtonHandler можно получить доступ к окна элемента управления. Ниже приведен полный метод ShowToolWindow().

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

4. Добавьте метод ButtonHandler. Он создает OpenFileDialog для пользователя указать файл мультимедиа для воспроизведения, а затем воспроизводит выбранного файла.

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

## <a name="set-the-default-position-for-the-tool-window"></a>Задание положения по умолчанию для окна инструментов
 Затем укажите расположение по умолчанию в интегрированной среде разработки для окна инструментов. Сведения о конфигурации для окна инструментов находится в *FirstToolWindowPackage.cs* файла.

1. В *FirstToolWindowPackage.cs*, найти <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> атрибут `FirstToolWindowPackage` класс, который передает тип FirstToolWindow конструктору. Чтобы указать положение по умолчанию, необходимо добавить дополнительные параметры в конструктор, в следующем примере.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Первый именованный параметр — `Style` и его значение равно `Tabbed`, который означает, что окно вкладки в существующее окно. Положение закрепления задается `Window` параметра, n данном случае GUID **обозревателе решений**.

    > [!NOTE]
    > Дополнительные сведения о типах окон в интегрированной среде разработки см. в разделе <xref:EnvDTE.vsWindowType>.

## <a name="test-the-tool-window"></a>Тестирование окна инструментов

1. Нажмите клавишу **F5** открыть новый экземпляр Visual Studio экспериментальном построении.

2. На **представление** последовательно выберите пункты **Other Windows** и нажмите кнопку **первое окно инструментов**.

    Окна инструментов проигрывателя мультимедиа следует открывать в той же позиции, что **обозревателе решений**. Если он по-прежнему отображается в той же позиции, что и раньше, сбросить макет окна (**окно / Сброс макета окон**).

3. Нажмите кнопку (он имеет **поиска** значок) в окне инструментов. Выберите поддерживаемые звукового или видеофайла, например *C:\windows\media\chimes.wav*, затем нажмите клавишу **откройте**.

    Вы должны услышать звук колокольчика.

## <a name="see-also"></a>См. также
[Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
