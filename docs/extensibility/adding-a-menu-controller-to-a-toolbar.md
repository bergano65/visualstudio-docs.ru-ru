---
title: "Контроллер меню добавляется на панель инструментов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 786d7c8841f680d5af5c539e30723289df4db0f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Контроллер меню добавляется на панель инструментов
Это пошаговое руководство построено [Добавление панели инструментов в окне инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md) Пошаговое руководство и показано, как добавить контроллер меню в панели инструментов окна инструментов. Описанные здесь действия также могут применяться к панели инструментов, которая создается в [Добавление панели инструментов](../extensibility/adding-a-toolbar.md) Пошаговое руководство.  
  
 Контроллер меню — это элемент управления разбиения. В левой части меню контроллера показаны последние использованные команды, и его можно запустить, щелкнув его. В правой части контроллер меню — стрелка, при нажатии открывается список дополнительных команд. При выборе команды в списке, и выполняется команда, и заменяет команда контроллера меню слева. Таким образом как кнопки, всегда отображаются последние использованные команды из списка функционирует контроллер меню.  
  
 Контроллеры меню может отображаться в меню, но чаще всего используются на панели инструментов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Создание контроллера меню  
  
#### <a name="to-create-a-menu-controller"></a>Чтобы создать контроллер меню  
  
1.  Следуйте процедурам, описанным в [Добавление панели инструментов в окне инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md) для создания окна инструментов, которое содержит панель инструментов.  
  
2.  В TWTestCommandPackage.vsct перейдите к разделу символы. В элементе GuidSymbol с именем **guidTWTestCommandPackageCmdSet**, объявите контроллер меню, группы меню контроллера и трех элементов меню.  
  
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
  
     `TextChanges` И `TextIsAnchorCommand` флаги должен быть включен, чтобы включить контроллер меню в соответствии с последней выбранной команды.  
  
4.  В группах статьи после последней группы записи, добавьте группу контроллер меню.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Задавая контроллер меню как родительский элемент, все команды, размещена в этой группе будут отображаться в меню контроллера. `priority` Опустить атрибут, который задает значение по умолчанию 0, так как они будут только группы на контроллере меню.  
  
5.  В разделе кнопки после последней записи кнопки, добавьте элемент кнопки для каждого из элементов меню.  
  
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
  
6.  На этом этапе можно взглянуть на контроллер меню. Выполните сборку решения и запустите отладку. Вы увидите экспериментальный экземпляр.  
  
    1.  На **представления и другие окна** выберите пункт **окно инструментов тестирования**.  
  
    2.  Контроллер меню появляется на панели инструментов в окне инструментов.  
  
    3.  Щелкните стрелку справа контроллера все три возможных команды меню.  
  
     Обратите внимание, как команда выбрана, заголовок контроллер меню изменяется для отображения этой команды. В следующем разделе мы добавим код, чтобы активировать эти команды.  
  
## <a name="implementing-the-menu-controller-commands"></a>Реализация команды меню контроллера  
  
1.  В TWTestCommandPackageGuids.cs добавьте идентификаторы команд для меню трех элементов после существующей команды идентификаторы.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  В TWTestCommand.cs добавьте следующий код в верхней части класса TWTestCommand.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  В конструкторе TWTestCommand после последнего вызова `AddCommand` метод, добавьте код для маршрутизации для каждой команды через тех же обработчиков событий.  
  
    ```csharp  
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
  
4.  Добавьте обработчик событий к классу TWTestCommand Пометить выбранные команды в виде checked.  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Добавьте обработчик событий, отображает MessageBox, когда пользователь выбирает команду меню контроллера:  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
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
  
## <a name="testing-the-menu-controller"></a>Меню контроллера тестирования  
  
1.  Выполните сборку решения и запустите отладку. Вы увидите экспериментальный экземпляр.  
  
2.  Откройте **окно инструментов тестирования** на **представления и другие окна** меню.  
  
     Контроллер меню отображается на панели инструментов в окне инструментов и отображает **MC элемент 1**.  
  
3.  Слева от стрелки, нажмите кнопку меню контроллера.  
  
     Должны появиться три элемента, в первом из которых установлен и имеется поле выделения вокруг ее значок. Нажмите кнопку **MC элемент 3**.  
  
     Появится диалоговое окно с сообщением **выбранного контроллера меню элемент 3**. Обратите внимание, что сообщение соответствует текста на кнопке контроллер меню. Теперь отображает кнопку меню контроллера **MC элемент 3**.  
  
## <a name="see-also"></a>См. также  
 [Добавление панели инструментов в окне инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)