---
title: "Часто задаваемые вопросы: Преобразование надстроек для расширений VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 43376b304637ffe59d443ee82350d5492133db2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Часто задаваемые вопросы. Преобразование надстроек в расширения VSPackage
Надстройки устарели. Чтобы сделать новые расширения Visual Studio, необходимо создать расширение VSIX. Здесь приведены ответы на некоторые часто задаваемые вопросы о преобразовании надстроек Visual Studio для расширения VSIX.  
  
> [!WARNING]
>  Начиная с Visual Studio 2015 для проектов C# и Visual Basic можно использовать проект VSIX и добавить шаблоны элементов для команды меню, окна инструментов и пакеты VSPackage. Дополнительные сведения см. в разделе [новые возможности пакета SDK для Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
>  Во многих случаях можно просто перенести кода добавьте в проект VSIX с элементом проекта VSPackage. Чтобы получить объект автоматизации DTE, следует вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> в методе <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
>   
>  `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
>  Дополнительные сведения см. в разделе [запуск мой код надстройки в VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) ниже.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Какое программное обеспечение необходимо для разработки расширений VSIX  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Где находится документация расширения?  
 Начать с [начинается разработка расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Другие статьи о разработке расширения VSSDK на сайте MSDN приведены ниже том, что один.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Как преобразовать проект надстройки в проект VSIX?  
 Невозможно преобразовать проект надстройки непосредственно в проект VSIX, поскольку механизмами проекты VSIX не совпадают, как и в проектах надстроек. Шаблон проекта VSIX, а также шаблоны элементов проекта вправо с большим числом код, который позволяет сравнительно легко подготовить к и работает как расширение VSIX.  
  
##  <a name="BKMK_StartDeveloping"></a>Как начать разработку расширения VSIX?  
 Ниже приведен порядок выполнения файл VSIX, который содержит команду меню.  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Чтобы сделать расширение VSIX, которое содержит команды меню  
  
1.  Создайте проект VSIX. (**Файл**, **New**, **проекта**, или тип **проекта** в **быстрого запуска** окна). В **новый проект** диалогового окна разверните **Visual C# / расширяемости** или **Visual Basic и расширяемость** и выберите **проект VSIX**.) Назовите проект **TestExtension** и укажите расположение для него.  
  
2.  Добавить **настраиваемой команды** шаблон элемента проекта. (Щелкните правой кнопкой мыши узел проекта в **обозревателе решений** и выберите **добавить / новый элемент**. В **новый проект** диалоговое окно для Visual C# или Visual Basic, выберите **расширяемости** , а затем выберите **настраиваемой команды**.)  
  
3.  Нажмите клавишу F5, чтобы построить проект и запустить его в режиме отладки.  
  
     Откроется второй экземпляр Visual Studio. Он называется экспериментальным экземпляром и может содержать не такие настройки, как экземпляр Visual Studio, используемый для написания кода. При первом запуске экспериментального экземпляра будет выдано предложение зайти в VS Online и определить тему и профиль.  
  
     На **средства** меню (в экспериментальном экземпляре) вы увидите кнопку с именем **Мои команды с именем**. При выборе этой кнопки, появится сообщение: **TestVSPackagePackage.MenuItemCallback() внутри**.  
  
##  <a name="BKMK_RunAddin"></a>Как выполнять код надстройки в VSPackage  
 Код надстройки можно запустить одним из двух способов.  
  
-   Путем запуска команды меню (код находится в методе `IDTCommandTarget.Exec`).  
  
-   Автоматически при запуске (код находится в обработчике событий `OnConnection`).  
  
 То же самое можно сделать в VSPackage. Вот как добавить код надстройки в метод обратного вызова.  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Внедрение команды меню в VSPackage  
  
1.  Создайте VSPackage с командой меню. (Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2.  Откройте файл, содержащий определение VSPackage. (В проекте C# имеет  *\<имя проекта >*Package.cs.)  
  
3.  Добавьте в файл следующие операторы `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Найдите метод `MenuItemCallback`. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект <xref:EnvDTE80.DTE2>:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Добавьте код из метода надстройки `IDTCommandTarget.Exec`. Например, ниже приведен код, который добавляет новую область для **вывода** окна и выводится «Некоторые Text» в новой области.  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        DTE2 dte = (DTE2) GetService(typeof(DTE));  
        OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
        OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
        outputWindowPane.OutputString("Some Text");  
    }  
  
    ```  
  
6.  Постройте и запустите этот проект. Нажмите клавишу F5 или выберите **запустить** на **отладки** инструментов. В экспериментальном экземпляре Visual Studio **средства** меню должны иметь кнопку с именем **Мои команды с именем**. При выборе этой кнопки слова **некоторые текст** должны появиться в **вывода** области окна. (Может потребоваться открыть **вывода** окна.)  
  
 Можно также настроить запуск кода при загрузке. Обычно для расширений VSPackage эту возможность не используют. Если при запуске Visual Studio попытаются загрузиться слишком много расширений, время запуска может заметно увеличиться. Лучше настроить автоматическую загрузку расширения VSPackage при выполнении определенных условий (например, при открытии решения).  
  
 В следующей процедуре показано, как запустить в расширении VSPackage код надстройки, загружающий ее автоматически при открытии решения.  
  
#### <a name="to-autoload-a-vspackage"></a>Настройка автоматической загрузки VSPackage  
  
1.  Создайте проект VSIX с элементом проекта пакета Visual Studio. (Для этого действия см. в разделе [как приступить к разработке расширений VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Просто добавьте **пакета Visual Studio** элемента проекта вместо.) Назовите проект VSIX **TestAutoload**.  
  
2.  Откройте TestAutoloadPackage.cs. Найдите строку, где объявляется класс пакета:  
  
    ```csharp  
    public sealed class <name of your package>Package : Package  
    ```  
  
3.  Над этой строкой есть набор атрибутов. Добавьте следующий атрибут:  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    ```  
  
