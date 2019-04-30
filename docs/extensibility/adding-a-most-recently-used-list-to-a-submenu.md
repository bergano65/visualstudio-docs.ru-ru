---
title: Добавление недавно использовавшийся списка в подменю | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 462f59d472c6de8872394b2eadd5f33aa27bccca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843830"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Добавление недавно использовавшийся списка в подменю
Это пошаговое руководство построено на демонстрации в [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)и показано, как добавить в подменю динамический список. Список динамического формирует основу для создания списка наиболее недавно использовавшихся Элементов.

Динамический список меню начинается с заполнителем меню. Каждый раз, когда меню отображается, в среде разработки Visual Studio (IDE) запрашивает все команды, которые следует отобразить заполнитель VSPackage. В меню динамического списка может находиться где угодно. Тем не менее динамические списки обычно сохраняется и выводится сами по себе, в нижней части меню или подменю. Используя эти шаблоны разработки, как разрешить динамический список команд, чтобы развернуть или свернуть, не влияя на положение других команд меню. В этом пошаговом руководстве динамический список отображается в нижней части существующего вложенного меню, отделен от остальной части подменю строкой.

С технической точки зрения динамического списка также может применяться к панели инструментов. Тем не менее мы не рекомендуется, так как панель инструментов должно оставаться без изменений, если пользователь выполняет определенные действия, чтобы изменить его.

В этом пошаговом руководстве создается список последних выбиравшихся файлов из четырех элементов, изменения их порядка, каждый раз, что один из них выбран (выбранный элемент перемещается к верхней части списка).

Дополнительные сведения о меню и *.vsct* файлы, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Предварительные требования
Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="create-an-extension"></a>Создание расширения

- Выполните процедуры, описанные в [Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md) создать подменю, который изменяется в следующих процедурах.

  Процедуры, описанные в этом пошаговом руководстве предполагается, что называется VSPackage `TopLevelMenu`, который является имя, которое используется в [добавить меню в строке меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Создать команду динамического элемента списка

1. Откройте *TestCommandPackage.vsct*.

2. В `Symbols` раздела `GuidSymbol` узел с именем guidTestCommandPackageCmdSet, добавьте символ для `MRUListGroup` группы и `cmdidMRUList` команды, как показано ниже.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. В `Groups` добавьте объявленную группу после существующей группы записи.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. В `Buttons` добавьте узел для представления команды вновь объявленное после существующих записей кнопки.

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

    `DynamicItemStart` Флаг позволяет команде формируется динамически.

5. Постройте проект и начать отладку, чтобы протестировать новые команды.

    На **TestMenu** меню, щелкните новый подменю **подменю**, чтобы отобразить новую команду, **MRU заполнитель**. После реализации динамического списка Использованных команд в следующей процедуре, эта команда метка будет заменен этого списка каждый раз, которое открывается подменю.

## <a name="filling-the-mru-list"></a>Заполнение списку MRU

1. В *TestCommandPackageGuids.cs*, добавьте следующие строки после существующего идентификаторы команд в `TestCommandPackageGuids` определение класса.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. В *TestCommand.cs* добавьте следующий оператор using.

    ```csharp
    using System.Collections;
    ```

3. Добавьте следующий код в конструктор тестовую команду после последнего вызова AddCommand. `InitMRUMenu` Будут определены позже

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Добавьте следующий код в классе тестовую команду. Этот код инициализирует список строк, представляющих элементов, отображаемых в списке последних выбиравшихся файлов.

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

5. После `InitializeMRUList` метод, добавьте `InitMRUMenu` метод. При этом будет инициализирована команды меню списка последних выбиравшихся файлов.

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

    Необходимо создать командный объект меню для всех возможных элементов в списке последних выбиравшихся файлов. Интегрированная среда разработки вызовы `OnMRUQueryStatus` для каждого элемента в списке последних выбиравшихся файлов, пока имеется больше нет элементов. В управляемом коде единственным способом для интегрированной среды разработки знать, что отсутствуют дополнительные элементы — это сначала создать все возможные элементы. Если требуется, можно пометить дополнительные элементы как невидимые в сначала с помощью `mc.Visible = false;` после создания команды меню. Эти элементы можно затем сделать видимыми позже с помощью `mc.Visible = true;` в `OnMRUQueryStatus` метод.

6. После `InitMRUMenu` метод, добавьте следующий `OnMRUQueryStatus` метод. Это обработчик, который задает текст для каждого элемента в списке последних выбиравшихся файлов.

    ```csharp
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

7. После `OnMRUQueryStatus` метод, добавьте следующий `OnMRUExec` метод. Это обработчик для выбора элемента MRU. Этот метод перемещает выбранный элемент в верхней части списка и затем отображает элемент, выбранный в окне сообщения.

    ```csharp
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

## <a name="testing-the-mru-list"></a>Тестирование списку MRU

1. Выполните сборку решения и запустите отладку.

2. На **TestMenu** меню, щелкните **тестовую команду вызова**. В результате откроется окно сообщения, которое указывает, что команда была выбрана.

    > [!NOTE]
    > Этот шаг необходим для принудительного VSPackage для загрузки и правильно отобразить список последних выбиравшихся файлов. Если пропустить этот шаг, данный список не отображается.

3. На **меню "Тест"** меню, щелкните **подменю**. В конце подменю, ниже разделитель отображается список из четырех элементов. При нажатии кнопки **элемента 3**, появится окно сообщения с отображать текст, **выбранного элемента 3**. (Если список четырех элементов не отображается, убедитесь, что вы следовали инструкциям в предыдущем шаге.)

4. Снова откройте подменю. Обратите внимание, что **элемента 3** теперь находится в верхней части списка и других элементов, отправленных на одну позицию вниз. Нажмите кнопку **3 элемента** снова и обратите внимание, что в окне сообщения по-прежнему отображаются **выбранного элемента 3**, что означает, что текст правильно были перемещены в новое место вместе с команду метки.

## <a name="see-also"></a>См. также
- [Динамическое добавление элементов меню](../extensibility/dynamically-adding-menu-items.md)
