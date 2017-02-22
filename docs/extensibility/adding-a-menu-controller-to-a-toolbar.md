---
title: "Добавление контроллера меню панели инструментов | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Добавление контроллеров меню панели инструментов [Visual Studio]"
  - "меню, Добавление контроллеров меню панели инструментов"
  - "контроллеры меню, добавление в панель инструментов"
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
caps.handback.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
---
# Добавление контроллера меню панели инструментов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом пошаговом руководстве основано руководство [Добавление панели инструментов в окне инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md) пошаговом руководстве демонстрируется добавление контроллера меню на панели инструментов окна. Приведенные ниже действия также могут применяться к панели инструментов, которая создается в [Добавление панели инструментов](../extensibility/adding-a-toolbar.md) Пошаговое руководство.  
  
 Контроллер меню является элементом управления разбиения. В левой части меню контроллера показаны последние использованные команды, и его можно запустить, щелкнув его. В правой части меню контроллер является стрелки, при нажатии открывается список дополнительных команд. При выборе команды в списке, и выполнения команды и заменяет команды слева от контроллера меню. Таким образом контроллер меню работает, как кнопки, всегда отображает последние использованные команды из списка.  
  
 Контроллеры меню может отображаться в меню, но чаще всего используются на панели инструментов.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание контроллера меню  
  
#### Чтобы создать контроллер меню  
  
1.  Следуйте процедурам, описанным в [Добавление панели инструментов в окне инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md) для создания окна инструментов, которое содержит панель инструментов.  
  
2.  В TWTestCommandPackage.vsct перейдите к разделу символы. В элементе GuidSymbol с именем **guidTWTestCommandPackageCmdSet**, объявлять контроллер меню, группы меню контроллера и три элемента меню.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  В разделе меню после последнего элемента меню, определите контроллер меню как меню.  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     `TextChanges` И `TextIsAnchorCommand` флаги должен быть включен, чтобы разрешить в контроллере меню в соответствии с последней выбранной команды.  
  
4.  В группах статьи после последней группы записи, добавьте группу меню контроллера.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Задавая контроллер меню как родительский, все команды, помещаются в эту группу будут отображаться в меню контроллера.`priority` Атрибут опущен, который задает значение по умолчанию 0, так как они будут только группы на контроллере меню.  
  
5.  В разделе кнопки после последнего элемента button, добавьте элемент кнопки для каждого из элементов меню.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  На этом этапе можно взглянуть на контроллере меню. Выполните сборку решения и запустите отладку. Вы должны увидеть экспериментальный экземпляр.  
  
    1.  На **представления и другие окна** откройте в меню **окно инструментов тестирования**.  
  
    2.  Контроллер меню появляется на панели инструментов в окне инструментов.  
  
    3.  Щелкните стрелку справа контроллера для отображения три возможных команд меню.  
  
     Обратите внимание, при выборе команды title контроллера меню изменяется для отображения этой команды. В следующем разделе мы добавим код, чтобы активировать эти команды.  
  
## Реализация команды меню контроллера  
  
1.  Добавьте в TWTestCommandPackageGuids.cs, идентификаторы команд для элементов меню три после идентификаторы существующих команд.  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  В TWTestCommand.cs добавьте следующий код в начало класса TWTestCommand.  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  В конструкторе TWTestCommand после последнего вызова метода `AddCommand` метод, добавьте код для маршрутизации для каждой команды с помощью тех же обработчиков событий.  
  
    ```c#  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Добавьте обработчик событий в класс TWTestCommand, чтобы пометить выбранную команду как checked.  
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Добавьте обработчик событий, который отображает MessageBox, когда пользователь выбирает команду меню контроллера:  
  
    ```c#  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## Тестирование контроллера меню  
  
1.  Выполните сборку решения и запустите отладку. Вы должны увидеть экспериментальный экземпляр.  
  
2.  Откройте **окно инструментов тестирования** на **представления и другие окна** меню.  
  
     Контроллер меню появляется на панели инструментов в окне инструментов и отображает **MC элемент 1**.  
  
3.  Нажмите кнопку контроллера слева от стрелки.  
  
     Вы должны увидеть три элемента, первый из которых установлен и имеется поле выделения вокруг его значок. Щелкните **MC элемент 3**.  
  
     Появится диалоговое окно с сообщением **Выбранные контроллера меню элемента 3**. Обратите внимание, что сообщение соответствует текст на кнопке меню контроллера. Теперь отображает кнопки меню контроллера **MC элемента 3**.  
  
## См. также  
 [Добавление панели инструментов в окне инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)