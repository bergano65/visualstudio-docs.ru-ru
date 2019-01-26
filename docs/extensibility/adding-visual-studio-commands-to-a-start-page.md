---
title: Добавление команд Visual Studio на начальную страницу | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de713065b61df07a791fa81e89425481227676ea
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006715"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Добавление команд Visual Studio для начальной страницы
При создании настраиваемой начальной страницы, можно добавить в него команды Visual Studio. В этом документе описываются различные способы для привязки к объектам XAML на начальной странице команды Visual Studio.  
  
 Дополнительные сведения о командах в XAML см. в разделе [Commanding Обзор](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="add-commands-from-the-command-well"></a>Также добавить команды из команды  
 Начальная страница создана в [Создание настраиваемой начальной страницы](../extensibility/creating-a-custom-start-page.md) добавлены <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> и <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> пространства имен, как показано ниже.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Добавить другое пространство имен из сборки Microsoft.VisualStudio.Shell *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Может потребоваться добавить ссылку на эту сборку в проекте.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Можно использовать `vscom:` псевдоним для привязки команд Visual Studio к XAML элементы управления на странице, задав <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> свойство элемента управления, `vscom:VSCommands.ExecuteCommand`. Затем можно задать <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> имя выполняемой команды, как показано в следующем примере.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` Псевдоним, который ссылается на схемы XAML, является обязательным в начале всех команд.  
  
 Можно задать значение `Command` свойство для любой команды, который может быть организован **команда** окна. Список доступных команд, см. в разделе [псевдонимы команд Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Если добавляемая команда требует дополнительный параметр, можно добавить его к значению `CommandParameter` свойство. Отдельные параметры из команды разделяются пробелами, как показано в следующем примере.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="call-extensions-from-the-command-well"></a>Также вызывать расширения из команды  
 Для вызова команды из зарегистрированные объекты VSPackage используется тот же синтаксис, который используется для вызова других команд Visual Studio. Например, если установленный VSPackage добавляет **Домашняя страница** команды **представление** меню, можно вызвать эту команду, задав `CommandParameter` для `View.HomePage`.  
  
> [!NOTE]
>  Если вызвать команду, которая связана с помощью VSPackage, необходимо загрузить пакет, при вызове команды.  
  
## <a name="add-commands-from-assemblies"></a>Добавить команды из сборок  
 Чтобы вызвать команду из сборки, кода или к нему доступ в пакет VSPackage, который не связан с командой меню, необходимо создать псевдоним для сборки и затем вызвать псевдоним.  
  
### <a name="to-call-a-command-from-an-assembly"></a>Для вызова команды из сборки  
  
1.  В решении добавьте ссылку на сборку.  
  
2.  В верхней части *StartPage.xaml* файл, добавьте директиву пространства имен для сборки, как показано в следующем примере.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Вызвать команду, задав `Command` свойства объекта XAML, как показано в следующем примере.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Необходимо скопировать сборку и вставьте его в *... \\\Common7\IDE\PrivateAssemblies {папка установки visual Studio}\* чтобы убедиться в том, он загружается, прежде чем он вызывается.  
  
## <a name="add-commands-with-the-dte-object"></a>Добавьте команды с объектом DTE  
 Можно получить доступ к объект DTE из начальной страницы, как в разметке, так и в коде.  
  
 В разметке, доступен с помощью [привязка расширения разметки](/dotnet/framework/wpf/advanced/binding-markup-extension) синтаксис для вызова <xref:EnvDTE.DTE> объекта. Этот подход можно использовать для привязки к простые свойства, например те, которые возвращают коллекции, но нельзя привязать к методам или служб. В следующем примере показан <xref:System.Windows.Controls.TextBlock> элемент управления, который привязывается к <xref:EnvDTE._DTE.Name%2A> свойство и <xref:System.Windows.Controls.ListBox> элемента управления, который перечисляет <xref:EnvDTE.Window.Caption%2A> свойства коллекции, который возвращается <xref:EnvDTE._DTE.Windows%2A> свойство.  
  
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
  
 Например, см. в разделе [Пошаговое руководство: Сохранение пользовательских параметров на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>См. также  
 [Добавление пользовательского элемента управления на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md)