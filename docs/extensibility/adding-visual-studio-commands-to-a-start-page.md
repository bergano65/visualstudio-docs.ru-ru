---
title: "Добавление команд Visual Studio на начальной странице | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: efb332de822bd86cc95c4786dbca3472fd0984cc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Добавление команд Visual Studio на начальную страницу
При создании настраиваемой начальной страницы, можно добавить в него команды Visual Studio. В этом документе рассматриваются различные способы для привязки команд Visual Studio объектов XAML на начальной странице.  
  
 Дополнительные сведения о командах в XAML см. в разделе [Общие сведения о командах](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="adding-commands-from-the-command-well"></a>Добавление команд с помощью команды также  
 Начальная страница создана в [Создание настраиваемая начальная страница](../extensibility/creating-a-custom-start-page.md) добавлены <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> и <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> пространства имен, как показано ниже.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Добавьте другое пространство имен для Microsoft.VisualStudio.Shell из Microsoft.VisualStudio.Shell.Immutable.11.0.dll сборки. (Может потребоваться добавить ссылку на эту сборку в проекте.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Можно использовать `vscom:` псевдоним для привязки команд Visual Studio код XAML определяет на странице, задав <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> свойства элемента управления для `vscom:VSCommands.ExecuteCommand`. Затем можно задать <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> свойства имя команды для выполнения, как показано в следующем примере.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` Псевдоним, который ссылается на схемы XAML, не требуется в начале всех команд.  
  
 Можно задать значение `Command` свойство для любой команды, может осуществляться из **команда** окна. Список доступных команд см. в разделе [псевдонимы команд Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Если добавляемая команда требует дополнительный параметр, можно добавить его к значению `CommandParameter` свойство. Отдельные параметры из команды с помощью пробелов, как показано в следующем примере.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Также вызов расширения из команды  
 Команды можно вызывать из зарегистрированных пакетов VSPackage с помощью того же синтаксиса, который позволяет вызывать другие команды Visual Studio. Например, если установленные VSPackage добавляет **Домашняя страница** команды **представление** меню, можно вызвать эту команду, задав `CommandParameter` для `View.HomePage`.  
  
> [!NOTE]
>  Если вызвать команду, которая связана с VSPackage, необходимо загрузить пакет при вызове данной команды.  
  
## <a name="adding-commands-from-assemblies"></a>Добавление команд из сборок  
 Чтобы вызвать команду из сборки или доступа к коду в пакет VSPackage, который не связан с помощью команды меню, необходимо создать псевдоним для сборки и затем вызвать псевдоним.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Для вызова команды из сборки  
  
1.  В вашем решении добавьте ссылку на сборку.  
  
2.  В верхней части файл StartPage.xaml добавьте директиву пространства имен для сборки, как показано в следующем примере.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Вызвать команду, задав `Command` свойства объекта XAML, как показано в следующем примере.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Необходимо скопировать сборку и вставьте его в... \\ *Папка установки visual Studio*\Common7\IDE\PrivateAssemblies\ чтобы убедиться в том, он загружается перед его вызовом.  
  
## <a name="adding-commands-with-the-dte-object"></a>Добавление команд с помощью объекта DTE  
 Объект DTE доступны из начальной страницы, как в разметке, так и в коде.  
  
 В разметке, доступен с помощью [привязки расширения разметки](/dotnet/framework/wpf/advanced/binding-markup-extension) синтаксис для вызова <xref:EnvDTE.DTE> объекта. Этот подход можно использовать для привязки к простых свойств, например те, которые возвращают коллекции, но не удается выполнить привязку к методам или службы. В следующем примере показан <xref:System.Windows.Controls.TextBlock> элемента управления, который привязывает <xref:EnvDTE._DTE.Name%2A> свойство и <xref:System.Windows.Controls.ListBox> управления, перечисляющий <xref:EnvDTE.Window.Caption%2A> свойства коллекции, который возвращается <xref:EnvDTE._DTE.Windows%2A> свойство.  
  
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
  
 Пример см. в разделе [Пошаговое руководство: сохранение параметров пользователя на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>См. также  
 [Добавление пользовательского элемента на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md)