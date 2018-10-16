---
title: Добавление команды на панели инструментов обозревателя решений | Документация Майкрософт
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
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 40
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f32cc47b796ea7d32207448e7888c17a1d40a73a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254403"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Добавление команды на панель инструментов обозревателя решений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как добавить кнопку **обозревателе решений** панели инструментов.  
  
 Любую команду на панели инструментов или меню называется кнопки в Visual Studio. При нажатии кнопки выполняется код в обработчик команд. Обычно связанные команды группируются вместе для формирования одной группы. Меню или панели инструментов действуют как контейнеры для групп. Приоритет определяет порядок, в котором отображаются отдельные команды в группе, в меню или на панели инструментов. Кнопки можно запретить отображение на панели инструментов или меню, контролируя его видимость. Команда, которая указана в `<VisibilityConstraints>` раздел файла vsct, появляется только в связанного контекста. Видимость нельзя применять к группам.  
  
 Дополнительные сведения о меню, панели инструментов команды и vsct-файлы, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Используются файлы таблицы команд XML (vsct-) вместо командные файлы конфигурации (.ctc) таблицы для определения того, как меню и команды отображаются в пакетов VSPackage. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню  
 Создайте проект VSIX с именем `SolutionToolbar`. Добавление шаблона элемента команды меню с именем **ToolbarButton**. Сведения о том, как это сделать, см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Добавление кнопки на панели инструментов обозревателя решений  
 В этом разделе пошагового руководства показано, как добавить кнопку **обозревателе решений** панели инструментов. При нажатии кнопки выполняется код в метод обратного вызова.  
  
1.  В файле ToolbarButtonPackage.vsct, перейдите в раздел `<Symbols>` раздел. `<GuidSymbol>` Узел содержит группы меню и команды, который был создан с помощью шаблона пакета. Добавление `<IDSymbol>` элемент в этот узел, чтобы объявить группу, которая будет содержать команду.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  В `<Groups>` разделе после существующую запись группы, определить новую группу, объявленного на предыдущем шаге.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Установив пару GUID: ID в качестве родительского `guidSHLMainMenu` и `IDM_VS_TOOL_PROJWIN` помещает эту группу в **обозревателе решений** панели инструментов, а также задать значение высоким приоритетом помещает его после других группы команд.  
  
3.  В `<Buttons>` измените идентификатор родительского объекта, созданного `<Button>` запись группы, определенные на предыдущем шаге. Измененный `<Button>` элемент должен выглядеть следующим образом:  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
     **Обозревателе решений** панель инструментов должна отображать новые кнопки справа от существующих кнопок. Значок кнопки, зачеркивания.  
  
5.  Нажмите кнопку "Создать".  
  
     Диалоговое окно, которое содержит сообщение **ToolbarButtonPackage внутри SolutionToolbar.ToolbarButton.MenuItemCallback()** должны отображаться.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Управление видимостью кнопки  
 В этом разделе пошагового руководства показано, как управлять видимостью кнопки на панели инструментов. Задавая контекст для одного или нескольких проектов в `<VisibilityConstraints>` раздел файла SolutionToolbar.vsct, ограничить кнопки отображаются, только когда проект или проекты открыты.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Для отображения кнопки, когда один или несколько проектов будут открыты  
  
1.  В `<Buttons>` разделе ToolbarButtonPackage.vsct, добавьте два флага команды для существующего `<Button>` элемент, между `<Strings>` и `<Icons>` теги.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     `DefaultInvisible` И `DynamicVisibility` флаги должны быть заданы так, записей в `<VisibilityConstraints>` разделе вступили в силу.  
  
2.  Создание `<VisibilityConstraints>` раздел, содержащий два `<VisibilityItem>` записей. Поместите новый раздел сразу после закрытия `</Commands>` тега.  
  
    ```xml  
    <VisibilityConstraints>  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasSingleProject" />  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasMultipleProjects" />  
    </VisibilityConstraints>  
    ```  
  
     Каждый элемент видимость представляет условие, в котором отображается указанную кнопку. Чтобы применить несколько условий, необходимо создать несколько записей для одной кнопки.  
  
3.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
     **Обозревателе решений** панель инструментов содержит кнопки зачеркивания.  
  
4.  Откройте любое решение, содержащее проект.  
  
     На панели инструментов справа от существующей кнопки появляется кнопка «зачеркивание».  
  
5.  На **файл** меню, щелкните **закрыть решение**. Кнопки исчезнет с панели инструментов.  
  
 Управляет видимостью кнопки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] до загрузки VSPackage. После загрузки VSPackage, VSPackage управляет видимостью кнопки.  Дополнительные сведения см. в разделе [команды MenuCommand и. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)

