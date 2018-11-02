---
title: Добавление контроллера меню на панель инструментов | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d6ccae3f53181863ada9dcaa93cb616431885cda
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830955"
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Добавление контроллера меню на панель инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это пошаговое руководство построено [Добавление панели инструментов в окно инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md) Пошаговое руководство и показано, как добавить контроллер меню в панели инструментов окна инструментов. Показанные здесь шаги также может применяться к панели инструментов, которая создается в [Добавление панели инструментов](../extensibility/adding-a-toolbar.md) Пошаговое руководство.  
  
 Контроллер меню — элемент управления split. В левой части меню контроллера показана команда последний использованный и его можно было выполнить, щелкнув его. В правой части контроллер меню — это стрелка, при нажатии открывается список дополнительных команд. При выбора команды в списке, выполняется команда, и он заменяет команды слева контроллера меню. В этом случае контроллер меню работает, как кнопки, всегда отображает последнее использованное команды из списка.  
  
 Контроллеры меню может отображаться в меню, но чаще всего используются на панелях инструментов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Создание контроллера меню  
  
#### <a name="to-create-a-menu-controller"></a>Чтобы создать контроллер меню  
  
1. Следуйте процедуре, описанной в [Добавление панели инструментов в окно инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md) создать окно инструментов, который содержит панель инструментов.  
  
2. В TWTestCommandPackage.vsct перейдите к разделу символы. В названный элемент GuidSymbol **guidTWTestCommandPackageCmdSet**, объявите контроллере меню, группы контроллера меню и трех пунктов меню.  
  
   ```xml  
   <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
   ```  
  
3. В разделе меню после последнего элемента меню, определите контроллер меню в виде меню.  
  
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
  
4. В группах разделе после последнего элемента группы, добавьте группу контроллера меню.  
  
   ```xml  
   <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
   </Group>  
   ```  
  
    Задавая контроллер меню как родительский, все команды, помещаются в эту группу будут отображаться в контроллер меню. `priority` Атрибут указан, который устанавливает значение по умолчанию 0, так как они будут только группы на контроллере меню.  
  
5. В разделе кнопок после последней записи кнопки, добавьте элемент кнопки для каждого элемента меню.  
  
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
  
6. На этом этапе можно взглянуть на контроллер меню. Выполните сборку решения и запустите отладку. Вы должны увидеть экспериментальный экземпляр.  
  
   1. На **представления / Other Windows** откройте в меню **окно инструментов тестирования**.  
  
   2. Контроллер меню отображается на панели инструментов в окне инструментов.  
  
   3. Щелкните стрелку в правой части контроллер меню, чтобы увидеть три возможных команд.  
  
      Обратите внимание, что при выборе команды заголовок контроллера меню изменяется для отображения этой команды. В следующем разделе мы добавим код, чтобы активировать эти команды.  
  
## <a name="implementing-the-menu-controller-commands"></a>Реализация команды меню контроллера  
  
1.  В TWTestCommandPackageGuids.cs добавьте идентификаторы команд для трех меню элементов после существующей команды идентификаторы.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  В TWTestCommand.cs добавьте следующий код в верхней части класса TWTestCommand.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  В конструкторе TWTestCommand после последнего вызова `AddCommand` метод, добавьте код для маршрутизации для каждой команды с помощью тех же обработчиков событий.  
  
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
  
5.  Добавление обработчика событий, который отображает окно MessageBox, когда пользователь выбирает команду на контроллере меню:  
  
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
  
## <a name="testing-the-menu-controller"></a>Тестирование контроллера меню  
  
1.  Выполните сборку решения и запустите отладку. Вы должны увидеть экспериментальный экземпляр.  
  
2.  Откройте **окно инструментов тестирования** на **представления / Other Windows** меню.  
  
     Контроллер меню отображается на панели инструментов в окне инструментов и отображает **MC элемент 1**.  
  
3.  Слева от стрелки, нажмите кнопку меню контроллера.  
  
     Вы должны увидеть три элемента, первая из которых установлен и имеет выделенный прямоугольник вокруг его значок. Нажмите кнопку **MC элемент 3**.  
  
     Появится диалоговое окно с сообщением **выбранного контроллера меню элемента 3**. Обратите внимание на то, что сообщение соответствует текст на кнопке меню контроллера. Кнопка контроллера меню теперь отображает **MC элемента 3**.  
  
## <a name="see-also"></a>См. также  
 [Добавление панели инструментов в окно инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)

