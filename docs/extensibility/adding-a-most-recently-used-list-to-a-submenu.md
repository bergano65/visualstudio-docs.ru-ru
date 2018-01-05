---
title: "Добавление недавно использовавшихся список в подменю | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: "46"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 087faaae07c4c240b53830ee238cee4f9065d21f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Добавление большинство недавно используемых список в подменю
Это пошаговое руководство построено на демонстрации в [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)и показано, как добавить в подменю динамический список. Динамический список формирует основу для создания списка наиболее недавно использованных файлов (MRU).  
  
 Динамический список меню начинается с заполнителем меню. Каждый раз отображается меню, среде разработки Visual Studio (IDE) запрашивает все команды, которые следует отобразить заполнитель VSPackage. В меню динамического списка может находиться где угодно. Однако динамические списки обычно сохраняется и выводится сами по себе, в нижней части меню или подменю. Используя эти шаблоны проектирования, включите динамический список команд, чтобы развернуть или свернуть, не затрагивая положение других команд меню. В этом пошаговом руководстве динамический список последних выбиравшихся файлов отображается в нижней части существующей подменю, отделены от остальной части подменю линией.  
  
 С технической точки зрения динамический список также может применяться к панели инструментов. Тем не менее мы не рекомендуем такого использования, так, как панель инструментов должно оставаться без изменений, если пользователь выполняет определенные действия, чтобы изменить его.  
  
 В этом пошаговом руководстве создается список последних выбиравшихся файлов четырех элементов, изменения порядка их каждый раз, что один из них выбран (Перемещение выбранного элемента вверху списка).  
  
 Дополнительные сведения о меню и vsct-файлами см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Создание расширения  
  
-   Следуйте инструкциям в разделе [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md) Создание подменю, который изменяется в следующих процедурах.  
  
 Процедуры, описанные в этом пошаговом руководстве предполагается, что имя VSPackage является `TopLevelMenu`, который имеет имя, которое используется в [добавлению меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Создание команды динамического элемента списка  
  
1.  Откройте TestCommandPackage.vsct.  
  
2.  В `Symbols` раздела `GuidSymbol` символ для добавления узла с именем guidTestCommandPackageCmdSet, `MRUListGroup` группы и `cmdidMRUList` команды, как показано ниже.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  В `Groups` статьи, добавьте группу объявленный после существующей группы записи.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  В `Buttons` добавьте узел для представления вновь объявленное команды, после существующих записей кнопки.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart` Флаг становится доступной команда формируется динамически.  
  
5.  Постройте проект и начните отладку для проверки отображения новой команды.  
  
     На **TestMenu** меню, щелкните новое подменю **подменю**, чтобы отобразить новой команды **MRU заполнитель**. После реализации динамический список последних Использованных команд в следующей процедуре эта метка команда будет заменен этим списком при каждом открытии подменю.  
  
## <a name="filling-the-mru-list"></a>Заполнение списка последних выбиравшихся файлов  
  
1.  В TestCommandPackageGuids.cs, добавьте следующие строки после существующих идентификаторов команд в `TestCommandPackageGuids` определения класса.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  Добавьте следующие строки в TestCommand.cs с помощью инструкции.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3.  Добавьте следующий код в конструктор TestCommand после последнего вызова AddCommand. `InitMRUMenu` Будут определены позже  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Добавьте следующий код в класс TestCommand. Этот код инициализирует список строк, которые представляют элементы, который будет отображаться в списке последних выбиравшихся файлов.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  После `InitializeMRUList` метод, добавьте `InitMRUMenu` метод. При этом будет инициализирована команды меню список последних выбиравшихся файлов.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     Необходимо создать объект команды меню для всех возможных элементов в списке последних выбиравшихся файлов. Интегрированная среда разработки вызовы `OnMRUQueryStatus` для каждого элемента в списке последних выбиравшихся файлов, пока не будут больше нет элементов. В управляемом коде единственным способом для интегрированной среды разработки знать, что отсутствуют дополнительные элементы является сначала создать все возможные элементы. Если требуется, можно пометить дополнительные элементы не видны в качестве сначала с помощью `mc.Visible = false;` после создания команды меню. Эти элементы можно затем сделать видимыми позже с помощью `mc.Visible = true;` в `OnMRUQueryStatus` метод.  
  
6.  После `InitMRUMenu` метод, добавьте следующий `OnMRUQueryStatus` метод. Этот метод является обработчиком, который задает текст для каждого элемента последних выбиравшихся файлов.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  После `OnMRUQueryStatus` метод, добавьте следующий `OnMRUExec` метод. Этот метод является обработчиком для выбора элемента последних выбиравшихся файлов. Этот метод перемещает выбранный элемент в верхней части списка, а затем отображает элемент, выбранный в окне сообщения.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>Тестирование список последних выбиравшихся файлов  
  
#### <a name="to-test-the-mru-menu-list"></a>Чтобы проверить список меню последних выбиравшихся файлов  
  
1.  Постройте проект и начните отладку  
  
2.  На **TestMenu** меню, нажмите кнопку **TestCommand вызова**. В результате откроется окно сообщения, которое указывает, что команда была выбрана.  
  
    > [!NOTE]
    >  Этот шаг необходим для принудительного VSPackage для загрузки и правильно отобразить список последних выбиравшихся файлов. Если пропустить этот шаг, ДАННЫЙ список не отображается.  
  
3.  На **меню тест** меню, нажмите кнопку **подменю**. Четыре элемента отображаются в конце подменю ниже разделителя. При нажатии кнопки **элемент 3**, окно сообщения должен отображаться, а также отображать текст «Выбранный элемент 3». (Если список четырех элементов не отображается, убедитесь, что выполнены инструкции в предыдущем шаге.)  
  
4.  Снова откройте подменю. Обратите внимание, что **элемент 3** теперь находится в верхней части списка и других элементов помещено на одну позицию вниз. Нажмите кнопку **элемент 3** снова и обратите внимание, что в окне сообщения по-прежнему отображается «Выбранный элемент 3», который указывает, что текст правильно был перемещен на новое место вместе с команду метки.  
  
## <a name="see-also"></a>См. также  
 [Динамическое добавление элементов меню](../extensibility/dynamically-adding-menu-items.md)