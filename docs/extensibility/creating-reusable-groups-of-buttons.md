---
title: Создание многоразовых групп кнопок (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739461"
---
# <a name="create-reusable-groups-of-buttons"></a>Создание многоразовых групп кнопок
Командная группа — это набор команд, которые всегда появляются вместе в меню или панели инструментов. Любая командная группа может быть повторно использована, назначив ее в различные родительские меню в разделе CommandPlacements файла *.vsct.*

 Группы командования обычно содержат кнопки, но они также могут содержать другие меню или комбо-коробки.

## <a name="to-create-a-reusable-group-of-buttons"></a>Создание многоразовой группы кнопок

1. Создайте проект VSIX под названием `ReusableButtons`. Для получения дополнительной информации [см. Создать расширение с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Когда проект откроется, добавьте шаблон пользовательского элемента команд под названием **ReusableCommand.** В **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт**. В диалоге **Добавить новый элемент** перейдите на **Visual C е** > **Extensibility** и выберите **пользовательские команды.** В поле **«Имя»** в нижней части окна измените имя файла команды на *ReusableCommand.cs.*

3. В файле *vsct* перейдите в раздел Символы и найдите элемент GuidSymbol, содержащий группы и команды для проекта. Он должен быть назван guidReusableCommandPackageCmdSet.

4. Добавьте IDSymbol для каждой кнопки, которую вы добавите в группу, как в следующем примере.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     По умолчанию шаблон элемента команды создает группу под названием **MyMenuGroup** и кнопку с предоставленным вами названием, а также запись IDSymbol для каждого из них.

5. В разделе Группы создайте элемент группы с теми же атрибутами GUID и ID, что и в разделе Символы. Вы также можете использовать существующую группу или использовать запись, предоставленную шаблоном команды, как в следующем примере. Эта группа отображается в меню **«Инструменты»**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Создание группы кнопок для повторного использования

1. Вы можете поместить команду или меню в группу либо с помощью группы в качестве родителя в определении команды или меню, либо путем ввода команды или меню в группу с помощью раздела CommandPlacements.

     В разделе Кнопки определяют кнопку, которая имеет группу в качестве родительской, или использовать кнопку, которая предоставляется шаблоном пакета, как показано в следующем примере.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Если кнопка должна отображаться в нескольких группах, создайте запись для нее в разделе CommandPlacements, которая должна быть размещена после раздела Команд. Установите атрибуты GUID и ID элемента CommandPlacement в соответствии с кнопками, которые вы хотите разместить, а затем установите GUID и идентификатор элемента «Родитель» на элемент целевой группы, как показано в следующем примере.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Значение поля Приоритета определяет положение команды в новой командной группе. Приоритеты, установленные в элементе CommandPlacement, переопределяют те, которые установлены в определении элемента. Команды с более низкими значениями приоритета отображаются перед командами с более высокими значениями приоритета. Допускается дублирование значений приоритетов, но относительное положение команд, которые имеют одинаковое приоритетное значение, не может быть гарантировано, поскольку порядок, в котором команда **devenv/setup** создает окончательный интерфейс из реестра, может быть непоследовательным.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Положить многоразовую группу кнопок в меню

1. Создайте запись `CommandPlacements` в разделе. Установите GUID и `CommandPlacement` идентификатор элемента на идентификатор элемента для элементов вашей группы и установите родительский GUID и идентификатор для целевого местоположения.

    Раздел Командных Мест должен быть размещен сразу после раздела Команд:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Командная группа может быть включена в более чем одно меню. Родительское меню может быть созданным, то [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] есть предоставленным (как описано в *ShellCmdDef.vsct* или *SharedCmdDef.vsct),* или меню, которое определено в другом VSPackage. Количество родительских слоев не ограничено до тех пор, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] пока родительское меню в конечном итоге подключено к меню ярлыка, которое отображается VSPackage.

    Следующий пример помещает группу на панели инструментов **Solution Explorer** справа от других кнопок.

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