4.  Установите точку останова в методе `Initialize()` и запустите отладку (F5).  
  
5.  Откройте проект в экспериментальном экземпляре. После этого должен загрузиться проект VSPackage и сработать точка останова.  
  
 Можно определить другие контексты загрузки VSPackage, используя для этого поля <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Дополнительные сведения см. в разделе [загрузке пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Как получить объект DTE?  
 Если надстройка, например, не отображает пользовательский интерфейс, команды меню, кнопки панели инструментов или инструменты Windows, можно использовать код как есть, пока не будет получен объект DTE автоматизации из VSPackage. Это делается так.  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Получение объекта DTE из VSPackage  
  
1.  В проект VSIX с помощью шаблона пакета Visual Studio элемент искать  *\<имя проекта >*Package.cs файл. Это класс, который извлекается из <xref:Microsoft.VisualStudio.Shell.Package> и может помочь при взаимодействии с Visual Studio. В данном случае используйте <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект <xref:EnvDTE80.DTE2>.  
  
2.  Добавьте следующие операторы `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
3.  Найдите метод `Initialize`. Данный метод обрабатывает команду, указанную в Мастере пакетов. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект DTE:  
  
    ```csharp  
    DTE dte = (DTE)GetService(typeof(DTE));  
    ```  
  
 После получения объекта автоматизации <xref:EnvDTE.DTE> можно добавить в проект остальную часть кода надстройки. Если вам нужен объект <xref:EnvDTE80.DTE2>, проделайте то же самое.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Как применить стиль VSPackage к командам меню и кнопкам панели инструментов в надстройке?  
 Расширения VSPackage используют для создания большинства команд меню, панелей инструментов, кнопок панели инструментов и других элементов пользовательского интерфейса файл .VSCT. **Настраиваемой команды** шаблон элемента проекта дает возможность создать команду на **средства** меню. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Дополнительные сведения о vsct-файлами см. в разделе [как пакеты VSPackage добавить элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Пошаговые руководства, в которых показано, как использовать vsct-файл для добавления элементов меню, панелей инструментов и кнопки панели инструментов, в разделе [расширение меню и команд](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Как добавить пользовательские окна инструментов с помощью VSPackage?  
 Окно инструментов пользовательский шаблон элемента дает возможность создать окно инструментов. Дополнительные сведения об этом шаблоне элемента проекта см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md). Сведения об окнах средств см. в разделе [расширение и настройка окна инструментов](../extensibility/extending-and-customizing-tool-windows.md) и статьи в нем, особенно [Добавление окно инструментов](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Как управлять окнами Visual Studio с помощью VSPackage?  
 Если надстройка управляет окнами Visual Studio, то код надстройки также должен работать в VSPackage. Например, эта процедура показано, как добавить код, который управляет **список задач** для `MenuItemCallback` метод пакета VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Вставка кода управления окнами из надстройки в VSPackage  
  
1.  Создать пакет VSPackage, имеющий команды меню, как и в [как приступить к разработке расширений VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) раздела.  
  
2.  Откройте файл, содержащий определение VSPackage. (В проекте C# имеет  *\<имя проекта >*Package.cs.)  
  
3.  Добавьте следующие операторы `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Найдите метод `MenuItemCallback`. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект <xref:EnvDTE80.DTE2>:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Добавьте код из надстройки. Например, ниже приведен код, который добавляет новые задачи для **список задач**, содержит число задач, а затем удаляет одну задачу.  
  
    ```csharp  
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
  
1.  Создать пакет VSPackage, имеющий команды меню, как и в [как приступить к разработке расширений VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) раздела.  
  
2.  Откройте файл, содержащий определение VSPackage. (В проекте C# имеет  *\<имя проекта >*Package.cs.)  
  
3.  Добавьте следующие операторы `using`:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  Найдите метод `MenuItemCallback`. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект <xref:EnvDTE80.DTE2>:  
  
    ```csharp  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    ```  
  
5.  Добавьте код из надстройки. Например, следующий код позволяет получить имя запускаемого проекта в решении. (При запуске этого пакета должно быть открыто многопроектное решение.)  
  
    ```csharp  
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
  
```csharp  
Events2 dteEvents = (Events2)dte.Events;  
dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;   
. . .  
public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)   
{  
    string s = "[Event] Renamed " + oldName + " to " + Path.GetFileName(projItem.get_FileNames(1) + " in project " + projItem.ContainingProject.Name;   
}  
```