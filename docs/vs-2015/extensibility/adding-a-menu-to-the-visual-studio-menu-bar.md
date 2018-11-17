---
title: Добавление меню в строке меню Visual Studio | Документация Майкрософт
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
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aaad040724efc2b090db606c5675dce6f7422f5e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806221"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Добавление меню в строку меню Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как добавлять меню в строку меню среды разработки Visual Studio (IDE). Интегрированная среда разработки строка меню содержит меню категории, такие как **файл**, **изменить**, **представление**, **окно**, и **помочь** .  
  
 Перед добавлением нового меню в строке меню Visual Studio, учитывать ли ваши команды должно размещаться в существующее меню. Дополнительные сведения о размещении команды, см. в разделе [меню и команд для Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Меню объявляются в vsct-файле проекта. Дополнительные сведения о меню и vsct-файлы, см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Выполнив это пошаговое руководство, можно создать меню с именем **TestMenu** , содержащий одну команду.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Создание проекта VSIX, содержащего шаблон элемента настраиваемой команды  
  
1.  Создайте проект VSIX с именем `TopLevelMenu`. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, в разделе **Visual C#** / **расширяемости**.  Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  При открытии проекта, Добавление пользовательской команды шаблона элемента с именем **тестовую команду**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите к **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя командного файла для **TestCommand.cs**.  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Создание меню в строке меню интегрированной среды разработки  
  
#### <a name="to-create-a-menu"></a>Создание меню  
  
1.  В **обозревателе решений**, откройте TestCommandPackage.vsct.  
  
     В конце файла, не существует \<символы > узел, который содержит несколько \<GuidSymbol > узлов. В узле с именем guidTestCommandPackageCmdSet добавьте новый символ, следующим образом:  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Создать пустой \<меню > узел в \<команды > узел, непосредственно перед \<группы >. В \<меню > узел, добавьте \<меню >, как показано ниже:  
  
    ```xml  
    <Menus>  
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">  
            <Parent guid="guidSHLMainMenu"  
                    id="IDG_VS_MM_TOOLSADDINS" />  
            <Strings>  
              <ButtonText>TestMenu</ButtonText>  
              <CommandName>TestMenu</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     `guid` И `id` значения меню задают набор команд и меню в набор команд.  
  
     `guid` И `id` значения родительского размещения меню в разделе меню Visual Studio, содержащий меню «Сервис» и «Add-ins.  
  
     Значение `CommandName` строка указывает, что текст должен отображаться в элементе меню.  
  
3.  В \<группы > найдите \<группы > и измените \<родительского > элемент меню, который мы только что добавили:  
  
    ```csharp  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     В результате группа частью нового меню.  
  
4.  Найти `Buttons` раздел. Обратите внимание, что [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] создала шаблон пакета `Button` элемент, имеющий родительского присвоено `MyMenuGroup`. Таким образом эта команда будет отображаться в меню.  
  
## <a name="building-and-testing-the-extension"></a>Построение и тестирование расширения  
  
1.  Выполните сборку решения и запустите отладку. Экземпляр экспериментального экземпляра должна появиться.  
  
2.  В строке меню в экспериментальном экземпляре должен содержать **TestMenu** меню.  
  
3.  На **TestMenu** меню, щелкните **вызвать команду проверки**.  
  
     Появится окно сообщения с отображения сообщения «Тестовую команду пакета внутри TopLevelMenu.TestCommand.MenuItemCallback()». Это означает, что работает новой команды.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)

