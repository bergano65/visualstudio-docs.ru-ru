---
title: "Добавление команд Visual Studio на начальной странице | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 20
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c75d9b41d0e51d6db2e78d0afa0e1ddf37e87b8a
ms.lasthandoff: 02/22/2017

---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Добавление команд Visual Studio на начальной странице
При создании настраиваемой начальной страницы, можно добавить в него команды Visual Studio. В этом документе обсуждаются различные способы для привязки к объектам XAML на начальной странице команды Visual Studio.  
  
 Дополнительные сведения о командах в XAML см. в разделе [Общие сведения о командах](http://msdn.microsoft.com/Library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Добавление команд с помощью команды также  
 Созданные начальной страницы в [Создание начальной страницы пользовательских](../extensibility/creating-a-custom-start-page.md) добавлены <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>и <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>пространства имен, как показано ниже.</xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> </xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Добавьте другое пространство имен для Microsoft.VisualStudio.Shell из Microsoft.VisualStudio.Shell.Immutable.11.0.dll сборки. (Может потребоваться добавить ссылку на эту сборку в проекте.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Можно использовать `vscom:` псевдоним для привязки команд Visual Studio в XAML элементы управления на странице, задав <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>свойство элемента управления, `vscom:VSCommands.ExecuteCommand`.</xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Затем можно задать <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>Свойства имя команды для выполнения, как показано в следующем примере.</xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` Псевдоним, который ссылается на схемы XAML, является обязательным в начале всех команд.  
  
 Можно задать значение `Command` свойство для любой команды, может осуществляться из **команда** окна. Список доступных команд см. в разделе [псевдонимы команд Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Если добавляемая команда требует дополнительный параметр, можно добавить его к значению `CommandParameter` свойство. Отдельные параметры команд пробелами, как показано в следующем примере.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Также вызов расширения с помощью команды  
 Команды можно вызвать из зарегистрированных пакеты VSPackage, используя тот же синтаксис, который используется для вызова других команд Visual Studio. Например, если установленный VSPackage добавляет **Домашняя страница** команды **представление** меню, можно вызвать эту команду, задав `CommandParameter` в `View.HomePage`.  
  
> [!NOTE]
>  Если вызвать команду, которая связана с VSPackage, необходимо загрузить пакет, при вызове команды.  
  
## <a name="adding-commands-from-assemblies"></a>Добавление команд из сборок  
 Чтобы вызвать команду из сборки или доступа к коду в VSPackage, который не связан с командой меню, необходимо создать псевдоним для сборки, а затем вызовите псевдоним.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Для вызова команды из сборки  
  
1.  В решении добавьте ссылку на сборку.  
  
2.  В верхней части файла StartPage.xaml добавьте директиву пространства имен для сборки, как показано в следующем примере.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Вызвать команду, задав `Command` свойство XAML объекта, как показано в следующем примере.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Необходимо скопировать сборку и вставьте его в... \\ *Папка установки visual Studio*\Common7\IDE\PrivateAssemblies\ чтобы убедиться, что он загружается перед его вызовом.  
  
## <a name="adding-commands-with-the-dte-object"></a>Добавление команд с помощью объекта DTE  
 Объект DTE доступны на начальную страницу, разметки и кода.  
  
 В разметке, доступен с помощью [расширения разметки привязки](http://msdn.microsoft.com/Library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) синтаксис для вызова <xref:EnvDTE.DTE>объекта.</xref:EnvDTE.DTE> Этот подход можно использовать для привязки к простые свойства, например те, которые возвращают коллекции, но не удается выполнить привязку к методам или служб. В следующем примере показан <xref:System.Windows.Controls.TextBlock>элемент управления, который привязывает к <xref:EnvDTE._DTE.Name%2A>свойство и <xref:System.Windows.Controls.ListBox>элемента управления, который перечисляет <xref:EnvDTE.Window.Caption%2A>Свойства коллекции, возвращенного <xref:EnvDTE._DTE.Windows%2A>свойство.</xref:EnvDTE._DTE.Windows%2A> </xref:EnvDTE.Window.Caption%2A> </xref:System.Windows.Controls.ListBox> </xref:EnvDTE._DTE.Name%2A> </xref:System.Windows.Controls.TextBlock>  
  
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
  
 Пример см. в разделе [Пошаговое руководство: сохранение параметров пользователя на начальной страницы](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>См. также  
 [Добавление пользовательского элемента управления к домашней странице](../extensibility/adding-user-control-to-the-start-page.md)
