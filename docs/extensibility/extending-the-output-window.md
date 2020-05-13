---
title: Расширение окна вывода (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711646"
---
# <a name="extend-the-output-window"></a>Расширить окно вывода
**Окно вывода** представляет собой набор текстовых стекол для чтения/записи. Visual Studio имеет эти встроенные стекла: **Build**, в котором проекты передают [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] сообщения о сборках, и **General**, в котором передает сообщения о IDE. Проекты автоматически получают ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> панель **сборки** с помощью методов интерфейса, <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> а Visual Studio предлагает прямой доступ к **общему** стеку через службу. В дополнение к встроенным стеклам, вы можете создавать и управлять своими собственными пользовательскими стеклами.

 Вы можете **Output** управлять окном <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> вывода <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> непосредственно через интерфейсы и интерфейсы. Интерфейс, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> предлагаемый службой, <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> определяет методы создания, извлечения и уничтожения оконных стекол. **Output** Интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> определяет методы отображения стекол, сокрытия стекол и манипулирования их текстом. Альтернативный способ управления окном **вывода** <xref:EnvDTE.OutputWindow> — <xref:EnvDTE.OutputWindowPane> это объекты в модели объектов Visual Studio Automation. Эти объекты инкапсулируют почти всю <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> функциональность <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> интерфейсов и интерфейсов. Кроме того, <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> объекты добавляют некоторые функциональные возможности более высокого уровня, чтобы облегчить перечисление оконных стекол **выходного** окна и извлечение текста из стекол.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Создайте расширение, используюв оглашку выходного стекла
 Вы можете сделать расширение, которое осуществляет различные аспекты панели вывода.

1. Создайте проект VSIX с `TestOutput` командой меню под названием **TestOutput.** Для получения дополнительной информации [см. Создать расширение с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Добавьте следующие ссылки.

    1. EnvDTE

    2. EnvDTE80

3. В *TestOutput.cs*добавьте следующее заявление с помощью:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. В *TestOutput.cs,* `ShowMessageBox` удалите метод. Добавьте следующий метод заглушки:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. В конструкторе TestOutput измените обработчик команды на OutputCommandHandler. Вот часть, которая добавляет команды:

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

6. В приведенных ниже разделах имеются различные методы, отображающие различные способы работы с панелью выходного слоя. Эти методы можно назвать телом `OutputCommandHandler()` метода. Например, следующий код `CreatePane()` добавляет метод, приведенный в следующем разделе.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Создание окна вывода с помощью IVsOutputWindow
 В этом примере показано, как создать новое <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> стекло окна **output** с помощью интерфейса.

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

 Если вы добавите этот метод к расширению, приведенном в предыдущем разделе, при нажатии на команду **Invoke TestOutput** вы должны увидеть окно **вывода** с заголовком, который говорит **Показать выход из: CreatedPane** и слова **Это созданный pane** в самом панели.

## <a name="create-an-output-window-with-outputwindow"></a>Создание окна вывода с помощью OutputWindow
 В этом примере **Output** показано, как создать <xref:EnvDTE.OutputWindow> оконное стекло вывода с помощью объекта.

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
        panes.Add(title);
    }
}
```

 Несмотря <xref:EnvDTE.OutputWindowPanes> на то, что коллекция позволяет получить оконное стекло **Output** по названию, названия стекол не гарантированно уникальны. Если вы сомневаетесь в уникальности <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> названия, используйте метод, чтобы получить правильное стекло его GUID.

 Если вы добавите этот метод к расширению, приведенном в предыдущем разделе, при нажатии на команду **Invoke TestOutput** вы должны увидеть окно вывода с заголовком, который говорит **Показать выход из: DTEPane** и слова **Добавленный DTE Pane** в самом стекле.

## <a name="delete-an-output-window"></a>Удаление окна вывода
 В этом примере показано, как удалить стекло окна **вывода.**

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

 Если вы добавите этот метод к расширению, приведенном в предыдущем разделе, при нажатии на команду **Invoke TestOutput** вы должны увидеть окно вывода с заголовком, который говорит **Показать выход из: New Pane** и слова **Добавленные Созданные pane** в самом панели. Если вы нажмете на команду **Invoke TestOutput** снова, панель удаляется.

## <a name="get-the-general-pane-of-the-output-window"></a>Получить общее стекло окна вывода
 В этом примере показано, как получить встроенное **общее** стекло окна **вывода.**

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Если вы добавите этот метод к расширению, приведенным в предыдущем разделе, при нажатии на команду **Invoke TestOutput** вы должны увидеть, что в окне **вывода** отображается слова **Найдено Общее стекло** в панели.

## <a name="get-the-build-pane-of-the-output-window"></a>Получить развернуть стекло вывода
 В этом примере показано, как найти панель **сборки** и написать на него. Так как панель **сборки** не активирована по умолчанию, она активирует его также.

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
