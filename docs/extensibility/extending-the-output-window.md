---
title: Расширение в окне вывода | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b9a8b260c1a3cab126d19f0cedc0c1e5362cf81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-output-window"></a>Расширение в окне вывода
**Вывода** окна — это набор областей текста для чтения и записи. В Visual Studio есть этих встроенных панелей: **построения**, в какие проекты обмена сообщениями о сборках, и **Общие**, в котором [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] передает сообщения о интегрированной среды разработки. Проекты получить ссылку на **построения** панели автоматически посредством <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> методов интерфейса и Visual Studio предоставляет прямой доступ к **Общие** области посредством <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> Служба. Помимо встроенных панелей можно создавать и собственные пользовательские панели управления.  
  
 Можно управлять **вывода** напрямую с помощью окна <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> интерфейсов. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Интерфейс, который предлагаемых <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> службы, определяет методы для создания, извлечения и уничтожение **вывода** области окна. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Интерфейс определяет методы для отображения панелей, скрытие области и управление их текст. Альтернативный способ управления **вывода** окно выполняется с помощью <xref:EnvDTE.OutputWindow> и <xref:EnvDTE.OutputWindowPane> объекты в объектной модели автоматизации Visual Studio. Эти объекты инкапсулируют практически все функциональные возможности <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> интерфейсов. Кроме того <xref:EnvDTE.OutputWindow> и <xref:EnvDTE.OutputWindowPane> объектов добавить некоторые функции более высокого уровня для упрощения перечислить **вывода** области окна и извлечь текст из области.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Создание расширения, использующего области вывода  
 Можно создать расширение, которое проверяет различные аспекты области вывода.  
  
1.  Создайте проект VSIX с именем `TestOutput` с помощью команды меню с именем **TestOutput**. Дополнительные сведения см. в разделе [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Добавьте следующие ссылки:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  В TestOutput.cs, добавьте следующий код с помощью инструкции:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4.  В TestOutput.cs удалите метод ShowMessageBox. Добавьте следующие заглушки метода:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5.  В конструкторе TestOutput измените обработчик команд на OutputCommandHandler. Вот часть, которая добавляет команды:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6.  В следующих разделах существуют различные методы, которые демонстрируют различные способы работы с области вывода. Может вызывать эти методы тело метода OutputCommandHandler(). Например следующий код добавляет метод CreatePane(), приведенные в следующем разделе.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Создание с IVsOutputWindow окно вывода  
 В этом примере показано, как создать новую **вывода** область окна с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> интерфейса.  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 При добавлении этого метода расширения, указанного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы увидите **вывода** окна с заголовком, которое говорит **Показать выходные данные из: CreatedPane** и слова **это в области создания** в самой области.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Создание с OutputWindow окно вывода  
 В этом примере показано, как создать **вывода** область окна с помощью <xref:EnvDTE.OutputWindow> объекта.  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Несмотря на то что <xref:EnvDTE.OutputWindowPanes> коллекции позволяет получать **вывода** область окна по заголовку, названия области не гарантируется уникальность. Когда вы сомневаюсь уникальность заголовок, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> метод для извлечения области правильный по его идентификатору GUID.  
  
 Если добавить этот метод расширения, указанного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы увидите в окне вывода с заголовком, которое говорит **Показать выходные данные от: DTEPane** и слова **добавлена панель DTE** в самой области.  
  
## <a name="deleting-an-output-window"></a>Удаление окно вывода  
 В этом примере показано, как удалить **вывода** области окна.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 При добавлении этого метода расширения, указанного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы увидите в окне вывода с заголовком, которое говорит **Показать выходные данные от: Новая панель** и слова **добавлены созданные панели** в самой области. Если щелкнуть **TestOutput вызова** команду еще раз, удаляется области.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Получение области Основные в окне вывода  
 В этом примере показано, как получить встроенной **Общие** области **вывода** окна.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 При добавлении этого метода расширения, указанного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы должны увидеть **выходные данные** в окне отображаются слова **найти общие область** в области.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Получение области построения в окне вывода  
 В этом примере показано, как найти в области построения и записи в файл. Поскольку по умолчанию не активирован в области построения, он активируется также.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```