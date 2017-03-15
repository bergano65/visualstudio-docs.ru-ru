---
title: "Добавление окна инструментов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "учебники"
  - "окна инструментов"
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: 52
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 52
---
# Добавление окна инструментов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом пошаговом руководстве вы узнаете, как создать окно инструментов и интегрировать его в Visual Studio одним из следующих способов:  
  
-   Добавьте элемент управления в окно средства.  
  
-   Добавление панели инструментов окна инструментов.  
  
-   Добавление команды на панели инструментов.  
  
-   Реализации этих команд.  
  
-   Задайте положение по умолчанию для окна средства.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание окна инструментов  
  
1.  Создайте проект с именем **FirstToolWin** с помощью шаблона VSIX и добавление шаблона элемента окна пользовательского инструмента с именем **FirstToolWindow**.  
  
    > [!NOTE]
    >  Дополнительные сведения о создании модуля с окном инструмента см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Добавление элемента управления в окно средства  
  
1.  Удалите элемент управления по умолчанию. Откройте FirstToolWindowControl.xaml и удалите **Click Me\!** кнопки.  
  
2.  В **элементов**, разверните **все элементы управления WPF** статьи и перетащите **элемент мультимедиа** управления **FirstToolWindowControl** формы. Выберите элемент управления и в **Свойства** окна, имя этого элемента **mediaElement1**.  
  
## Добавление панели инструментов окна инструментов  
 Добавив на панель инструментов следующим образом, гарантирует его градиенты и цвета, согласованное с оставшейся частью интегрированной среды разработки.  
  
1.  В **обозревателе решений**, откройте FirstToolWindowPackage.vsct. Файл .vsct определяет элементы графического пользовательского интерфейса \(GUI\) в окно средства с помощью XML.  
  
2.  В `<Symbols>` найдите `<GuidSymbol>` узел которого `name` атрибут `guidFirstToolWindowPackageCmdSet`. Добавьте следующие две `<IDSymbol>` элементы в список `<IDSymbol>` элементы на этом узле для определения панели инструментов и группа панели инструментов.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Непосредственно над `<Buttons>` Создайте `<Menus>` раздел, который имеет следующий вид:  
  
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
  
     Существует несколько различных видов меню. Это меню — это панель инструментов в окне инструментов, определяется его `type` атрибута.`guid` И  `id` Параметры составляют полный идентификатор панели инструментов. Как правило `<Parent>` меню является объемлющей группы. Тем не менее панель инструментов определяется как его родительский элемент. Таким образом, используется тот же идентификатор для `<Menu>` и `<Parent>` элементы.`priority` Атрибут является только "0".  
  
4.  Панели инструментов напоминают меню различными способами. Например как возможно группы команд, меню, панелей инструментов может имеется групп. \(Меню группы команд разделяются линиями. На панели инструментов группы не разделены visual разделителей.\)  
  
     Добавить `<Groups>` раздел, содержащий `<Group>` элемента. Определяет группы, идентификатор которого объявлен в `<Symbols>` разделе. Добавить `<Groups>` раздел сразу после `<Menus>` раздел.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     Установив родительского GUID и идентификатор GUID и идентификатор панели инструментов, добавьте группу на панель инструментов.  
  
## Добавление команды на панели инструментов  
 Добавление команды на панели инструментов, которая отображается в виде кнопки.  
  
1.  В `<Symbols>` статьи, объявите следующие элементы IDSymbol объявления группы сразу после панели инструментов и панели инструментов.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Добавьте элемент Button внутри `<Buttons>` раздел. Этот элемент будет отображаться на панели инструментов в окне инструментов со значком поиска \(с увеличительным стеклом\).  
  
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
  
3.  Откройте FirstToolWindowCommand.cs и добавьте следующие строки в классе сразу после существующих полей.  
  
    ```c#  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     В результате команды доступны в коде.  
  
## Добавьте свойство MediaPlayer FirstToolWindowControl  
 От обработчиков событий для элементов управления панели инструментов код должен иметь доступ к элемента управления Media Player, который является дочерним классом FirstToolWindowControl.  
  
 В **обозревателе решений**, щелкните правой кнопкой мыши FirstToolWindowControl.xaml, нажмите кнопку **Просмотр кода**, и добавьте следующий код в класс FirstToolWindowControl.  
  
```c#  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## Создать окно инструментов и панели инструментов  
 Добавление панели инструментов и команды меню, который вызывает **Открыть файл** диалоговое окно и воспроизведение файла мультимедиа.  
  
