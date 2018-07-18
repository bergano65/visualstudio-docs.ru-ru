---
title: Добавление меню в строке меню Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a391da85c38176d79a1c77ce8836ce510e8d27e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103088"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Добавление меню в строке меню Visual Studio
В этом пошаговом руководстве показано, как добавить меню в строке меню среды разработки Visual Studio (IDE). Интегрированная среда разработки строка меню содержит меню категории, такие как **файл**, **изменить**, **представление**, **окна**, и **справки** .  
  
 Перед добавлением нового меню в строке меню Visual Studio, учитывать ли команды должно быть помещено в существующее меню. Дополнительные сведения о размещении команды см. в разделе [меню и команд для Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Меню объявляются в vsct-файле проекта. Дополнительные сведения о меню и vsct-файлами см. в разделе [команд, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Выполняя данное пошаговое руководство, можно создать меню с именем **TestMenu** , содержащую одну команду.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Создание проект VSIX, который содержит шаблон элемента настраиваемой команды  
  
1.  Создайте проект VSIX с именем `TopLevelMenu`. Шаблон проекта VSIX в можно найти **новый проект** диалогового окна в разделе **Visual C#** / **расширяемости**.  Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  При открытии проекта, Добавление пользовательской команды элемента шаблона с именем **TestCommand**. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите на **Visual C# / Extensibility** и выберите **настраиваемой команды**. В **имя** в нижней части окна, измените имя файла команд для **TestCommand.cs**.  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Создание меню в строке меню интегрированной среды разработки  
  
#### <a name="to-create-a-menu"></a>Чтобы создать меню  
  
1.  В **обозревателе решений**, откройте TestCommandPackage.vsct.  
  
     В конце файла является \<символы > узел, который содержит несколько \<GuidSymbol > узлов. В узле с именем guidTestCommandPackageCmdSet добавьте новый символ, следующим образом.  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Создать пустой \<меню > узла в \<команды > узел, непосредственно перед \<группы >. В \<меню > узла, добавьте \<меню > узла, как показано ниже:  
  
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
  
     `guid` И `id` значения меню задают набор команд и меню, определенных в набор команд.  
  
     `guid` И `id` значения родительского объекта размещения меню в разделе в меню Visual Studio, содержащий меню «Сервис» и «надстройки.  
  
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
  
4.  Найти `Buttons` раздела. Обратите внимание, что [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создала шаблон пакета `Button` элемент, имеющий родительского равным `MyMenuGroup`. В результате этой команды появится в меню.  
  
## <a name="building-and-testing-the-extension"></a>Построение и тестирование расширения  
  
1.  Выполните сборку решения и запустите отладку. Экземпляр экспериментального экземпляра должно отображаться.  
  
2.  В меню в экспериментальном экземпляре должен содержать **TestMenu** меню.  
  
3.  На **TestMenu** меню, нажмите кнопку **вызвать команду проверки**.  
  
     Окно сообщения должен отображаться, а также отображать сообщение «TestCommand пакета внутри TopLevelMenu.TestCommand.MenuItemCallback()». Это означает, что новая команда работает.  
  
## <a name="see-also"></a>См. также  
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)