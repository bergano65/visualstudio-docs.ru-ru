---
title: "Добавление панели инструментов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 38
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
ms.openlocfilehash: e6b9b6a5ce384112464d0f768c35bf7b5c57a589
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-toolbar"></a>Добавление панели инструментов
В этом пошаговом руководстве показано, как добавить панель инструментов в Интегрированной среде разработки Visual Studio.  
  
 Панель инструментов представляет полосу горизонтальной или вертикальной кнопками, привязанных к командам. В зависимости от его реализации панели инструментов в Интегрированной среде разработки можно перемещать, закрепить на любой стороне главного окна интегрированной среды разработки или внесенные оставаться поверх других окон.  
  
 Кроме того, пользователи могут добавлять команды на панель инструментов или удалить их из него с помощью **Настройка** диалоговое окно. Как правило панели инструментов в VSPackages настраиваемые пользователем. IDE обрабатывает все настройки и VSPackage реагирует на команды. VSPackage не нужно знать, где физически расположен команды.  
  
 Дополнительные сведения о меню см. в разделе [команд, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Создание расширения с помощью панели инструментов  
 Создайте проект VSIX с именем `IDEToolbar`. Добавление шаблона элемента команды меню с именем **ToolbarTestCommand**. Сведения о том, как это сделать см. в разделе [создания расширения с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Создание панели инструментов для интегрированной среды разработки  
  
1.  В ToolbarTestCommandPackage.vsct найдите раздел символы. В GuidSymbol элемент с именем guidToolbarTestCommandPackageCmdSet добавьте объявления для панели инструментов и группу инструментов, следующим образом.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  В верхней части раздела команды создайте раздел меню. Добавьте элемент меню в раздел меню для определения панели инструментов.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     Панели инструментов не могут быть вложенными как подменю. Таким образом не нужно назначить родительской группы. Кроме того у вас установить приоритет, поскольку пользователь может перемещать панели инструментов. Как правило исходное размещение панели инструментов определяется программным способом, но последующие изменения пользователем, сохраняются.  
  
3.  В [группы](../extensibility/groups-element.md) разделе после существующей группы записи, определить [группы](../extensibility/group-element.md) элемент команд на панели инструментов.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Создание кнопки на панели инструментов. В разделе кнопок замените этот блок для кнопки панели инструментов. Кнопка блоке должен выглядеть следующим образом:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     По умолчанию Если панель инструментов не сопоставлены команды, он не отображается.  
  
5.  Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен отображаться.  
  
6.  Щелкните правой кнопкой мыши меню Visual Studio, чтобы получить список панелей инструментов. Выберите **инструментов тестирования**.  
  
7.  Теперь вы увидите панели инструментов значок справа от найти в значок файлов. Если щелкнуть значок, вы увидите окно сообщения с сообщением **ToolbarTestCommandPackage. Внутри IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
