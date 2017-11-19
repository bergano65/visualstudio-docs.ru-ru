---
title: "Создание многократно используемых групп кнопок | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: "44"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4be8e84c6040f3b4d57082cd39920aec2196e9f7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-reusable-groups-of-buttons"></a>Создание многократно используемых групп кнопок
Группа команд — это совокупность команды, которые всегда появляются вместе в меню или панели инструментов. Все команды группа может использоваться повторно, назначив его другим родительским элементам меню в разделе CommandPlacements vsct-файле.  
  
 Команда группы обычно содержат кнопки, но они также могут содержать других меню или поля со списком.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Создание многократно используемых группы кнопок  
  
1.  Создайте проект VSIX с именем `ReusableButtons`. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  При открытии проекта, Добавление пользовательской команды элемента шаблона с именем **ReusableCommand**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите на **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **ReusableCommand.cs**.  
  
3.  В vsct-файле перейдите к разделу символы и найдите элемент GuidSymbol, содержащий группы и команды для проекта. Он должен быть назван guidReusableCommandPackageCmdSet.  
  
4.  Добавьте IDSymbol для каждой кнопки, который будет добавлен в группу, как показано в следующем примере.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     По умолчанию шаблон элемента команды создается группа с именем **MyGroup** и кнопки, которая имеет имя, которое вы указали, вместе с IDSymbol запись для каждого.  
  
5.  В разделе "группы" создайте группу элемент, который имеет те же атрибуты GUID и ID, как и в разделе символы. Также можно использовать существующую группу, или использовать операция, предоставляемая шаблон команды, как показано в следующем примере. Эта группа появилась на **средства** меню  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Чтобы создать группу кнопок для повторного использования  
  
1.  Можно поместить команду или меню в группе с помощью группы как родительский в определении меню или команды или поместив команды или меню в группе, используя раздел CommandPlacements.  
  
     В разделе кнопок определите кнопки, которая имеет группе, что и родительский объект, или используйте кнопки, которая предоставляется с помощью шаблона пакета, как показано в следующем примере.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  Если кнопки в несколько групп, создайте для него запись в разделе CommandPlacements, который должен быть помещен после команды секции. Задать атрибуты GUID и ID элемента CommandPlacement должны совпадать с кнопку, которую можно разместить и задайте GUID и ID своего родительского элемента теми целевой группы, как показано в следующем примере.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Значение поля Приоритет определяет положение команды в новую группу команды. Установлены приоритеты в CommandPlacement, элемент переопределяют заданные в определении элемента. Команды, имеющие более низкий приоритет, отображаются перед командами, имеющие высокий приоритет. Одинаковые значения приоритета разрешены, но относительное положение команд, которые имеют одинаковое значение приоритета не может быть гарантирована, поскольку порядок, в котором **devenv/setup** команда создает окончательный интерфейс из реестра могут быть не согласованы.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Чтобы поместить многократно используемых группе кнопок меню  
  
1.  Создать запись в `CommandPlacements` раздела. Значение GUID и идентификатор `CommandPlacement` элемента, отличающиеся от вашей группы и задать родительский объект GUID и ID тем в целевое расположение.  
  
     В разделе CommandPlacements должны размещаться только после команды секции:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Группа команд могут быть включены в несколько меню. Его родительском меню может быть тот, который вы создали, предоставляемую [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (как описано в разделе ShellCmdDef.vsct или SharedCmdDef.vsct), или пакет, который определен в другом пакете VSPackage. Количество уровней родительских связей не ограничено, при условии, что в конечном итоге подключенного родительского меню [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или контекстное меню, которое отображается пакетом VSPackage.  
  
     Следующий пример помещает группе **обозревателе решений** справа от других кнопок панели инструментов.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">  
          <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements>  
      <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"   
          priority="0x605">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />  
      </CommandPlacement>  
    </CommandPlacements>  
  
    ```