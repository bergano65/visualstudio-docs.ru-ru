---
title: 'Часто задаваемые вопросы: преобразование надстроек в расширения VSPackage | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3a01d333-6e31-423f-ae06-5091a4fcb7a9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6ed31f96fc2021d0d9e104692f0440cfb78a5e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843057"
---
# <a name="faq-converting-add-ins-to-vspackage-extensions"></a>Часто задаваемые вопросы. Преобразование надстроек в расширения VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Надстройки устарели. Для создания нового расширения Visual Studio необходимо создать расширение VSIX. Ниже приведены ответы на некоторые часто задаваемые вопросы о преобразовании надстройки Visual Studio в расширение VSIX.  
  
> [!WARNING]
> Начиная с Visual Studio 2015 для проектов C# и Visual Basic можно использовать проект VSIX и добавлять шаблоны элементов для команд меню, окон инструментов и пакетов VSPackage. Дополнительные сведения см. [в разделе новые возможности пакета SDK для Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
> [!IMPORTANT]
> Во многих случаях можно просто передавать код надстройки в проект VSIX с помощью элемента проекта VSPackage. Чтобы получить объект автоматизации DTE, следует вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> в методе <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
>   
> `DTE2 dte = (DTE2)GetService(typeof(DTE));`  
>   
> Дополнительные сведения см. [в разделе как можно выполнить код надстройки в VSPackage?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_RunAddin) ниже.  
  
## <a name="what-software-do-i-need-to-develop-vsix-extensions"></a>Какое программное обеспечение требуется для разработки расширений VSIX?  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Пакет SDK для VS можно установить и позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="wheres-the-extension-documentation"></a>Где находится документация расширения?  
 Начните с [начала разработки расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md). Другие статьи о разработке расширений VSSDK на сайте MSDN приведены ниже.  
  
## <a name="can-i-convert-my-add-in-project-to-a-vsix-project"></a>Можно ли преобразовать проект надстройки в проект VSIX?  
 Проект надстройки нельзя преобразовать непосредственно в проект VSIX, так как механизмы, используемые в проектах VSIX, не совпадают с элементами в проектах надстроек. Шаблон проекта VSIX, а также верные шаблоны элементов проектов содержат много кода, что упрощает работу и запуск в качестве расширения VSIX.  
  
## <a name="how-do-i-start-developing-vsix-extensions"></a><a name="BKMK_StartDeveloping"></a> Разделы справки начать разработку расширений VSIX?  
 Вот как можно создать VSIX с командой меню:  
  
#### <a name="to-make-a-vsix-extension-that-has-a-menu-command"></a>Создание расширения VSIX с командой меню  
  
1. Создайте проект VSIX. (**Файл**, **создать**, **проект**или тип **проект** в окне **Быстрый запуск** ). В диалоговом окне **Новый проект** разверните узел **Visual C#/Extensibility** или **Visual Basic/Extensibility** и выберите **проект VSIX**.) Назовите проект **тестекстенсион** и укажите его расположение.  
  
2. Добавление пользовательского шаблона элемента **командного** проекта. (Щелкните правой кнопкой мыши узел проекта в **Обозреватель решений** и выберите **Добавить/новый элемент**. В диалоговом окне **Новый проект** для Visual C# или Visual Basic выберите узел **расширяемость** и выберите **Настраиваемая команда**.)  
  
3. Нажмите клавишу F5, чтобы построить проект и запустить его в режиме отладки.  
  
     Откроется второй экземпляр Visual Studio. Он называется экспериментальным экземпляром и может содержать не такие настройки, как экземпляр Visual Studio, используемый для написания кода. При первом запуске экспериментального экземпляра будет выдано предложение зайти в VS Online и определить тему и профиль.  
  
     В меню **Сервис** (в экспериментальном экземпляре) появится кнопка с именем **Моя команда**. При нажатии этой кнопки появится сообщение: **внутри тествспаккажепаккаже. менуитемкаллбакк ()**.  
  
## <a name="how-can-i-run-my-add-in-code-in-a-vspackage"></a><a name="BKMK_RunAddin"></a> Как выполнить код надстройки в VSPackage?  
 Код надстройки можно запустить одним из двух способов.  
  
- Путем запуска команды меню (код находится в методе `IDTCommandTarget.Exec`).  
  
- Автоматически при запуске (код находится в обработчике событий `OnConnection`).  
  
  То же самое можно сделать в VSPackage. Вот как добавить код надстройки в метод обратного вызова.  
  
#### <a name="to-implement-a-menu-command-in-a-vspackage"></a>Внедрение команды меню в VSPackage  
  
1. Создайте VSPackage с командой меню. (Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).)  
  
