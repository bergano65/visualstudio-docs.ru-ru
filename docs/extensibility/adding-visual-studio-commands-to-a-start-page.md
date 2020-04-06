---
title: Добавление команд Visual Studio на стартовую страницу (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740112"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Добавление команд Visual Studio в стартовую страницу

При создании пользовательской страницы Start Page можно добавить к ней команды Visual Studio. В этом документе рассматриваются различные способы привязки команд Visual Studio к объектам XAML на стартовой странице.

Для получения дополнительной информации о командах в XAML [см.](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Добавление команд хорошо

Стартовая страница, созданная в <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> создании <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> [пользовательской стартовой страницы,](../extensibility/creating-a-custom-start-page.md) добавила и пространства имен следующим образом.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Добавьте еще одно пространство имен для Microsoft.VisualStudio.Shell из сборки *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Возможно, потребуется добавить ссылку на эту сборку в проекте.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Можно использовать `vscom:` псевдоним для привязки команд Visual Studio к элементам <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> управления XAML `vscom:VSCommands.ExecuteCommand`на странице, установив свойство элемента управления. Затем можно установить свойство <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> к имени команды для выполнения, как показано в следующем примере.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> Псевдоним, `x:` относящаяся к схеме XAML, требуется в начале всех команд.

 Значение `Command` свойства можно установить для любой команды, к которым можно получить доступ из окна **команды.** Список доступных команд можно найти [в псевдонимах Visual Studio.](../ide/reference/visual-studio-command-aliases.md)

 Если для добавления команды требуется дополнительный параметр, `CommandParameter` его можно добавить к значению свойства. Отделите параметры от команд с помощью пробелов, как показано в следующем примере.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Расширение вызова из скважины команды
 Команды из зарегистрированных VSPackages можно вызывать с помощью того же синтаксиса, который используется для вызова других команд Visual Studio. Например, если установленный VSPackage добавляет команду **Home Page** в меню **Просмотра,** эту команду можно вызвать, установив `CommandParameter` на кнопку: `View.HomePage`

> [!NOTE]
> Если вы вызываете команду, связанную с VSPackage, пакет должен быть загружен при вызове команды.

## <a name="add-commands-from-assemblies"></a>Добавление команд из сборок
 Чтобы вызвать команду из сборки или получить доступ к коду в VSPackage, не связанном с командой меню, необходимо создать псевдоним для сборки, а затем вызвать псевдоним.

### <a name="to-call-a-command-from-an-assembly"></a>Вызов команды из сборки

1. В своем решении добавьте ссылку на сборку.

2. В верхней части файла *StartPage.xaml* добавьте директиву пространства имен для сборки, как показано в следующем примере.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Вызвать команду, установив `Command` свойство объекта XAML, как показано в следующем примере.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Вы должны скопировать сборку, а затем вставить его в К. \\Папка установки Visual Studio (Общие7-IDE)PrivateAssemblies,\* чтобы убедиться, что она загружена до того, как она называется.

## <a name="add-commands-with-the-dte-object"></a>Добавление команд с объектом DTE
 Вы можете получить доступ к объекту DTE со стартовой страницы, как в разметке, так и в коде.

 В разметке <xref:EnvDTE.DTE> можно получить к нему доступ с помощью синтаксиса [расширения связывания для](/dotnet/framework/wpf/advanced/binding-markup-extension) вызова объекта. Этот подход можно использовать для привязки к простым свойствам, таким как те, которые возвращают коллекции, но нельзя связывать сястыть с методами или службами. В следующем примере показан <xref:System.Windows.Controls.TextBlock> элемент <xref:EnvDTE._DTE.Name%2A> управления, который <xref:System.Windows.Controls.ListBox> связывается с свойством, и элемент управления, который перечисляет <xref:EnvDTE.Window.Caption%2A> свойства коллекции, возвращенной <xref:EnvDTE._DTE.Windows%2A> свойством.

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 Например, [см. Walkthrough: Сохранение настроек пользователя на стартовой странице.](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)

## <a name="see-also"></a>См. также

- [Добавление элемента управления пользователем в страницу «Старт»](../extensibility/adding-user-control-to-the-start-page.md)
