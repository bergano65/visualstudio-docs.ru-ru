---
title: Добавление панели инструментов в окно инструментов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 49
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f35ed0f74f8d3fad711f7c1dd4158072b786eb7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562980"
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Добавление панели инструментов в окно инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Добавление панели инструментов в окно инструментов](https://docs.microsoft.com/visualstudio/extensibility/adding-a-toolbar-to-a-tool-window).  
  
В этом пошаговом руководстве показано, как добавить панель инструментов в окно инструментов.  
  
 Панель инструментов представляет собой горизонтальную или вертикальную полосу, содержащую кнопки, привязанный к командам. Длина в панели инструментов окна инструментов совпадает всегда ширины или высоты окна инструментов, в зависимости от место закрепления панели инструментов.  
  
 В отличие от панели инструментов в интегрированной среде разработки панели инструментов в окне инструментов должно быть закреплено и нельзя переместить или настроить. Если VSPackage прописывается в коде umanaged, панели инструментов можно закрепить с любой стороны.  
  
 Дополнительные сведения о том, как добавить панель инструментов см. в разделе [Добавление панели инструментов](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Создание панели инструментов для окна инструментов  
  
1.  Создайте проект VSIX с именем `TWToolbar` , оба с командой меню с именем **TWTestCommand** и окна инструментов с именем **TestToolWindow**. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md) и [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md). Необходимо добавить шаблон элемента команды перед добавлением шаблон окно инструмента.  
  
2.  В TWTestCommandPackage.vsct найдите в разделе "символы". В GuidSymbol узел с именем guidTWTestCommandPackageCmdSet объявите панель инструментов и группу инструментов, следующим образом.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  В верхней части `Commands` разделе, создайте `Menus` раздел. Добавление `Menu` для определения панели инструментов.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Панели инструментов не могут быть вложенными как подменю. Таким образом у вас нет для назначения родительского. Кроме того у вас нет установить приоритет, поскольку пользователь может перемещать панели инструментов. Как правило исходное размещение панель инструментов определяется программным способом, но последующие изменения пользователем, сохраняются.  
  
4.  В разделе "группы" Определите группы, который будет содержать команды для панели инструментов.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  В разделе кнопки сменить родительскую существующего элемента Button группы панели инструментов, чтобы панель инструментов отображается.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     По умолчанию если нет команд на панели инструментов он не отображается.  
  
     Так как новая панель инструментов не добавляется автоматически к окну инструментов, панели инструментов должны добавляться явным образом. Этот метод будет рассмотрен в следующем разделе.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Добавление панели инструментов окна инструментов  
  
1.  В TWTestCommandPackageGuids.cs добавьте следующие строки.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  В TestToolWindow.cs добавьте следующий оператор using.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  Добавьте следующую строку в конструктор TestToolWindow.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Тестирование на панели инструментов в окне инструментов  
  
1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
2.  На **представления / Other Windows** меню, щелкните **окно инструментов тестирования** для отображения окна инструментов.  
  
     Вы увидите, что панель инструментов, (она выглядит как значок по умолчанию), в верхней левой части окна инструментов сразу же после заголовка.  
  
3.  На панели инструментов щелкните значок для отображения сообщения **TWTestCommandPackage внутри TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>См. также  
 [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)