2. Откройте файл, содержащий определение VSPackage. (В проекте C# это <em>\<your project name></em> Package.cs.)  
  
3. Добавьте в него следующие инструкции `using` .  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Найдите метод `MenuItemCallback`. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект <xref:EnvDTE80.DTE2>:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Добавьте код из метода надстройки `IDTCommandTarget.Exec`. Например, ниже приведен код, который добавляет новую панель в окно **вывода** и выводит «некоторый текст» на новой панели.  
  
   ```csharp  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       DTE2 dte = (DTE2) GetService(typeof(DTE));  
       OutputWindow outputWindow = dte.ToolWindows.OutputWindow;  
  
       OutputWindowPane outputWindowPane = outputWindow.OutputWindowPanes.Add("A New Pane");  
       outputWindowPane.OutputString("Some Text");  
   }  
  
   ```  
  
6. Постройте и запустите этот проект. Нажмите клавишу F5 или кнопку **запустить** на панели инструментов **Отладка** . В экспериментальном экземпляре Visual Studio в меню " **Сервис** " должна быть кнопка с именем " **Моя команда**". При нажатии этой кнопки в области окна **вывода** должны появиться слова с **текстом** . (Может потребоваться открыть окно **вывода** .)  
  
   Можно также настроить запуск кода при загрузке. Обычно для расширений VSPackage эту возможность не используют. Если при запуске Visual Studio попытаются загрузиться слишком много расширений, время запуска может заметно увеличиться. Лучше настроить автоматическую загрузку расширения VSPackage при выполнении определенных условий (например, при открытии решения).  
  
   В следующей процедуре показано, как запустить в расширении VSPackage код надстройки, загружающий ее автоматически при открытии решения.  
  
#### <a name="to-autoload-a-vspackage"></a>Настройка автоматической загрузки VSPackage  
  
1. Создание проекта VSIX с помощью элемента проекта пакета Visual Studio. (Действия для этого см. в разделе [разделы справки starting VSIX Extensions?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping). Просто добавьте вместо него элемент проекта **пакета Visual Studio** .) Назовите проект VSIX **тестаутолоад**.  
  
2. Откройте TestAutoloadPackage.cs. Найдите строку, где объявляется класс пакета:  
  
   ```csharp  
   public sealed class <name of your package>Package : Package  
   ```  
  
3. Над этой строкой есть набор атрибутов. Добавьте следующий атрибут:  
  
   ```csharp  
   [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
   ```  
  
4. Установите точку останова в методе `Initialize()` и запустите отладку (F5).  
  
5. Откройте проект в экспериментальном экземпляре. После этого должен загрузиться проект VSPackage и сработать точка останова.  
  
   Можно определить другие контексты загрузки VSPackage, используя для этого поля <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>. Дополнительные сведения см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="how-can-i-get-the-dte-object"></a>Как получить объект DTE?  
 Если надстройка, например, не отображает пользовательский интерфейс, команды меню, кнопки панели инструментов или инструменты Windows, можно использовать код как есть, пока не будет получен объект DTE автоматизации из VSPackage. Это делается так.  
  
#### <a name="to-get-the-dte-object-from-a-vspackage"></a>Получение объекта DTE из VSPackage  
  
1. В проекте VSIX с шаблоном элемента пакета Visual Studio найдите <em>\<project name></em> файл Package.cs. Это класс, который извлекается из <xref:Microsoft.VisualStudio.Shell.Package> и может помочь при взаимодействии с Visual Studio. В данном случае используйте <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект <xref:EnvDTE80.DTE2>.  
  
2. Добавьте следующие операторы `using`:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
3. Найдите метод `Initialize`. Данный метод обрабатывает команду, указанную в Мастере пакетов. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект DTE:  
  
   ```csharp  
   DTE dte = (DTE)GetService(typeof(DTE));  
   ```  
  
   После получения объекта автоматизации <xref:EnvDTE.DTE> можно добавить в проект остальную часть кода надстройки. Если вам нужен объект <xref:EnvDTE80.DTE2>, проделайте то же самое.  
  
## <a name="how-do-i-change-menu-commands-and-toolbar-buttons-in-my-add-in-to-the-vspackage-style"></a>Как применить стиль VSPackage к командам меню и кнопкам панели инструментов в надстройке?  
 Расширения VSPackage используют для создания большинства команд меню, панелей инструментов, кнопок панели инструментов и других элементов пользовательского интерфейса файл .VSCT. Шаблон элемента **пользовательского командного** проекта дает возможность создать команду в меню **Сервис** . Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Дополнительные сведения о vsct файлах см. в статье [Добавление элементов пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md). Пошаговые руководства, демонстрирующие использование файла vsct для добавления пунктов меню, панелей инструментов и кнопок панели инструментов, см. в разделе [Расширение меню и команд](../extensibility/extending-menus-and-commands.md).  
  
## <a name="how-do-i-add-custom-tool-windows-in-the-vspackage-way"></a>Как добавить пользовательские окна инструментов с помощью VSPackage?  
 Шаблон элемента проекта настраиваемого окна инструментов дает возможность создать окно инструментов. Дополнительные сведения об этом шаблоне элемента проекта см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md). Сведения о окнах инструментов см. в разделах [расширение и настройка окон инструментов](../extensibility/extending-and-customizing-tool-windows.md) и статьи в нем, особенно [Добавление окна инструментов](../extensibility/adding-a-tool-window.md).  
  
