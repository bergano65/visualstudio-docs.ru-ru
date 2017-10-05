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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b094a04a9d2e273418edaa7cc4bc2d36f89e9d29
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Добавление панели инструментов в окне инструментов
В этом пошаговом руководстве показано, как добавить панель инструментов в окно инструментов.  
  
 Панель инструментов представляет содержит кнопки, привязанный к командам полосу горизонтальной или вертикальной. Длина панели инструментов в окне инструментов всегда является то же, что ширина или высота окна инструментов в зависимости от того, место закрепления панели инструментов.  
  
 В отличие от панели инструментов в Интегрированной среде разработки панели инструментов в окне инструментов должны закрепляться и нельзя переместить или настроить. Если в коде umanaged написан VSPackage, панели инструментов можно закрепить на любую границу.  
  
 Дополнительные сведения о том, как добавить панель инструментов см. в разделе [Добавление панели инструментов](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Создание панели инструментов для окна инструментов  
  
1.  Создайте проект VSIX с именем `TWToolbar` с обе команды меню с именем **TWTestCommand** и окно инструментов с именем **TestToolWindow**. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md) и [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md). Необходимо добавить шаблон элемента команды перед добавлением шаблон окно инструмента.  
  
2.  В TWTestCommandPackage.vsct найдите раздел символы. В узле GuidSymbol с именем guidTWTestCommandPackageCmdSet объявите панель инструментов и панель инструментов группы, следующим образом.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  В верхней части `Commands` создайте `Menus` раздела. Добавить `Menu` для определения панели инструментов.  
  
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
  
     Панели инструментов не могут располагаться как подменю. Таким образом не нужно назначить родительский элемент. Кроме того у вас установить приоритет, поскольку пользователь может перемещать панели инструментов. Как правило исходное размещение панели инструментов определяется программным путем, но последующие изменения пользователем, сохраняются.  
  
4.  В разделе "группы" определите группу для хранения команд для панели инструментов.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  В разделе кнопки сменить родительскую существующий элемент Button группа панели инструментов, чтобы будет отображаться на панели инструментов.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     По умолчанию если на панели инструментов нет команд, он не отображается.  
  
     Поскольку новая панель инструментов не добавляется автоматически в окна инструментов, панели инструментов должны добавляться явным образом. Этот метод будет рассмотрен в следующем разделе.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Добавление панели инструментов окна инструментов  
  
1.  TWTestCommandPackageGuids.cs добавьте следующие строки.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  Добавьте следующие строки в TestToolWindow.cs с помощью инструкции.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  В конструкторе TestToolWindow добавьте следующую строку.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Тестирование панели инструментов в окне инструментов  
  
1.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр Visual Studio.  
  
2.  На **представления и другие окна** меню, нажмите кнопку **окно инструментов тестирования** для отображения в окне инструментов.  
  
     Вы увидите, что инструментов (он выглядит как значок по умолчанию) в верхней левой части окна инструментов под заголовок.  
  
3.  На панели инструментов щелкните значок для отображения сообщений о **TWTestCommandPackage внутри TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>См. также  
 [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)
