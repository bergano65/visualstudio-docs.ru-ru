---
title: Добавление меню в строку меню | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184928"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Добавление меню в строку меню Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как добавить меню в строку меню интегрированной среды разработки Visual Studio (IDE). Строка меню интегрированной среды разработки содержит категории меню, такие как **файл**, **Правка**, **вид**, **окно**и **Справка**.

 Перед добавлением нового меню в строку меню Visual Studio рассмотрите возможность размещения команд в существующем меню. Дополнительные сведения о размещении команд см. в разделе [меню и команды для Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Меню объявляются в файле vsct проекта. Дополнительные сведения о меню и файлах vsct см. в разделе [команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).

 Выполнив это пошаговое руководство, можно создать меню с именем **тестмену** , содержащее одну команду.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Создание проекта VSIX с пользовательским шаблоном элемента команды

1. Создайте проект VSIX с именем `TopLevelMenu` . Шаблон проекта VSIX можно найти в диалоговом окне **Новый проект** в разделе **Visual C#**  /  **расширяемость**Visual C#.  Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. При открытии проекта добавьте пользовательский шаблон элемента команды с именем **тесткомманд**. В **Обозреватель решений**щелкните правой кнопкой мыши узел проекта и выберите **Добавить/новый элемент**. В диалоговом окне **Добавление нового элемента** перейдите в раздел **Visual C#/Extensibility** и выберите пункт **пользовательская команда**. В поле **имя** в нижней части окна измените имя файла команд на **TestCommand.CS**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Создание меню в строке меню интегрированной среды разработки

#### <a name="to-create-a-menu"></a>Создание меню

1. В **Обозреватель решений**откройте тесткоммандпаккаже. vsct.

     В конце файла находится \<Symbols> узел, содержащий несколько \<GuidSymbol> узлов. В узле с именем Гуидтесткоммандпаккажекмдсет добавьте новый символ, как показано ниже.

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2. Создайте пустой \<Menus> узел в \<Commands> узле непосредственно перед \<Groups> . В \<Menus> узле добавьте \<Menu> узел, как показано ниже.

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

     `guid`Значения и в `id` меню указывают набор команд и конкретное меню в наборе команд.

     `guid`Значения и `id` родительского положения меню в разделе строки меню Visual Studio, содержащей меню средства и надстройки.

     Значение `CommandName` строки указывает, что текст должен отображаться в пункте меню.

3. В \<Groups> разделе найдите \<Group> и измените \<Parent> элемент, чтобы он указывал на только что добавленное меню:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     В результате группа становится частью нового меню.

4. Найдите раздел `Buttons`. Обратите внимание, что [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] шаблон пакета создал `Button` элемент, для которого его родительский объект имеет значение `MyMenuGroup` . В результате эта команда появится в меню.

## <a name="building-and-testing-the-extension"></a>Сборка и тестирование расширения

1. Выполните сборку решения и запустите отладку. Должен отобразиться экземпляр экспериментального экземпляра.

2. Строка меню в экспериментальном экземпляре должна содержать меню **тестмену** .

3. В меню **тестмену** выберите команду **вызвать команду Test**.

     Должно появиться окно сообщения с сообщением "пакет Тесткомманд внутри Топлевелмену. Тесткомманд. Менуитемкаллбакк ()". Это означает, что новая команда работает.

## <a name="see-also"></a>См. также:
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
