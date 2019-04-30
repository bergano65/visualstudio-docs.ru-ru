---
title: Добавление команд Visual Studio на начальную страницу | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 638c9c0f0d024830124445485dcf9991678bd4d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429015"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Добавление команд Visual Studio на начальную страницу
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании настраиваемой начальной страницы, можно добавить в него команды Visual Studio. В этом документе описываются различные способы для привязки команд Visual Studio к объектам XAML на начальной странице.  
  
 Дополнительные сведения о командах в XAML см. в разделе [сведения о системе команд](http://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Добавление команд из команды также  
 Начальная страница создана в [Создание настраиваемая начальная страница](../extensibility/creating-a-custom-start-page.md) добавлены <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> и <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> пространства имен, как показано ниже.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Добавьте другое пространство имен из сборки Microsoft.VisualStudio.Shell.Immutable.11.0.dll Microsoft.VisualStudio.Shell. (Может потребоваться добавить ссылку на эту сборку в проекте.)  
  
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
> `x:` Псевдоним, который ссылается на схемы XAML, является обязательным в начале всех команд.  
  
 Можно задать значение `Command` свойство для любой команды, который может быть организован **команда** окна. Список доступных команд, см. в разделе [псевдонимы команд Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Если добавляемая команда требует дополнительный параметр, можно добавить его к значению `CommandParameter` свойство. Отдельные параметры из команды разделяются пробелами, как показано в следующем примере.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Также вызов расширения из команды  
 Для вызова команды из зарегистрированные объекты VSPackage используется тот же синтаксис, который используется для вызова других команд Visual Studio. Например, если установленный VSPackage добавляет **Домашняя страница** команды **представление** меню, можно вызвать эту команду, задав `CommandParameter` для `View.HomePage`.  
  
> [!NOTE]
> Если вызвать команду, которая связана с помощью VSPackage, необходимо загрузить пакет, при вызове команды.  
  
## <a name="adding-commands-from-assemblies"></a>Добавление команд из сборок  
 Чтобы вызвать команду из сборки, кода или к нему доступ в пакет VSPackage, который не связан с командой меню, необходимо создать псевдоним для сборки и затем вызвать псевдоним.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Для вызова команды из сборки  
  
1. В решении добавьте ссылку на сборку.  
  
2. В верхней части файл StartPage.xaml добавьте директиву пространства имен для сборки, как показано в следующем примере.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. Вызвать команду, задав `Command` свойства объекта XAML, как показано в следующем примере.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> Необходимо скопировать сборку и вставьте его в... \\ *Папка установки visual Studio*\Common7\IDE\PrivateAssemblies\ чтобы убедиться в том, он загружается, прежде чем он вызывается.  
  
## <a name="adding-commands-with-the-dte-object"></a>Добавление команд с помощью объекта DTE  
 Можно получить доступ к объект DTE из начальной страницы, как в разметке, так и в коде.  
  
 В разметке, доступен с помощью [привязка расширения разметки](http://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) синтаксис для вызова <xref:EnvDTE.DTE> объекта. Этот подход можно использовать для привязки к простые свойства, например те, которые возвращают коллекции, но нельзя привязать к методам или служб. В следующем примере показан <xref:System.Windows.Controls.TextBlock> элемент управления, который привязывается к <xref:EnvDTE._DTE.Name%2A> свойство и <xref:System.Windows.Controls.ListBox> элемента управления, который перечисляет <xref:EnvDTE.Window.Caption%2A> свойства коллекции, который возвращается <xref:EnvDTE._DTE.Windows%2A> свойство.  
  
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
  
 Пример см. в разделе [Пошаговое руководство. Сохранение пользовательских параметров на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>См. также  
 [Добавление пользовательского элемента на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md)
