---
title: команды MenuCommand и OleMenuCommands | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
manager: douge
ms.openlocfilehash: 47ec8bd549f8f5093a7035f37ad728c1e245e3b9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147194"
---
# <a name="menucommands-vs-olemenucommands"></a>команды MenuCommand и OleMenuCommand
Вы можете создавать команды меню на основе объекта <xref:System.ComponentModel.Design.MenuCommand> или <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> и реализовывать соответствующие обработчики событий. В большинстве случаев можно использовать <xref:System.ComponentModel.Design.MenuCommand>, как это делает шаблон проекта VSPackage, но иногда может потребоваться использовать <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>.  
  
 Команды, которые VSPackage делает доступными в IDE, должны быть видимы и включены, чтобы пользователь смог их применять. Если команды создаются в VSCT-файле с помощью шаблона Visual Studio Package для проектов, то они видимы и включены по умолчанию. Устанавливая некоторые флаги команд, например `DynamicItemStart`, можно изменить это поведение по умолчанию. Видимость, включенность и другие свойства команды также можно изменять в коде во время выполнения, обратившись к объекту <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> , связанному с командой.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Расположения для шаблона пакета Visual Studio  
 Шаблон Visual Studio Package можно найти в диалоговом окне **Создание проекта** , развернув узлы **Visual Basic/Extensibility**(Visual Basic/Расширение среды), **C#/Extensibility**(C#/Расширение среды) или **Другие типы проектов/Расширение среды**.  
  
## <a name="creating-a-command"></a>Создание команды  
 Все команды, группы команд, меню, панели инструментов и окна инструментов определяются в VSCT-файле. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Если вы создаете VSPackage с помощью шаблона пакета, выберите пункт **Команда меню** , чтобы создать VSCT-файл и определить команду меню по умолчанию. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>Добавление команды в IDE  
  
1.  Откройте VSCT-файл.  
  
2.  В разделе `Symbols` найдите элемент [GuidSymbol](../extensibility/guidsymbol-element.md) , содержащий группы и команды.  
  
