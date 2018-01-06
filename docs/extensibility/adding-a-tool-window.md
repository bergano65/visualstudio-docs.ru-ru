---
title: "Добавление окна инструментов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: "52"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 205c6928010d4cf3a35c6947e516c0bbc8674f29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-tool-window"></a>Добавление окна инструментов
В этом пошаговом руководстве вы узнаете, как создать окно инструментов и интегрировать его в Visual Studio одним из следующих способов:  
  
-   Добавление элемента управления в окне инструментов.  
  
-   Добавление панели инструментов окна инструментов.  
  
-   Добавьте команду на панель инструментов.  
  
-   Реализации этих команд.  
  
-   Задайте положение по умолчанию для окна инструментов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tool-window"></a>Создание окна инструментов  
  
1.  Создайте проект с именем **FirstToolWin** с помощью шаблона VSIX и добавить шаблон элемента окна пользовательского инструмента с именем **FirstToolWindow**.  
  
    > [!NOTE]
    >  Дополнительные сведения о создании модуля с окном инструментов см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="add-a-control-to-the-tool-window"></a>Добавление элемента управления в окне инструментов  
  
1.  Удаление элемента управления по умолчанию. Откройте FirstToolWindowControl.xaml и удалите **Click Me!** .  
  
2.  В **элементов**, разверните **всех элементов управления WPF** статьи и перетащите **элемента мультимедиа** управления **FirstToolWindowControl** формы. Выберите элемент управления и в **свойства** окна, имя этого элемента **mediaElement1**.  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>Добавление панели инструментов окна инструментов  
 Путем добавления на панель инструментов следующим образом, можно гарантировать его градиенты и цвета согласования с остальной частью интегрированной среды разработки.  
  
1.  В **обозревателе решений**, откройте FirstToolWindowPackage.vsct. Vsct-файл определяет элементы графического пользовательского интерфейса (GUI) в окно инструментов с помощью XML.  
  
2.  В `<Symbols>` найдите `<GuidSymbol>` узел которого `name` атрибут `guidFirstToolWindowPackageCmdSet`. Добавьте следующие два `<IDSymbol>` элементы в список `<IDSymbol>` элементов в этот узел, чтобы определить, панель инструментов и панель инструментов группы.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Непосредственно над `<Buttons>` создайте `<Menus>` раздел, который выглядит следующим образом:  
  
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
  
     Существует несколько разных меню. Это меню — это панель инструментов в окне инструментов, определяется его `type` атрибута. `guid` И `id` параметры составляют полный идентификатор панели инструментов. Как правило `<Parent>` меню является объемлющей группы. Тем не менее панель инструментов определяется как собственным родителем. Таким образом, используется тот же идентификатор для `<Menu>` и `<Parent>` элементы. `priority` Атрибут является только "0".  
  
4.  Панели инструментов напоминают меню различными способами. Например так же, как группы команд, возможно, меню, панели инструментов может быть групп. (В меню, группы команд разделяются горизонтальных линий. На панели инструментов группы не разделяются visual разделителей.)  
  
     Добавить `<Groups>` раздел, содержащий `<Group>` элемента. Определяет группы, идентификатор которого объявлен в `<Symbols>` раздела. Добавить `<Groups>` статьи сразу после `<Menus>` раздела.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     Установив родительского GUID и идентификатор GUID и ID на панели инструментов, добавьте группу на панели инструментов.  
  
## <a name="add-a-command-to-the-toolbar"></a>Добавление команды на панель инструментов  
 Добавьте команду панели инструментов, которая отображается в виде кнопки.  
  
