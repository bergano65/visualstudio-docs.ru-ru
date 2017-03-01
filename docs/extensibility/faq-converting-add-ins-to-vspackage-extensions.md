---
title: "Часто задаваемые вопросы: Преобразование надстроек в расширения VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 22
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
ms.openlocfilehash: dd7451b090cb9f25f85d08341b6d38130a13942b
ms.lasthandoff: 02/22/2017

---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Часто задаваемые вопросы. Преобразование надстроек в расширения VSPackage
Надстройки устарели. Чтобы сделать новые расширения Visual Studio, необходимо создать расширение VSIX. Здесь приведены ответы на часто задаваемые вопросы о преобразовании надстройки Visual Studio для расширения VSIX.  
  
> [!WARNING]
>  Начиная с Visual Studio 2015 для проектов C# и Visual Basic, можно использовать проект VSIX и добавить элемент-шаблоны для команды меню, окна инструментов и пакетов VSPackages. Дополнительные сведения см. в разделе [новые возможности Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  Во многих случаях можно просто передать код надстройки в проект VSIX с элементом проекта VSPackage. Объект DTE автоматизации можно получить, вызвав <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>метод.</xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Дополнительные сведения см. в разделе [запуск мой код надстройки в VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) ниже.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Какое программное обеспечение необходимо для разработки расширений VSIX  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Где находится документация расширения?  
 Начните с [Начиная разрабатывать расширения Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Ниже, являются другие статьи о разработке расширения VSSDK на сайте MSDN.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Как преобразовать проект надстройки в проект VSIX?  
 Невозможно преобразовать проект надстройки непосредственно в проект VSIX, так как механизмы, используемые в проектах VSIX не те же в проектах надстроек. Шаблон проекта VSIX, а также шаблоны элементов проекта правой имеют большой объем кода, которая позволяет сравнительно легко создавать и запускать расширения VSIX.  
  
##  <a name="a-namebkmkstartdevelopinga-how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a>Как начать разработку расширений VSIX?  
 Ниже приведен порядок выполнения VSIX, который содержит команды меню.  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Чтобы подготовить расширение VSIX, есть команда меню  
  
1.  Создайте проект VSIX. (**Файл**, **New**, **проекта**, или тип **проекта** в **быстрого запуска** окна). В **новый проект** диалогового окна разверните **Visual C# и расширяемости** или **Visual Basic и расширяемость** и выберите **проект VSIX**.) Назовите проект **TestExtension** и указать расположение.  
  
2.  Добавить **настраиваемой команды** шаблона элемента проекта. (Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите **добавить-новый элемент**. В **новый проект** диалоговое окно для Visual C# или Visual Basic, выберите **расширения** и выберите команду **настраиваемой команды**.)  
  
3.  Нажмите клавишу F5, чтобы построить проект и запустить его в режиме отладки.  
  
     Откроется второй экземпляр Visual Studio. Он называется экспериментальным экземпляром и может содержать не такие настройки, как экземпляр Visual Studio, используемый для написания кода. При первом запуске экспериментального экземпляра будет выдано предложение зайти в VS Online и определить тему и профиль.  
  
     На **средства** меню (в экспериментальном экземпляре) вы увидите кнопку с именем **мое имя команды**. При нажатии этой кнопки должно появиться сообщение: **внутри TestVSPackagePackage.MenuItemCallback()**.  
  
##  <a name="a-namebkmkrunaddina-how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a>Как запустить код надстройки в VSPackage?  
 Код надстройки можно запустить одним из двух способов.  
  
-   Путем запуска команды меню (код находится в методе `IDTCommandTarget.Exec`).  
  
-   Автоматически при запуске (код находится в обработчике событий `OnConnection`).  
  
 То же самое можно сделать в VSPackage. Вот как добавить код надстройки в метод обратного вызова.  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Внедрение команды меню в VSPackage  
  
1.  Создайте VSPackage с командой меню. (Дополнительные сведения см. в разделе [создания расширения с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2.  Откройте файл, содержащий определение VSPackage. (В проекте C# имеет * \<имя проекта настроек*Package.cs.)  
  
3.  Добавьте в файл следующие операторы `using`:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Найдите метод `MenuItemCallback`. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>для получения <xref:EnvDTE80.DTE2>объект:</xref:EnvDTE80.DTE2> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Добавьте код из метода надстройки `IDTCommandTarget.Exec`. Например, ниже приведен код, который добавляет новую область в **вывода** окна и печатает «Какой-то текст» в этой области.  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));  
        OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
        OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
        outputWindowPane.OutputString("Some Text");  
    }  
  
    ```  
  
6.  Постройте и запустите этот проект. Нажмите клавишу F5 или выберите **запустить** на **отладки** инструментов. В экспериментальном экземпляре Visual Studio **средства** меню должна появиться кнопка с именем **мое имя команды**. При нажатии этой кнопки, слова **какой-то текст** должны появиться в **вывода** область окна. (Может потребоваться открыть **вывода** окна.)  
  
 Можно также настроить запуск кода при загрузке. Обычно для расширений VSPackage эту возможность не используют. Если при запуске Visual Studio попытаются загрузиться слишком много расширений, время запуска может заметно увеличиться. Лучше настроить автоматическую загрузку расширения VSPackage при выполнении определенных условий (например, при открытии решения).  
  
 В следующей процедуре показано, как запустить в расширении VSPackage код надстройки, загружающий ее автоматически при открытии решения.  
  
#### <a name="to-autoload-a-vspackage"></a>Настройка автоматической загрузки VSPackage  
  
1.  Создайте проект VSIX с элементом проекта пакета Visual Studio. (Для этого действия см. в разделе [как начать разработку расширений VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Просто добавьте **пакет Visual Studio** элемента проекта вместо.) Назовите проект VSIX **TestAutoload**.  
  
2.  Откройте TestAutoloadPackage.cs. Найдите строку, где объявляется класс пакета:  
  
    ```c#  
    public sealed class <name of your package>Package : Package  
    ```  
  
3.  Над этой строкой есть набор атрибутов. Добавьте следующий атрибут:  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    ```  
  
4.  Установите точку останова в методе `Initialize()` и запустите отладку (F5).  
  
5.  Откройте проект в экспериментальном экземпляре. После этого должен загрузиться проект VSPackage и сработать точка останова.  
  
 Можно указать другие контексты загрузки VSPackage, используя поля <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>.</xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Дополнительные сведения см. в разделе [загрузки пакетов VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Как получить объект DTE?  
 Если надстройка, например, не отображает пользовательский интерфейс, команды меню, кнопки панели инструментов или инструменты Windows, можно использовать код как есть, пока не будет получен объект DTE автоматизации из VSPackage. Это делается так.  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Получение объекта DTE из VSPackage  
  
1.  В проекте VSIX с шаблоном элемента пакета Visual Studio найдите * \<имя проекта настроек*файл Package.cs. Это класс, производный от <xref:Microsoft.VisualStudio.Shell.Package>; он может помочь при взаимодействии с Visual Studio.</xref:Microsoft.VisualStudio.Shell.Package> В этом случае используйте его <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>для получения <xref:EnvDTE80.DTE2>объекта.</xref:EnvDTE80.DTE2> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
2.  Добавьте следующие операторы `using`:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
3.  Найдите метод `Initialize`. Данный метод обрабатывает команду, указанную в Мастере пакетов. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>получить объект DTE:</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
    ```c#  
    DTE dte = (DTE)GetService(typeof(DTE));  
    ```  
  
 После того как <xref:EnvDTE.DTE>объекта автоматизации, остальная часть кода надстройки можно добавить в проект.</xref:EnvDTE.DTE> Если вам требуется <xref:EnvDTE80.DTE2>объекта, то же самое можно сделать.</xref:EnvDTE80.DTE2>  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Как применить стиль VSPackage к командам меню и кнопкам панели инструментов в надстройке?  
 Расширения VSPackage используют для создания большинства команд меню, панелей инструментов, кнопок панели инструментов и других элементов пользовательского интерфейса файл .VSCT. **Настраиваемой команды** шаблон проекта дает возможность создать команду на **средства** меню. Дополнительные сведения см. в разделе [создания расширения с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Дополнительные сведения о vsct-файлах см. в разделе [как VSPackages добавить элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Пошаговые руководства, демонстрирующие способы использования файла .vsct для добавления элементов меню, панелей инструментов и кнопок панели инструментов, в разделе [расширение меню и команд](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Как добавить пользовательские окна инструментов с помощью VSPackage?  
 Шаблон элемента проекта пользовательского окна инструментов дает возможность создать окно инструментов. Дополнительные сведения об этом шаблоне элемента проекта см. в разделе [создания расширения с окном инструмента](../extensibility/creating-an-extension-with-a-tool-window.md). Сведения об окнах средств просмотра [расширение и настройка окна инструментов](../extensibility/extending-and-customizing-tool-windows.md) и статьи, особенно [Добавление окно инструментов](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Как управлять окнами Visual Studio с помощью VSPackage?  
 Если надстройка управляет окнами Visual Studio, то код надстройки также должен работать в VSPackage. Например, эта процедура показано, как добавить код, который управляет **список задач** в `MenuItemCallback` методе VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Вставка кода управления окнами из надстройки в VSPackage  
  
1.  Создайте VSPackage с командой меню, как и в [как начать разработку расширений VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) раздел.  
  
2.  Откройте файл, содержащий определение VSPackage. (В проекте C# имеет * \<имя проекта настроек*Package.cs.)  
  
3.  Добавьте следующие операторы `using`:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Найдите метод `MenuItemCallback`. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>для получения <xref:EnvDTE80.DTE2>объект:</xref:EnvDTE80.DTE2> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Добавьте код из надстройки. Например, ниже приведен код, который добавляет новые задачи **список задач**, перечисляет количество задач, а затем удаляет одну задачу.  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)   
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        TaskList tl = (TaskList)dte.ToolWindows.TaskList;   
        askItem tlItem;   
  
        // Add a couple of tasks to the Task List.   
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 1.",    
            vsTaskPriority.vsTaskPriorityHigh, vsTaskIcon.vsTaskIconUser,   
            true, "", 10, true, true);  
        tlItem = tl.TaskItems.Add(" ", " ", "Test task 2.",   
            vsTaskPriority.vsTaskPriorityLow, vsTaskIcon.vsTaskIconComment, true, "", 20, true,true);  
  
        // List the total number of task list items after adding the new task items.  
        System.Windows.Forms.MessageBox.Show("Task Item 1 description: "+tl.TaskItems.Item(2).Description);  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
  
        // Remove the second task item. The items list in reverse numeric order.   
        System.Windows.Forms.MessageBox.Show("Deleting the second task item");  
        tl.TaskItems.Item(2).Delete();  
        System.Windows.Forms.MessageBox.Show("Total number of task items: "+tl.TaskItems.Count);   
    }  
    ```  
  
## <a name="how-do-i-manage-projects-and-solutions-in-a-vspackage"></a>Как управлять проектами и решениями в VSPackage?  
 Если надстройка управляет проектами и решениями, то код надстройки также должен работать в VSPackage. Например, в следующей процедуре показано, как добавить код для получения запускаемого проекта.  
  
1.  Создайте VSPackage с командой меню, как и в [как начать разработку расширений VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) раздел.  
  
2.  Откройте файл, содержащий определение VSPackage. (В проекте C# имеет * \<имя проекта настроек*Package.cs.)  
  
3.  Добавьте следующие операторы `using`:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Найдите метод `MenuItemCallback`. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>для получения <xref:EnvDTE80.DTE2>объект:</xref:EnvDTE80.DTE2> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
    ```c#  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Добавьте код из надстройки. Например, следующий код позволяет получить имя запускаемого проекта в решении. (При запуске этого пакета должно быть открыто многопроектное решение.)  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));   
  
        SolutionBuild2 sb = (SolutionBuild2)dte.Solution.SolutionBuild;   
        Project startupProj;   
        string msg = "";  
  
        foreach (String item in (Array)sb.StartupProjects)   
        {  
            msg += item;   
        }  
        System.Windows.Forms.MessageBox.Show("Solution startup Project: "+msg);   
        startupProj = dte.Solution.Item(msg);   
        System.Windows.Forms.MessageBox.Show("Full name of solution's startup project: "+"/n"+startupProj.FullName);   
    }  
    ```  
  
## <a name="how-do-i-set-keyboard-shortcuts-in-a-vspackage"></a>Как настроить сочетания клавиш в VSPackage?  
 Используйте элемент `<KeyBindings>` файла .VSCT. В следующем примере для команды `idCommand1` задается сочетание клавиш Alt + A, а для команды `idCommand2` — Alt + Ctrl + A. Обратите внимание на синтаксис ключевых имен.  
  
```xml  
<KeyBindings>  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand1" editor="guidVSStd97" key1="A" mod1="ALT" />  
    <KeyBinding guid="MyProjectCmdSet" id="idCommand2" editor="guidVSStd97" key1="A" mod1="CONTROL" mod2="ALT" />  
</KeyBindings>  
```  
  
## <a name="how-do-i-handle-automation-events-in-a-vspackage"></a>Как обрабатывать события автоматизации в VSPackage?  
 События обрабатываются в VSPackage точно так же, как и в надстройке. В следующем примере кода демонстрируется обработка события `OnItemRenamed`. (В данном примере предполагается, что у вас уже есть объект DTE.)  
  
```c#  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```