1.  Откройте FirstToolWindow.cs и добавьте следующие `using` инструкции.  
  
    ```c#  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  В классе FirstToolWindow Добавьте открытый ссылку на элемент управления FirstToolWindowControl.  
  
    ```c#  
    public FirstToolWindowControl control;  
    ```  
  
3.  В конце конструктора значение этой переменной управления только что созданный элемент управления.  
  
    ```c#  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Создать экземпляр панели инструментов в конструктор.  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  На этом этапе конструктор FirstToolWindow должен выглядеть следующим образом:  
  
    ```c#  
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
  
6.  Добавление команды меню на панели инструментов. В классе FirstToolWindowCommand.cs, добавьте следующий оператор using  
  
    ```c#  
    using System.Windows.Forms;  
    ```  
  
7.  В классе FirstToolWindowCommand добавьте следующий код в конце метода ShowToolWindow\(\). Команда ButtonHandler будет реализована в следующем разделе.  
  
    ```c#  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### Реализация команды меню в окне инструментов  
  
1.  Добавьте в класс FirstToolWindowCommand ButtonHandler метода, который вызывает **Открыть файл** диалогового окна. При выборе файла его воспроизведение файла мультимедиа.  
  
2.  В классе FirstToolWindowCommand добавьте закрытый ссылку FirstToolWindow окна, которое создается в методе FindToolWindow\(\).  
  
    ```c#  
    private FirstToolWindow window;  
    ```  
  
3.  Измените метод ShowToolWindow\(\) Настройка окна, определенный выше \(что обработчик команды ButtonHandler может обращаться к элементу управления окна. Ниже приведен полный метод ShowToolWindow\(\).  
  
    ```c#  
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
  
4.  Добавьте метод ButtonHandler. Он создает OpenFileDialog, пользователь может указать файл мультимедиа, чтобы воспроизвести, и затем воспроизводит выбранного файла.  
  
    ```c#  
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
  
## Задать положение по умолчанию для окна средств  
 Затем укажите расположение по умолчанию в Интегрированной среде разработки для окна средства. Сведения о конфигурации для окна средств — в файле FirstToolWindowPackage.cs.  
  
1.  Найдите в FirstToolWindowPackage.cs, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> атрибут `FirstToolWindowPackage` класс, который передается конструктору типа FirstToolWindow. Чтобы задать положение по умолчанию, необходимо добавить дополнительные параметры в конструктор, в следующем примере.  
  
    ```c#  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     Именованные первый параметр является `Style` и имеет значение `Tabbed`, что означает, что окно вкладки в существующем окне. Позицию закрепления определяется `Window` параметр, в данном случае n идентификатор GUID **обозревателе решений**.  
  
    > [!NOTE]
    >  Дополнительные сведения о типах окон в Интегрированной среде разработки см. в разделе <xref:EnvDTE.vsWindowType>.  
  
## Окно инструментов тестирования  
  
1.  Нажмите клавишу F5, чтобы открыть новый экземпляр Visual Studio экспериментальной сборки.  
  
2.  На **представление** наведите указатель мыши на **Другие окна** и нажмите кнопку **первое окно средства**.  
  
     В той же позиции, что следует открыть окно инструментов проигрывателя мультимедиа **обозревателе решений**. Если по\-прежнему отображается в той же позиции, что и раньше, Сброс макета окон \(**окна или Сброс макета окон**\).  
  
3.  Нажмите кнопку \(он имеет значок поиска\) в окне инструментов. Выберите поддерживаемые аудио или видео файла, например, C:\\windows\\media\\chimes.wav, затем нажмите клавишу **Откройте**.  
  
     Должен быть слышен звук колокольчика.  
  
## См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)