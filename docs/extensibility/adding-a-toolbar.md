---
title: "Добавление панели инструментов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da6ea8eac18151f0efbaefb3e9f910b695630669
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-toolbar"></a>Добавление панели инструментов
В этом пошаговом руководстве показано, как добавить панель инструментов в Интегрированной среде разработки Visual Studio.  
  
 Панель инструментов представляет горизонтальная или вертикальная полоса кнопками, которые связаны с командами. В зависимости от его реализации на панель инструментов в Интегрированной среде разработки можно перемещать, закреплены на любой стороне главного окна интегрированной среды разработки или делать оставаться поверх других окон.  
  
 Кроме того, пользователи могут добавлять команды на панель инструментов или удалять их из нее с помощью **Настройка** диалоговое окно. Как правило панелей инструментов в пакеты VSPackage — настраиваемые пользователем. IDE обрабатывает все настройки и VSPackage реагирует на команды. Пакет VSPackage не нужно знать, где физически расположены команды.  
  
 Дополнительные сведения о меню см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Создание расширения с помощью панели инструментов  
 Создайте проект VSIX с именем `IDEToolbar`. Добавить шаблон элемента команды меню с именем **ToolbarTestCommand**. Сведения о том, как это сделать в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Создание панели инструментов для интегрированной среды разработки  
  
1.  В ToolbarTestCommandPackage.vsct найдите раздел символы. В GuidSymbol элемент с именем guidToolbarTestCommandPackageCmdSet добавьте объявления для панели инструментов и панель инструментов группы, следующим образом.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  В верхней части области команд создайте раздел меню. Добавьте элемент меню в разделе меню, чтобы определить панели инструментов.  
  
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
  
     Панели инструментов не могут располагаться как подменю. Таким образом не нужно назначить родительской группы. Кроме того у вас установить приоритет, поскольку пользователь может перемещать панели инструментов. Как правило исходное размещение панели инструментов определяется программным путем, но последующие изменения пользователем, сохраняются.  
  
3.  В [группы](../extensibility/groups-element.md) разделе после существующую запись группы, определить [группы](../extensibility/group-element.md) элемент будет содержать команды панели инструментов.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Создание кнопки на панели инструментов. В разделе кнопки замените этот блок в кнопке панели инструментов. Кнопка блоке должен выглядеть следующим образом:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     По умолчанию если на панели инструментов нет команд, он не отображается.  
  
5.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
6.  Щелкните правой кнопкой мыши меню Visual Studio, чтобы получить список панелей инструментов. Выберите **инструментов тестирования**.  
  
7.  Теперь вы увидите панели инструментов значок поиска в файлах значок справа. Если щелкнуть значок, появится окно сообщения об ошибке **ToolbarTestCommandPackage. Внутри IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)