---
title: Создание повторно используемых групп кнопок | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4d340e13b6335b7dfde835cc21c48f6ded8cff3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885605"
---
# <a name="create-reusable-groups-of-buttons"></a>Создание повторно используемых групп кнопок
Группа команды — это коллекция команд, которые всегда отображаются вместе в меню или панели инструментов. Любую группу команды могут быть использованы повторно, присвоив его другой родительский элемент меню в разделе CommandPlacements *.vsct* файла.  
  
 Группы команд обычно содержат кнопки, но они также могут содержать другие меню или поля со списком.  
  
## <a name="to-create-a-reusable-group-of-buttons"></a>Создание многократно используемых группы кнопок  
  
1.  Создайте проект VSIX с именем `ReusableButtons`. Дополнительные сведения см. в разделе [создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  При открытии проекта, Добавление пользовательской команды шаблона элемента с именем **ReusableCommand**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить** > **новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C#** > **расширяемости** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя командного файла для *ReusableCommand.cs*.  
  
3.  В *.vsct* файл, перейдите в разделе "символы" и найдите элемент GuidSymbol, содержащий группы и команды для проекта. Она должна называться guidReusableCommandPackageCmdSet.  
  
4.  Добавьте IDSymbol для каждой кнопки, который будет добавлен в группу, как показано в следующем примере.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     По умолчанию, шаблон элемента команда создает группу с именем **MyMenuGroup** и кнопку, которая имеет имя, которое вы указали, а также IDSymbol запись для каждого.  
  
5.  В разделе "группы" создайте элемент Group, имеет те же атрибуты GUID и идентификатор, как те, приведенными в разделе "символы". Можно также использовать имеющуюся группу или использовать запись, которая предоставляется шаблон команды, как показано в следующем примере. Эта группа появилась на **средства** меню  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
## <a name="to-create-a-group-of-buttons-for-reuse"></a>Чтобы создать группу кнопок для повторного использования  
  
1.  Можно поместить команду или меню в группе с помощью группы в качестве родительской в определении меню или команды, или путем помещения команды или меню в группе, используя раздел CommandPlacements.  
  
     В разделе кнопки определить кнопку, которая имеет вашей группы в качестве своего родительского элемента, или использовать кнопки, которая предоставляется с помощью шаблона пакета, как показано в следующем примере.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  Если кнопка должна отображаться в несколько групп, в разделе CommandPlacements, который должен быть помещен после раздела команды создает запись для него. Задать атрибуты GUID и идентификатора элемента CommandPlacement должны совпадать с кнопкой, к которой можно разместить и задайте идентификатор GUID и идентификатор своего родительского элемента теми целевой группы, как показано в следующем примере.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Значение поля приоритета определяет положение команды в новой группе команды. Приоритеты набор в CommandPlacement, элемент переопределения, заданные в определении элемента. Команды, имеющие более низкий приоритет, отображаются перед командами, которые имеют более высокие значения приоритета. Одинаковые значения приоритета разрешены, но не может быть гарантирована относительное положение команд, которые имеют одинаковый приоритет, поскольку порядок, в котором **devenv/setup** команда создает окончательный интерфейса из реестра может не соответствовать.  
  
## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Для размещения многократно используемых группу кнопок, меню  
  
1. Создает запись в `CommandPlacements` разделе. Значение GUID и идентификатор `CommandPlacement` элемент те группы и задайте родительскую GUID и идентификатора объекта в целевое расположение.  
  
    В разделе CommandPlacements должны размещаться только после команды раздела:  
  
   ```xml  
   <CommandTable>  
   ...  
     <Commands>... </Commands>  
     <CommandPlacements>... </CommandPlacements>  
   ...   
   </CommandTable>  
   ```  
  
    Группа команд может быть включено на более чем с одним меню. Родительского меню может быть тот, который вы создали, предоставляемую [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (как описано в разделе *ShellCmdDef.vsct* или *SharedCmdDef.vsct*), или один, который определен в другом пакете VSPackage. Количество уровней родительских связей не ограничено до тех пор, пока родительского меню со временем подключен к [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или контекстное меню, которая отображается в VSPackage.  
  
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
