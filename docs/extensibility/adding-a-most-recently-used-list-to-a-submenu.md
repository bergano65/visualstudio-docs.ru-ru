---
title: Добавление недавно использованного списка в Submenu (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf389c0da7ec0aafb6e47dae8f09ffdc3b1d1e4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740300"
---
# <a name="add-a-most-recently-used-list-to-a-submenu"></a>Добавьте самый последний использованный список в подменю
Это пошаговое решение основывается на демонстрациях в [Добавлении подменю](../extensibility/adding-a-submenu-to-a-menu.md)в меню и показывает, как добавить динамический список в подменю. Динамический список является основой для создания списка most Recently Used (MRU).

Динамический список меню начинается с заполнителя в меню. Каждый раз, когда меню отображается, Visual Studio интегрированной среды разработки (IDE) просит VSPackage для всех команд, которые должны быть показаны на заполнителе. Динамический список может произойти в любом месте меню. Тем не менее, динамические списки обычно хранятся и отображаются сами по себе на подменю или в нижней части меню. Используя эти шаблоны проектирования, вы позволяете динамическому списку команд расширяться и сокращаться, не влияя на положение других команд в меню. В этом пошаговом слове динамический список MRU отображается в нижней части существующего подменю, отделенного от остальной части подменю строкой.

Технически динамический список также может быть применен к панели инструментов. Однако мы не рекомендуем использовать это использование, поскольку панель инструментов должна оставаться неизменной, если пользователь не предпримет определенные шаги для ее изменения.

Это пошаговое решение создает список MRU из четырех элементов, которые меняют свой порядок каждый раз при выборе одного из них (выбранный элемент перемещается в верхнюю часть списка).

Для получения дополнительной информации о меню и файлах *.vsct* смотрите [команды, меню и панели инструментов.](../extensibility/internals/commands-menus-and-toolbars.md)

## <a name="prerequisites"></a>Предварительные требования
Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Для получения дополнительной информации, [см.](../extensibility/visual-studio-sdk.md)

## <a name="create-an-extension"></a>Создание расширений

- Следуйте процедурам [добавления подменю](../extensibility/adding-a-submenu-to-a-menu.md) в меню для создания подменю, которое изменяется в следующих процедурах.

  Процедуры в этом пошаговое решение предполагают, `TopLevelMenu`что название VSPackage является , который является имя, которое используется в [Добавить меню в меню visual Studio бар](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).

## <a name="create-a-dynamic-item-list-command"></a>Создание команды динамического списка элементов

1. Открытый *TestCommandPackage.vsct*.

2. В `Symbols` разделе, в `GuidSymbol` уде под названием guidTestCommandPackageCmdSet, добавьте символ для `MRUListGroup` группы и `cmdidMRUList` команды, следующим образом.

    ```csharp
    <IDSymbol name="MRUListGroup" value="0x1200"/>
    <IDSymbol name="cmdidMRUList" value="0x0200"/>
    ```

3. В `Groups` разделе добавьте заявленную группу после существующих записей группы.

    ```cpp
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"
            priority="0x0100">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>

    ```

4. В `Buttons` разделе добавьте узла для представления недавно объявленной команды после существующих записей кнопок.

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

    Флаг `DynamicItemStart` позволяет динамически сгенерировать команду.

5. Создайте проект и начните отладку для тестирования отображения новой команды.

    В меню **TestMenu** щелкните новое подменю, **Sub Menu,** чтобы отобразить новую команду, **MRU Placeholder**. После того, как динамический список команд MRU будет реализован в следующей процедуре, эта метка команд будет заменена этим списком каждый раз, когда откроется submenu.

## <a name="filling-the-mru-list"></a>Заполнение списка MRU

1. В *TestCommandPackageGuids.cs*добавлены следующие строки после существующих `TestCommandPackageGuids` идентифицированных команд в определении класса.

    ```csharp
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file
    public const uint cmdidMRUList = 0x200;
    ```

2. В *TestCommand.cs* добавить следующее заявление с использованием.

    ```csharp
    using System.Collections;
    ```

3. Добавьте следующий код в конструктор TestCommand после последнего вызова AddCommand. Будет `InitMRUMenu` определено позже

    ```csharp
    this.InitMRUMenu(commandService);
    ```

4. Добавьте следующий код в классе TestCommand. Этот код инициализирует список строк, представляющих элементы, которые будут отображаться в списке MRU.

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

5. После `InitializeMRUList` метода добавьте `InitMRUMenu` метод. Это инициализирует команды меню списка MRU.

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

    Необходимо создать объект команды меню для каждого возможного элемента в списке MRU. IDE вызывает `OnMRUQueryStatus` метод для каждого элемента в списке MRU до тех пор, пока не будет больше элементов. В управляемом коде единственный способ для IDE знать, что больше нет элементов, это сначала создать все возможные элементы. При желании можно пометить дополнительные элементы `mc.Visible = false;` как не видимые сначала, используя команду меню. Эти элементы могут быть видны `mc.Visible = true;` позже с помощью метода. `OnMRUQueryStatus`

6. После `InitMRUMenu` метода добавьте `OnMRUQueryStatus` следующий метод. Это обработчик, который устанавливает текст для каждого элемента MRU.

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

7. После `OnMRUQueryStatus` метода добавьте `OnMRUExec` следующий метод. Это обработчик для выбора элемента MRU. Этот метод перемещает выбранный элемент в верхнюю часть списка, а затем отображает выбранный элемент в поле сообщений.

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

## <a name="testing-the-mru-list"></a>Тестирование списка MRU

1. Выполните сборку решения и запустите отладку.

2. В меню **TestMenu** нажмите **Наймите Invoke TestCommand**. При этом отображается поле сообщений, указывававое, что команда была выбрана.

    > [!NOTE]
    > Этот шаг необходим для того, чтобы заставить VSPackage загрузить и правильно отобразить список MRU. Если вы пропустите этот шаг, список MRU не отображается.

3. В меню **меню тестового меню** щелкните **Sub Menu**. Список из четырех элементов отображается в конце подменю, ниже сепаратора. При нажатии **пункта 3**, окно сообщения должно появиться и отобразить текст, **Выбранный пункт 3**. (Если список из четырех элементов не отображается, убедитесь, что вы следовали инструкциям на предыдущем этапе.)

4. Откройте подменю снова. Обратите внимание, что **пункт 3** в настоящее время в верхней части списка и другие элементы были толкнул вниз одну позицию. Нажмите **пункт 3** снова и обратите внимание, что поле сообщения по-прежнему отображает **Выбранный пункт 3**, который указывает, что текст правильно переехал в новое положение вместе с меткой команды.

## <a name="see-also"></a>См. также
- [Динамическое добавление элементов меню](../extensibility/dynamically-adding-menu-items.md)
