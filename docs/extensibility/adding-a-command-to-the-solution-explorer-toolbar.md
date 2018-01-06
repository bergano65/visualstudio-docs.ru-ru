---
title: "Добавление команды в панели инструментов обозревателя решений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: "39"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 85d38f2347009d75c5e06365c757d2d51339bf06
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Добавление команды в панели инструментов обозревателя решений
В этом пошаговом руководстве показано, как добавить кнопку, чтобы **обозревателе решений** инструментов.  
  
 Любые команды на панели инструментов или меню называется кнопки в Visual Studio. При нажатии этой кнопки выполняется код в обработчике команды. Обычно связанные команды группируются вместе для формирования одной группы. Меню или панели инструментов действуют как контейнеры для групп. Приоритет определяет порядок отображения отдельных команд в группе, в меню или на панели инструментов. Кнопки можно запретить отображение на панели инструментов или меню, контролируя его видимость. Команды, перечисленные в `<VisibilityConstraints>` раздел файла vsct, появляется только в контексте связанного. Видимость не может применяться к группам.  
  
 Дополнительные сведения о меню, команд панели инструментов и vsct-файлами см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Используйте файлы таблицы команд XML (.vsct) вместо файлов конфигурации (.ctc) команда таблицы можно определить внешний вид меню и команд в пакетов VSPackage. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Создание расширения с помощью команды меню  
 Создайте проект VSIX с именем `SolutionToolbar`. Добавить шаблон элемента команды меню с именем **ToolbarButton**. Сведения о том, как это сделать в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Добавление кнопки в панели инструментов обозревателя решений  
 В этом разделе пошагового руководства показано, как добавить кнопку, чтобы **обозревателе решений** инструментов. При нажатии этой кнопки выполняется код в метод обратного вызова.  
  
1.  В файле ToolbarButtonPackage.vsct перейдите к `<Symbols>` раздела. `<GuidSymbol>` Узел содержит группу меню и команды, который был создан с помощью шаблона пакета. Добавить `<IDSymbol>` элемент для этого узла, чтобы объявить группы, который будет содержать команду.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  В `<Groups>` разделе после существующей группы записи, определить новую группу, объявленного в предыдущем шаге.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Установив пару GUID: ID в качестве родительского `guidSHLMainMenu` и `IDM_VS_TOOL_PROJWIN` помещает эту группу на **обозревателе решений** инструментов, а значение высокоприоритетных помещает его после другие группы команд.  
  
3.  В `<Buttons>` измените идентификатор родительского объекта, созданного `<Button>` запись группы, определенные в предыдущем шаге. Измененный `<Button>` элемент должен выглядеть следующим образом:  
  
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
  
     **Обозревателе решений** панель инструментов должна отображать кнопки команды новый справа от существующих кнопок. Значок кнопки, зачеркивания.  
  
5.  Нажмите кнопку Создать.  
  
     Диалоговое окно с сообщением **ToolbarButtonPackage внутри SolutionToolbar.ToolbarButton.MenuItemCallback()** должны отображаться.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Управление видимостью кнопки  
 В этом разделе пошагового руководства показано, как управлять видимостью кнопки на панели инструментов. Установив один или несколько проектов в контекст `<VisibilityConstraints>` раздел файла SolutionToolbar.vsct ограничить кнопка отображается, только когда проект или проекты открыты.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Для отображения кнопки, если один или несколько проектов открыты  
  
1.  В `<Buttons>` раздел ToolbarButtonPackage.vsct, добавьте два флага команды для существующего `<Button>` элемент между `<Strings>` и `<Icons>` тегов.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     `DefaultInvisible` И `DynamicVisibility` флаги должны быть установлены, что записи в `<VisibilityConstraints>` разделе вступили в силу.  
  
2.  Создание `<VisibilityConstraints>` раздел, который имеет два `<VisibilityItem>` записей. Поместите новый раздел сразу после закрывающей `</Commands>` тег.  
  
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
  
     **Обозревателе решений** инструментов не содержит «зачеркнутый».  
  
4.  Откройте любого решения, содержащего проект.  
  
     Зачеркнутый кнопка на панели инструментов справа от существующих кнопок.  
  
5.  На **файл** меню, нажмите кнопку **закрыть решение**. На панели инструментов кнопка будет скрыта.  
  
 Видимость кнопки управляется [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] до окончания загрузки VSPackage. После загрузки VSPackage видимость кнопки управляется VSPackage.  Дополнительные сведения см. в разделе [команды MenuCommand и. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)