## <a name="how-do-i-manage-visual-studio-windows-in-the-vspackage-way"></a>Как управлять окнами Visual Studio с помощью VSPackage?  
 Если надстройка управляет окнами Visual Studio, то код надстройки также должен работать в VSPackage. Например, в этой процедуре показано, как добавить код, управляющий **список задач** , в `MenuItemCallback` метод VSPackage.  
  
#### <a name="to-insert-window-management-code-from-an-add-in-into-a-vspackage"></a>Вставка кода управления окнами из надстройки в VSPackage  
  
1. Создайте пакет VSPackage с командой меню, как в разделе [разделы справки начать разработку РАСШИРЕНИЙ VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Откройте файл, содержащий определение VSPackage. (В проекте C# это <em>\<your project name></em> Package.cs.)  
  
3. Добавьте следующие операторы `using`:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Найдите метод `MenuItemCallback`. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект <xref:EnvDTE80.DTE2>:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Добавьте код из надстройки. Например, ниже приведен код, который добавляет новые задачи в **список задач**, перечисляет количество задач, а затем удаляет одну задачу.  
  
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
  
1. Создайте пакет VSPackage с командой меню, как в разделе [разделы справки начать разработку РАСШИРЕНИЙ VSIX?](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md#BKMK_StartDeveloping) .  
  
2. Откройте файл, содержащий определение VSPackage. (В проекте C# это <em>\<your project name></em> Package.cs.)  
  
3. Добавьте следующие операторы `using`:  
  
   ```csharp  
   using EnvDTE;  
   using EnvDTE80;  
   ```  
  
4. Найдите метод `MenuItemCallback`. Добавьте вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>, чтобы получить объект <xref:EnvDTE80.DTE2>:  
  
   ```csharp  
   DTE2 dte = (DTE2)GetService(typeof(DTE));  
   ```  
  
5. Добавьте код из надстройки. Например, следующий код позволяет получить имя запускаемого проекта в решении. (При запуске этого пакета должно быть открыто многопроектное решение.)  
  
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
