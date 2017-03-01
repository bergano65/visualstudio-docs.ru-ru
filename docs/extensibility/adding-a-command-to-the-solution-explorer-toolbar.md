---
title: "Добавление команды на панели инструментов обозревателя решений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c5d6e1e597db52e4ba087cd358f1d2bdbd5f208f
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Добавление команды на панели инструментов обозревателя решений
В этом пошаговом руководстве показано, как добавить кнопку **обозревателе решений** инструментов.  
  
 Любые команды на панели инструментов или меню называется кнопки в Visual Studio. При нажатии кнопки выполняется код в обработчике команды. Как правило связанных команд группируются до одной группы. Меню и панели инструментов являются контейнерами для группы. Приоритет определяет порядок отображения отдельных команд в группе в меню или на панели инструментов. Кнопки можно запретить отображение на панели инструментов или меню, контролируя его видимости. Команды, перечисленные в `<VisibilityConstraints>` раздел файла .vsct появляется только в контексте связанного. Видимость не может применяться к группам.  
  
 Дополнительные сведения о меню, панели инструментов команды и vsct-файлах см. в разделе [команд, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Используйте файлы команда XML-таблицы (.vsct) вместо командные файлы конфигурации (.ctc) таблицу для определения отображения меню и команд в вашей VSPackages. Дополнительные сведения см. в разделе [таблицы команд Visual Studio (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню  
 Создайте проект VSIX с именем `SolutionToolbar`. Добавление шаблона элемента команды меню с именем **ToolbarButton**. Сведения о том, как это сделать см. в разделе [создания расширения с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Добавление кнопки на панели инструментов обозревателя решений  
 В этом разделе пошагового руководства показано, как добавить кнопку **обозревателе решений** инструментов. При нажатии кнопки выполняется код в метод обратного вызова.  
  
1.  В файле ToolbarButtonPackage.vsct go `<Symbols>` раздел. `<GuidSymbol>` Узел содержит группы меню и команды, который был создан с помощью шаблона пакета. Добавление `<IDSymbol>` элемент в этот узел, чтобы объявить группу, который будет содержать команду.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  В `<Groups>` разделе после существующей группы записи, определить новую группу, объявленной на предыдущем шаге.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Значение родительского пары GUID:ID `guidSHLMainMenu` и `IDM_VS_TOOL_PROJWIN` помещает эту группу **обозревателе решений** инструментов и установка значения высокоприоритетных помещает его после других групп, команд.  
  
3.  В `<Buttons>` измените идентификатор родительского сформированного `<Button>` запись, чтобы отразить группы, определенные на предыдущем шаге. Измененный `<Button>` элемент должен выглядеть следующим образом:  
  
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
  
5.  Нажмите кнопку Создать.  
  
     Диалоговое окно с сообщением **ToolbarButtonPackage внутри SolutionToolbar.ToolbarButton.MenuItemCallback()** должны отображаться.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Управление видимостью кнопки  
 В этом разделе пошагового руководства показано, как управлять видимостью кнопки на панели инструментов. Установив один или несколько проектов в контексте `<VisibilityConstraints>` раздел файла SolutionToolbar.vsct ограничить кнопки для отображения, только когда в проект или проекты открыты.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Для отображения кнопки, когда открыты один или несколько проектов  
  
1.  В `<Buttons>` раздел ToolbarButtonPackage.vsct, добавьте к существующему двух флагов команда `<Button>` элемент, между `<Strings>` и `<Icons>` тегов.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     `DefaultInvisible` И `DynamicVisibility` необходимо задать флаги, поэтому в этой записи `<VisibilityConstraints>` раздел вступили в силу.  
  
2.  Создание `<VisibilityConstraints>` раздел, который имеет два `<VisibilityItem>` записей. Поместить новый раздел сразу после закрытия `</Commands>` тег.  
  
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
  
     Каждый элемент видимость представляет условие, в котором отображается указанную кнопку. Чтобы применить несколько условий, необходимо создать несколько записей для той же самой кнопки.  
  
3.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
     **Обозревателе решений** панель инструментов содержит кнопки зачеркивания.  
  
4.  Откройте любое решение, содержащее проект.  
  
     Зачеркнутый кнопка на панели инструментов справа от существующих кнопок.  
  
5.  На **файл** меню, щелкните **закрыть решение**. Кнопки исчезнет с панели инструментов.  
  
 Управляет видимостью кнопки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] до загрузки VSPackage. После загрузки VSPackage видимость кнопки управляется VSPackage.  Дополнительные сведения см. в разделе [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
