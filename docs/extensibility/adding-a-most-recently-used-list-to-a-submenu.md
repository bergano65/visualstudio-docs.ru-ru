---
title: "Добавление наиболее недавно использовавшегося списка в подменю | Microsoft Docs"
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
  - "списки последних выбиравшихся файлов"
  - "меню, Создание списка Использованных"
  - "самые последние использовавшиеся"
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 46
caps.handback.revision: 46
ms.author: "gregvanl"
manager: "ghogen"
---
# Добавление наиболее недавно использовавшегося списка в подменю
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом пошаговом руководстве основано руководство демонстрации в [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md), и показано, как добавить в подменю динамического списка. Динамический список формирует основу для создания списка наиболее недавно использованных файлов \(MRU\).  
  
 Список динамических меню начинается с заполнитель меню. Каждый раз, когда меню отображается, среда разработки Visual Studio \(IDE\) запрашивает все команды, которые следует отобразить заполнитель VSPackage. Динамический список могут встречаться в меню. Однако динамические списки обычно хранятся и отображаются сами по себе подменю, либо в нижней части меню. Используя эти шаблоны проектирования, включите динамический список команд, чтобы развернуть или свернуть без влияния на положение других команд меню. В этом пошаговом руководстве динамический список отображается в нижней части существующего подменю, отделены от остальной части подменю линией.  
  
 С технической точки зрения динамического списка могут также применяться на панель инструментов. Тем не менее не рекомендуется такого использования, поскольку панель инструментов должно оставаться без изменений, если пользователь выполняет определенные действия, чтобы изменить его.  
  
 В этом пошаговом руководстве создается список последних Использованных четырех элементов, изменения их порядка, каждый раз, что один из них установлен \(выбранный элемент перемещается в верхней части списка\).  
  
 Дополнительные сведения о меню и vsct\-файлах см. в разделе [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Обязательные компоненты  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации см. [SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Создание расширения  
  
-   Следуйте инструкциям в разделе [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md) Создание подменю, которое изменяется в следующих процедурах.  
  
 Процедуры в этом пошаговом руководстве предполагается, что имя VSPackage — `TopLevelMenu`, это имя, используемое в [Добавление меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## Создание команды список динамических элементов  
  
1.  Откройте TestCommandPackage.vsct.  
  
2.  В `Symbols` раздела `GuidSymbol` узел с именем guidTestCommandPackageCmdSet, добавьте символ для `MRUListGroup` группы и `cmdidMRUList` команды, как показано ниже.  
  
    ```c#  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  В `Groups` статьи, добавьте объявленную группу после существующей группы записи.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  В `Buttons` добавьте узел, представляющий вновь объявленное команды после существующих записей кнопки.  
  
    ```c#  
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
  
     `DynamicItemStart` Флаг позволяет команде формируется динамически.  
  
5.  Построить проект и запустить отладку для тестирования новой команды.  
  
     На **TestMenu** меню, щелкните новое подменю **подменю**, чтобы отобразить новую команду **заполнитель MRU**. После реализации динамический список наиболее часто Используемых команд в следующей процедуре эта метка команда будет заменен этот список при каждом открытии подменю.  
  
## Заполнение списка  
  
1.  В TestCommandPackageGuids.cs, добавьте следующие строки после существующих идентификаторов команд в `TestCommandPackageGuids` Определение класса.  
  
    ```c#  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  В TestCommand.cs добавьте следующий оператор using.  
  
    ```c#  
    using System.Collections;  
    ```  
  
3.  Добавьте следующий код в конструктор TestCommand после последнего вызова метода AddCommand.`InitMRUMenu` Будут определены в дальнейшем  
  
    ```c#  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Добавьте следующий код в класс TestCommand. Этот код инициализирует список строк, которые представляют элементы, который будет отображаться в списке MRU.  
  
    ```c#  
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
  
5.  После `InitializeMRUList` метод, добавление `InitMRUMenu` метод. Команды меню список последних Использованных при этом инициализируется.  
  
    ```c#  
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
  
     Необходимо создать объект команды меню для всех возможных элементов в списке. Интегрированная среда разработки вызывает `OnMRUQueryStatus` для каждого элемента в списке пока нет дополнительных элементов. В управляемом коде единственным способом для интегрированной среды разработки знать, что нет дополнительных элементов является сначала создать все возможные элементы. Если требуется, можно пометить дополнительные элементы не видны в качестве сначала с помощью `mc.Visible = false;` После создания команды меню. Эти элементы можно затем сделать видимыми позже с помощью `mc.Visible = true;` в `OnMRUQueryStatus` метод.  
  
6.  После `InitMRUMenu` метод, добавьте следующий `OnMRUQueryStatus` метод. Это обработчик, который задает текст для каждого элемента список последних использованных файлов.  
  
    ```c#  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  После `OnMRUQueryStatus` метод, добавьте следующий `OnMRUExec` метод. Это обработчик для выбора элемента MRU. Этот метод перемещает элемент, выбранный в верхней части списка, а затем отображает элемент, выбранный в окне сообщения.  
  
    ```c#  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
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
  
## Список последних Использованных тестирования  
  
#### Чтобы проверить список последних Использованных меню  
  
1.  Построить проект и запустить отладку  
  
2.  На **TestMenu** меню, щелкните **вызова TestCommand**. Отобразится окно сообщения, которое указывает, что команда была выбрана.  
  
    > [!NOTE]
    >  Этот шаг необходим для принудительного VSPackage для загрузки и правильно отобразить список последних Использованных. Если пропустить этот шаг, данный список не отображается.  
  
3.  На **меню тест** меню, щелкните **подменю**. В конце подменю ниже разделителя отображается список из четырех элементов. При нажатии кнопки **товара 3**, должен присутствовать и отображения текста, окно сообщения «выбранному элементу 3». \(Если список четырех элементов не отображается, убедитесь, что выполнены инструкции в предыдущем шаге.\)  
  
4.  Снова откройте подменю. Обратите внимание, что **товара 3** теперь находится в верхней части списка и других элементов, которые будут отправлены на одну позицию вниз. Нажмите кнопку **элемент 3** снова и обратите внимание, что в окне сообщения по\-прежнему отображается «выбранному элементу 3», который указывает, что текст правильно был перемещен на новое место вместе с метки команды.  
  
## См. также  
 [Динамическое добавление элементов меню](../extensibility/dynamically-adding-menu-items.md)