1.  В `<Symbols>` статьи, объявите следующие элементы IDSymbol сразу после панель инструментов и панель инструментов группы объявления.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Добавьте элемент кнопки внутри `<Buttons>` раздела. Этот элемент будет отображаться на панели инструментов в окне инструментов со значком поиска (с увеличительным стеклом).  
  
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
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     В результате команды доступны в коде.  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Добавить свойство MediaPlayer FirstToolWindowControl  
 От обработчиков событий для элементов управления панели инструментов код должен иметь доступ к управления проигрыватель, который является дочерним элементом класса FirstToolWindowControl.  
  
 В **обозревателе решений**, щелкните правой кнопкой мыши FirstToolWindowControl.xaml, нажмите кнопку **Просмотр кода**и добавьте следующий код в класс FirstToolWindowControl.  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>Создать окно инструментов и панели инструментов  
 Добавить панель инструментов и команды меню, который вызывает **открыть файл** диалоговое окно и воспроизводит файл мультимедиа.  
  
1.  Откройте FirstToolWindow.cs и добавьте следующие `using` инструкции.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  Внутри класса FirstToolWindow Добавьте открытый ссылку на элемент управления FirstToolWindowControl.  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  В конце конструктора установите для этой переменной элемента управления в только что созданный элемент управления.  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Создайте экземпляр инструментов внутри конструктора.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  На этом этапе конструктор FirstToolWindow должен выглядеть следующим образом:  
  
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
  
6.  Добавьте команду меню в панели инструментов. В классе FirstToolWindowCommand.cs, добавьте следующий с помощью инструкции  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
7.  В классе FirstToolWindowCommand добавьте следующий код в конце метода ShowToolWindow(). Команда ButtonHandler будет реализована в следующем разделе.  
  
    ```csharp  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Реализация команды меню в окне инструментов  
  
1.  Добавьте в класс FirstToolWindowCommand ButtonHandler метода, который вызывает **открыть файл** диалогового окна. При выборе файла его воспроизведение файла мультимедиа.  
  
2.  В классе FirstToolWindowCommand добавьте закрытый ссылку FirstToolWindow окна, которое создается в методе FindToolWindow().  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  Измените метод ShowToolWindow(), чтобы задать окно, которое определено выше (таким образом, обработчик команд ButtonHandler можно получить доступ к окна элемента управления. Ниже приведен полный метод ShowToolWindow().  
  
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
  
4.  Добавьте метод ButtonHandler. Он создает OpenFileDialog для пользователя указать файл мультимедиа, чтобы воспроизвести, и затем воспроизводит выбранного файла.  
  
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
  
## <a name="set-the-default-position-for-the-tool-window"></a>Задать положение по умолчанию для окна инструментов  
 Затем укажите расположение по умолчанию в IDE для окна инструментов. Сведения о конфигурации для окна инструментов — в файле FirstToolWindowPackage.cs.  
  
1.  Найдите в FirstToolWindowPackage.cs, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> атрибут `FirstToolWindowPackage` класс, который передает тип FirstToolWindow в конструктор. Позволяет указать положение по умолчанию, необходимо добавить дополнительные параметры в конструктор, в следующем примере.  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     Первый именованный параметр — `Style` и имеет значение `Tabbed`, что означает, что окно вкладки в существующее окно. Позиция закрепления задана `Window` параметра, n данном случае GUID **обозревателе решений**.  
  
    > [!NOTE]
    >  Дополнительные сведения о типах окон в Интегрированной среде разработки см. в разделе <xref:EnvDTE.vsWindowType>.  
  
## <a name="testing-the-tool-window"></a>Тестирование окна инструментов  
  
1.  Нажмите клавишу F5, чтобы открыть новый экземпляр Visual Studio экспериментальный сборки.  
  
2.  На **представление** последовательно выберите пункты **другие окна** и нажмите кнопку **первое окно средства**.  
  
     В окне инструментов media player следует открывать в той же позиции, что **обозревателе решений**. Если он по-прежнему находится в той же позиции, что перед, сброса структуры окон (**окна или восстановить параметры окон**).  
  
3.  Нажмите кнопку (он имеет значок поиска) в окне инструментов. Выберите поддерживаемые аудио или видео файла, например, C:\windows\media\chimes.wav нажмите клавишу **откройте**.  
  
     Вы должны услышать звук колокольчика.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)