3.  Создайте по элементу [IDSymbol](../extensibility/idsymbol-element.md) для каждого меню, группы и команды, которые нужно добавить, как показано в следующем примере.  
  
     <!--FIXME [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  -->
    ```xaml  
    <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
      <IDSymbol name="MyMenuGroup" value="0x1020" />
      <IDSymbol name="cmdidMyCommand" value="0x0100" />
    </GuidSymbol>
    ```  
  
    Атрибуты `name` элементов `GuidSymbol` и `IDSymbol` предоставляют пару GUID:ID для каждого нового меню, группы или команды. `guid` представляет набор команд, определенных для вашего VSPackage. Можно определить несколько наборов команд. Каждая пара GUID:ID должна быть уникальной.  
  
4.  В разделе [Buttons](../extensibility/buttons-element.md) создайте элемент [Button](../extensibility/button-element.md) (кнопка) для определения команды, как показано в следующем примере.  
  
     <!--FIXME [!CODE [ButtonGroup#03](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#03)]  -->
    ```xaml  
    <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```  
  
    1.  Задайте поля `guid` и `id` , чтобы они соответствовали GUID:ID новой команды.  
  
    2.  Задайте атрибут `priority` .  
  
         Атрибут `priority` используется VSCT-файлом для определения расположения кнопки среди других объектов в родительской группе.  
  
         Команды, имеющие более низкий приоритет, отображаются над командами с более высоким приоритетом или слева от них. Одинаковые значения приоритета разрешены, но относительное расположение команд с одинаковым приоритетом определяется порядком, в котором пакеты VSPackage обрабатываются во время выполнения, и этот порядок нельзя определить заранее.  
  
         Если атрибут `priority` пропустить, он получает значение 0.  
  
    3.  Задайте атрибут `type` . В большинстве случаев его значение будет равно `"Button"`. Описание других допустимых типов кнопки см. в разделе [Button Element](../extensibility/button-element.md).  
  
5.  В определении кнопки создайте элемент [Strings](../extensibility/strings-element.md) , включающий элемент [ButtonText](../extensibility/buttontext-element.md) , который содержит имя меню, отображаемое в IDE, и элемент [CommandName](../extensibility/commandname-element.md) , который содержит имя команды, используемой для доступа к этому меню в окне **Команда** .  
  
     Если строка текста кнопки содержит символ &, пользователь может открыть меню, нажав клавишу ALT и клавишу, указанную после символа &.  
  
     При добавлении элемента `Tooltip` содержащийся в нем текст будет отображаться, когда пользователь наведет указатель на кнопку.  
  
6.  Добавьте элемент [Icon](../extensibility/icon-element.md) , чтобы указать значок, который должен отображаться с командой. Значки требуются для кнопок на панели инструментов, но не для пунктов меню. Поля `guid` и `id` элемента `Icon` должны соответствовать таким же полям элемента [Bitmap](../extensibility/bitmap-element.md) , определенного в разделе `Bitmaps` .  
  
7.  Добавьте флаги команды, чтобы соответствующим образом изменить внешний вид и поведение кнопки. Для этого добавьте элемент [CommandFlag](../extensibility/command-flag-element.md) в определение меню.  
  
8.  Задайте родительскую группу команды. Родительская группа может быть создаваемой группой, группой из другого пакета или группой из IDE. Например, чтобы добавить команду в панель инструментов редактирования Visual Studio рядом с кнопками **Комментарий** и **Удалить комментарий** , задайте родительскую группу guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT. Если родительская группа является определяемой пользователем, она должна быть дочерним элементом меню, панели инструментов или окна инструментов в IDE.  
  
     В зависимости от проекта это можно сделать одним из двух способов.  
  
    -   В элементе `Button` создайте элемент [Parent](../extensibility/parent-element.md) и укажите в его полях `guid` и `id` Guid и ID (идентификатор) группы, где будет размещаться команда, которая также называется *основной родительской группой*.  
  
         В следующем примере задается команда, которая будет отображаться в определяемом пользователем меню.  
  
         <!--FIXME [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  -->
        ```xaml  
        <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
          <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
          <Icon guid="guidImages" id="bmpPic1" />
          <Strings>
            <CommandName>cmdidTestCommand</CommandName>
            <ButtonText>Test Command</ButtonText>
          </Strings>
        </Button>
        ```  
  
    -   Вы можете опустить элемент `Parent` , если команду предполагается размещать с помощью функции размещения команд. Создайте элемент [CommandPlacements](../extensibility/commandplacements-element.md) перед разделом `Symbols` и добавьте элемент [CommandPlacement](../extensibility/commandplacement-element.md) , имеющий `guid` и `id` команды, `priority`и родительский объект, как показано в следующем примере.  
  
         <!-- FIXME [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)] -->  
        ```xaml  
        <CommandPlacements>
          <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
            <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
          </CommandPlacement>
        </CommandPlacements>
        ```  
  
         Если создать несколько размещений команд, имеющих одинаковые пары GUID:ID и разные родительские группы, меню будет отображаться в нескольких местах. Дополнительные сведения см. в описании элемента [CommandPlacements](../extensibility/commandplacements-element.md) .  
  
     Дополнительные сведения о родительских связях и группах команд см. в разделе [группы кнопок для повторного использования создание](../extensibility/creating-reusable-groups-of-buttons.md).  
  
 На этом этапе команда будет отображаться в IDE, но не будет иметь никаких функций. Если команда была создана с помощью шаблона пакета, по умолчанию она будет иметь обработчик щелчка, выводящий сообщение.  
  
## <a name="handling-the-new-command"></a>Обработка новой команды  
 Большинство команд в управляемом коде может обрабатываться в Managed Package Framework (MPF) с помощью сопоставления команды с объектом <xref:System.ComponentModel.Design.MenuCommand> или <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> и реализации соответствующих обработчиков событий.  
  
 Для кода, использующего интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> непосредственно для обработки команд, вы должны реализовать интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> и его методы. Два наиболее важных метода — <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Получите экземпляр <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> , как показано в следующем примере.  
  
     [!code-csharp[ButtonGroup#21](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_5.cs)]  
  
2.  Создайте объект <xref:System.ComponentModel.Design.CommandID> , имеющий в качестве параметров GUID и ID (идентификатор) команды для обработки, как показано в следующем примере.  
  
     [!code-csharp[ButtonGroup#22](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_6.cs)]  
  
     Шаблон пакета Visual Studio предоставляет две коллекции, `GuidList` и `PkgCmdIDList`, для хранения идентификаторов GUID и идентификаторов ID команд. Для команд, которые были добавлены с помощью шаблона, они заполняются автоматически, но для команд, добавленных вручную, необходимо также добавить запись ID в класс `PkgCmdIdList` .  
  
     Кроме того, вы можете заполнить объект <xref:System.ComponentModel.Design.CommandID> , используя исходное строковое значение GUID и целочисленное значение ID.  
  
3.  Создайте экземпляр объекта <xref:System.ComponentModel.Design.MenuCommand> или <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> , определяющий метод, который обрабатывает команду вместе с <xref:System.ComponentModel.Design.CommandID>, как показано в следующем примере.  
  
     [!code-csharp[ButtonGroup#23](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_7.cs)]  
  
     Для статических команд подходит <xref:System.ComponentModel.Design.MenuCommand> . Для динамического отображения пунктов меню требуются обработчики событий QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> добавляет событие <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> , которое происходит, когда открывается основное меню команды, и некоторые другие свойства, например <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Команды, созданные шаблоном проекта, по умолчанию передаются в объект <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> метода `Initialize()` класса пакета.  
  
4.  Для статических команд подходит <xref:System.ComponentModel.Design.MenuCommand> . Для динамического отображения пунктов меню требуются обработчики событий QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> добавляет событие <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> , которое происходит, когда открывается основное меню команды, и некоторые другие свойства, например <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Команды, созданные шаблоном проекта, по умолчанию передаются в объект <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> метода `Initialize()` класса пакета. Мастер Visual Studio реализует метод `Initialize` с помощью `MenuCommand`. Для динамического отображения пункта меню вы должны изменить это на `OleMenuCommand`, как показано на следующем шаге. Кроме того, чтобы изменить текст пункта меню, необходимо добавить флаг команды TextChanges на кнопку команды меню в VSCT-файле, как показано в приведенном ниже примере.  
  
     <!--FIXME [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]-->  
    ```xaml  
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
  
5.  Передайте новую команду меню в метод <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> интерфейса <xref:System.ComponentModel.Design.IMenuCommandService> . Для команд, создаваемых шаблоном проекта, это выполняется по умолчанию, как показано в следующем примере.  
  
     [!code-csharp[ButtonGroup#24](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_9.cs)]  
  
6.  Реализуйте метод, который обрабатывает команду.  
  
#### <a name="to-implement-querystatus"></a>Реализация QueryStatus  
  
1.  Событие QueryStatus происходит перед отображением команды. Это позволяет установить свойства данной команды в обработчике события до того, как пользователь получит доступ к команде. Этот метод доступен только командам, которые добавлены в качестве объектов <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .  
  
     Добавьте объект `EventHandler` в событие <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> в объекте <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> , создаваемом для обработки команды, как показано в следующем примере (`menuItem` — это экземпляр <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ).  
  
     [!code-csharp[MenuText#14](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_10.cs)]
     [!code-vb[MenuText#14](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_10.vb)]  
  
     Объект `EventHandler` получает имя метода, который вызывается при запросе состояния команды меню.  
  
2.  Реализуйте метод обработчика состояния запроса для команды. Параметр `object` `sender` можно привести к объекту <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> , который используется для задания различных атрибутов команды меню, включая ее текст. В следующей таблице показаны свойства в классе <xref:System.ComponentModel.Design.MenuCommand> (от которого является производным класс <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> MPF), соответствующие флагам <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> .  
  
    |Свойство MenuCommand|Флаг OLECMDF|  
    |--------------------------|------------------|  
    |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|OLECMDF_LATCHED|  
    |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|OLECMDF_INVISIBLE|  
    |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|OLECMDF_ENABLED|  
  
     Чтобы изменить текст команды меню, используйте свойство <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> в объекте <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> , как показано в следующем примере.  
  
     [!code-csharp[MenuText#11](../extensibility/codesnippet/CSharp/menucommands-vs-olemenucommands_11.cs)]
     [!code-vb[MenuText#11](../extensibility/codesnippet/VisualBasic/menucommands-vs-olemenucommands_11.vb)]  
  
 MPF автоматически выполняет обработку в случае неподдерживаемых или неизвестных групп. Пока команда не будет добавлена в <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> с помощью метода <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> , эта команда не поддерживается.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Обработка команд с помощью интерфейса IOleCommandTarget  
 Для кода, использующего интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> напрямую, VSPackage должен реализовать методы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> интерфейса <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Если VSPackage реализует иерархию проекта, вместо этих методов должны быть реализованы методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .  
  
 Оба метода, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> , разработаны для получения в качестве входных данных одного `GUID` набора команд и массива идентификаторов команд. Рекомендуется, чтобы пакеты VSPackage полностью поддерживали эту концепцию нескольких идентификаторов в одном вызове. Однако поскольку VSPackage не вызывается из других пакетов VSPackage, вы можете предположить, что массив команд содержит только один идентификатор команды, так как методы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> выполняются в строго определенном порядке. Дополнительные сведения о маршрутизации см. в разделе [маршрутизация команд в пакетах VSPackage](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Для кода, использующего интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> непосредственно для обработки команд, вы должны реализовать метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> в VSPackage следующим образом для обработки команд.  
  
##### <a name="to-implement-the-querystatus-method"></a>Реализация метода QueryStatus  
  
1.  Получите <xref:Microsoft.VisualStudio.VSConstants.S_OK> для допустимых команд.  
  
2.  Задайте элемент `cmdf` параметра `prgCmds` .  
  
     Значение элемента `cmdf` — это логическое объединение значений из перечисления <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> с помощью логического оператора ИЛИ (`|`).  
  
     Используйте соответствующее перечисление, в зависимости от состояния команды.  
  
    -   Если команда поддерживается:  
  
         `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
    -   Если команда должна быть невидимой в данный момент:  
  
         `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
    -   Если команда включена и отображается для выбора:  
  
         `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
         В случае обработки команд, которые размещаются в меню типа `MenuControllerLatched`, первая команда, помеченная флагом `OLECMDF_LATCHED` , — команда по умолчанию. Она отображается в меню при запуске. Дополнительные сведения о типах меню `MenuController` см. в разделе [Menu Element](../extensibility/menu-element.md).  
  
    -   Если команда включена в текущий момент:  
  
         `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
    -   Если команда является частью контекстного меню и скрыта по умолчанию:  
  
         `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXTMENU`  
  
    -   Если команда использует флаг `TEXTCHANGES` , задайте в элементе `rgwz` параметра `pCmdText` новый текст команды, а в элементе `cwActual` параметра `pCmdText` — размер командной строки.  
  
     В состояниях ошибок метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> должен обрабатывать следующие ошибки.  
  
    -   Если идентификатор GUID неизвестен или не поддерживается, должно возвращаться значение `OLECMDERR_E_UNKNOWNGROUP`.  
  
    -   Если идентификатор GUID известен, но идентификатор ID команды неизвестен или не поддерживается, должно возвращаться значение `OLECMDERR_E_NOTSUPPORTED`.  
  
 Реализация VSPackage метода <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> также должна возвращать конкретные коды ошибок, в зависимости от того, поддерживается ли команда и была ли она обработана успешно.  
  
##### <a name="to-implement-the-exec-method"></a>Реализация метода Exec  
  
-   Если `GUID` команды неизвестен, должно возвращаться значение `OLECMDERR_E_UNKNOWNGROUP`.  
  
-   Если `GUID` известен, но ID команды неизвестен, должно возвращаться значение `OLECMDERR_E_NOTSUPPORTED`.  
  
-   Если `GUID` и ID команды соответствуют паре GUID:ID, которая используется командой в VSCT-файле, выполните код, связанный с командой, и верните значение <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме VSCT XML](../extensibility/vsct-xml-schema-reference.md)   
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)