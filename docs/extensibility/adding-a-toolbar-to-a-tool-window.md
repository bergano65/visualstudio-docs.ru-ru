---
title: "Добавление панели инструментов в окне инструментов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 48
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
ms.openlocfilehash: 80f8d2e3d689b05680c5d43a0d4b26f17d9a88ce
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Добавление панели инструментов в окне инструментов
В этом пошаговом руководстве показано, как добавить панель инструментов в окне инструментов.  
  
 Панель инструментов представляет содержит кнопки, привязанный к командам полосу горизонтальной или вертикальной. Длина панели инструментов в окне инструментов всегда является таким же, как ширина или высота окна инструмента в зависимости от того, место закрепления панели инструментов.  
  
 В отличие от панели инструментов в Интегрированной среде разработки панели инструментов в окне инструментов должны закрепляться и нельзя перемещать и настроить. В коде umanaged запись VSPackage, панели инструментов можно закрепить на любую границу.  
  
 Дополнительные сведения о том, как добавить панель инструментов см. в разделе [Добавление панели инструментов](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Создание панели инструментов для окна инструментов  
  
1.  Создайте проект VSIX с именем `TWToolbar` с обе команды меню с именем **TWTestCommand** и окно инструментов с именем **TestToolWindow**. Дополнительные сведения см. в разделе [создания расширения с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md) и [создания расширения с окном инструмента](../extensibility/creating-an-extension-with-a-tool-window.md). Необходимо добавить шаблон элемента команды перед добавлением шаблон окна инструмента.  
  
2.  В TWTestCommandPackage.vsct найдите раздел символы. В узле GuidSymbol с именем guidTWTestCommandPackageCmdSet объявите панель инструментов и группу инструментов, следующим образом.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  В верхней части `Commands` создайте `Menus` раздел. Добавление `Menu` для определения панели инструментов.  
  
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
  
     Панели инструментов не могут быть вложенными как подменю. Таким образом не нужно назначить родительского. Кроме того у вас установить приоритет, поскольку пользователь может перемещать панели инструментов. Как правило исходное размещение панели инструментов определяется программным способом, но последующие изменения пользователем, сохраняются.  
  
4.  В разделе группы определяют группу для хранения команд на панели инструментов.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  В разделе кнопки сменить родительскую существующего элемента Button группу инструментов, чтобы панель инструментов отображается.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     По умолчанию Если панель инструментов не сопоставлены команды, он не отображается.  
  
     Так как новая панель инструментов не добавляется автоматически в окно инструментов, панели инструментов должны быть добавлены явно. Этот метод будет рассмотрен в следующем разделе.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Добавление панели инструментов в окне средства  
  
1.  В TWTestCommandPackageGuids.cs добавьте следующие строки.  
  
    ```c#  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  В TestToolWindow.cs добавьте следующий оператор using.  
  
    ```c#  
    using System.ComponentModel.Design;  
    ```  
  
3.  В конструкторе TestToolWindow добавьте следующую строку.  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Тестирование панели инструментов в окне инструментов  
  
1.  Выполните сборку решения и запустите отладку. Должна появиться экспериментальный экземпляр Visual Studio.  
  
2.  На **представления и другие окна** меню, щелкните **окно инструментов тестирования** для отображения окна средства.  
  
     Вы увидите, что инструментов (она выглядит как значок по умолчанию) в верхней левой части окна средства, под заголовок.  
  
3.  На панели инструментов щелкните значок для отображения сообщения **TWTestCommandPackage внутри TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>См. также  
 [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)
