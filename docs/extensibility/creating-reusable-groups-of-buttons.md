---
title: "Создание многократно используемых групп кнопок | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "группы кнопок, создание в пакеты VSPackage"
  - "Пакеты VSPackage, создание группы для повторного использования кнопок"
  - "Создание многократно используемых групп кнопок"
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 44
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 44
---
# Создание многократно используемых групп кнопок
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Команда группа — это коллекция команд, которые всегда появляются вместе в меню или панели инструментов. Все группы команд могут быть использованы, назначив его другому родительскому меню в разделе CommandPlacements файла .vsct.  
  
 Команда группы обычно содержат кнопки, но они также могут содержать другие меню или поля со списком.  
  
### Создание многократно используемых группы кнопок  
  
1.  Создайте проект VSIX с именем `ReusableButtons`. Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  При открытии проекта, Добавление пользовательской команды элемента шаблона с именем **ReusableCommand**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **Добавить или создать элемент**. В **Добавление нового элемента** диалоговое окно, последовательно выберите пункты **Visual C\# и расширяемость** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **ReusableCommand.cs**.  
  
3.  В файл .vsct перейдите к разделу символы и найдите элемент GuidSymbol, содержащий групп и команд для проекта. Он должен иметь имя guidReusableCommandPackageCmdSet.  
  
4.  Добавьте IDSymbol для каждой кнопки, который будет добавлен в группу, как показано в следующем примере.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="ReusableCommandId" value="0x0100" /> <IDSymbol name="SecondReusableCommandId" value="0x0200" /> </GuidSymbol>  
    ```  
  
     По умолчанию шаблон элемента команда создает группу с именем **MyGroup** и кнопку, которая имеет имя, которое вы указали, вместе с IDSymbol запись для каждого.  
  
5.  В разделе «группы» создайте элемент группы, который имеет те же атрибуты GUID и идентификатор те, приведенными в разделе "символы". Также можно использовать существующую группу или использовать запись, которая предоставляется шаблон команды, как показано в следующем примере. Эта группа появилась на **средства** меню  
  
    ```xml  
    <Groups> <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/> </Group> </Groups>  
    ```  
  
### Создание группы кнопок для повторного использования  
  
1.  Команда или меню можно поместить в группу с помощью группы является родительским в определении меню или команды или поместив команды или меню в группе, используя раздел CommandPlacements.  
  
     В разделе кнопки определить кнопку, которая имеет вашей группы в качестве родительского, или используйте кнопку, которая предоставляется с помощью шаблона пакета, как показано в следующем примере.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> <Icon guid="guidImages" id="bmpPic1" /> <Strings> <ButtonText>Invoke ReusableCommand</ButtonText> </Strings> </Button>  
    ```  
  
2.  Если кнопки должны присутствовать в более чем одной группе, создайте для него запись в разделе CommandPlacements, который должен быть помещен после команды раздела. Задать атрибуты GUID и идентификатор элемента CommandPlacement должны совпадать с кнопку, которую требуется разместить и задайте идентификатор GUID и идентификатор родительского элемента тем целевой группы, как показано в следующем примере.  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> </CommandPlacement> </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Значение поля приоритета определяет положение команды в новые группы команд. Задайте приоритеты в CommandPlacement, элемент переопределяют заданные в определении элемента. Перед командами, которые имеют более высокие значения приоритета отображаются команды, имеющие более низкие значения приоритета. Приоритет повторяющиеся значения, разрешены, но относительное положение команд, которые имеют одинаковое значение приоритета не может быть гарантирована, так как порядок, в котором **devenv \/setup** команда создает конечное интерфейса из реестра могут быть не согласованы.  
  
### Для размещения многократно используемых группа кнопок меню  
  
1.  Создать запись в `CommandPlacements` разделе. Значение GUID и идентификатор `CommandPlacement` элемента те группы и задать родительский объект GUID и идентификатор тем в целевое расположение.  
  
     В разделе CommandPlacements должны размещаться только после команды раздела:  
  
    ```xml  
    <CommandTable> ... <Commands>... </Commands> <CommandPlacements>... </CommandPlacements> ... </CommandTable>  
    ```  
  
     Группы команд может быть включен в более чем одном меню. Меню родительского окна может быть тот, который вы создали, поставляемое [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(как описано в разделе ShellCmdDef.vsct или SharedCmdDef.vsct\), или один из определенных в другой VSPackage. Количество уровней родительских связей не ограничено, при условии, что со временем родительского меню подключен к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или контекстного меню, отображаемого в VSPackage.  
  
     Следующий пример помещает группе **обозревателе решений** справа от других кнопок панели инструментов.  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/> </CommandPlacement> </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup" priority="0x605"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" /> </CommandPlacement> </CommandPlacements>  
  
    ```