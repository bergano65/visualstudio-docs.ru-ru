---
title: "Расширение в окне вывода | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Окно вывода, сведения об окне выходных данных"
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Расширение в окне вывода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Выходной** окно — это набор областей текста, чтение и запись. Visual Studio содержит следующие встроенные панели: **построения**, в какие проекты обмена сообщениями о построениях, и **Общие**, в котором [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] передает сообщения об Интегрированной среде разработки. Проекты получить ссылку на **построения** области автоматически посредством <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> методов интерфейса, а Visual Studio предлагает прямой доступ к **Общие** области через <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> службы. Помимо встроенных панелей можно создать и управлять собственных пользовательских панелей.  
  
 Можно управлять **вывода** напрямую с помощью окна <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> интерфейсов.<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Интерфейс, который предлагается в <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> службы, определяет методы для создания, извлечения и уничтожение **вывода** области окна.<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> Интерфейс определяет методы для отображения панелей, скрытие панелей и управление им текста. Альтернативным способом управления **вывода** окна – <xref:EnvDTE.OutputWindow> и <xref:EnvDTE.OutputWindowPane> объекты в объектной модели автоматизации Visual Studio. Эти объекты инкапсулируют практически все функциональные возможности <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> интерфейсов. Кроме того <xref:EnvDTE.OutputWindow> и <xref:EnvDTE.OutputWindowPane> объекты добавить некоторые функции более высокого уровня для облегчения перечисления **вывода** области окна и извлечение текста из области.  
  
## Создание расширения, который используется в области вывода  
 Можно создать расширение, которое выполняет различные аспекты области вывода.  
  
1.  Создайте проект VSIX с именем `TestOutput` с командой меню с именем **TestOutput**. Для получения дополнительной информации см. [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Добавьте следующие ссылки:  
  
    1.  EnvDTE  
  
    2.  EnvDTE80  
  
3.  В TestOutput.cs, добавьте следующий оператор using:  
  
    ```f#  
    using EnvDTE; using EnvDTE80;  
    ```  
  
4.  В TestOutput.cs удалите метод ShowMessageBox. Добавьте следующий метод заглушки:  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { }  
    ```  
  
5.  В конструкторе TestOutput измените обработчик команды на OutputCommandHandler. Вот часть, которая добавляет команды:  
  
    ```c#  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService; if (commandService != null) { CommandID menuCommandID = new CommandID(MenuGroup, CommandId); EventHandler eventHandler = OutputCommandHandler; MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID); commandService.AddCommand(menuItem); }  
    ```  
  
6.  В приведенных ниже разделах существуют различные методы, которые демонстрируют различные способы работы с области вывода. Может вызывать эти методы в теле метода OutputCommandHandler\(\). Например следующий код добавляет метод CreatePane\(\), приведенные в следующем разделе.  
  
    ```c#  
    private void OutputCommandHandler(object sender, EventArgs e) { CreatePane(new Guid(), "Created Pane", true, false); }  
    ```  
  
## Создание окно вывода с IVsOutputWindow  
 В этом примере показано, как создать новую **вывода** область окна с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> интерфейса.  
  
```c#  
void CreatePane(Guid paneGuid, string title, bool visible, bool clearWithSolution) { IVsOutputWindow output = (IVsOutputWindow)GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; // Create a new pane. output.CreatePane( ref paneGuid, title, Convert.ToInt32(visible), Convert.ToInt32(clearWithSolution)); // Retrieve the new pane. output.GetPane(ref paneGuid, out pane); pane.OutputString("This is the Created Pane \n"); }  
```  
  
 Если добавить этот метод расширения, указанного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды вы должны увидеть **Выходные данные** окно с заголовком, — говорит **Показать выходные данные от: CreatedPane** и слова **это область создана** в саму область.  
  
## Создание окно вывода с OutputWindow  
 В этом примере показано, как создать **вывода** область окна с помощью <xref:EnvDTE.OutputWindow> объекта.  
  
```c#  
void CreatePane(string title) { DTE2 dte = (DTE2)GetService(typeof(DTE)); OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; try { // If the pane exists already, write to it. panes.Item(title); } catch (ArgumentException) { // Create a new pane and write to it. return panes.Add(title); } }  
```  
  
 Хотя <xref:EnvDTE.OutputWindowPanes> коллекции позволяет извлекать **вывода** область окна по его названию, области заголовков не гарантируется уникальность. Когда сомневаюсь уникальность заголовок, используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> метод для получения правильного панели по его идентификатору GUID.  
  
 Если добавить этот метод расширения, указанного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы увидите в окне вывода с заголовком, — говорит **Показать выходные данные от: DTEPane** и слова **добавлены панели DTE** в самой области.  
  
## Удаление окно вывода  
 В этом примере показано, как удалить **вывода** область окна.  
  
```c#  
void DeletePane(Guid paneGuid) { IVsOutputWindow output = (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow)); IVsOutputWindowPane pane; output.GetPane(ref paneGuid, out pane); if (pane == null) { CreatePane(paneGuid, "New Pane\n", true, true); } else { output.DeletePane(ref paneGuid); } }  
```  
  
 Если добавить этот метод расширения, указанного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы увидите в окне вывода с заголовком, — говорит **Показать выходные данные от: Новая область** и слова **добавлены созданные панели** в саму область. При нажатии кнопки **вызова TestOutput** команду еще раз, область удаляется.  
  
## Начало области Общие окна вывода  
 В этом примере показано, как получить встроенной **Общие** области **вывода** окна.  
  
```c#  
void GetGeneralPane() { return (IVsOutputWindowPane)GetService( typeof(SVsGeneralOutputWindowPane)); }  
```  
  
 Если добавить этот метод расширения, указанного в предыдущем разделе, при нажатии кнопки **вызова TestOutput** команды, вы увидите, **вывода** окне отображаются слова **Найти общие области** в области.  
  
## Начало области построения окна вывода  
 В этом примере показано, как найти области построения и записи в файл. Поскольку области построения не активирован по умолчанию, она активируется также.  
  
```c#  
void OutputTaskItemStringExExample(string buildMessage) { EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE)); EnvDTE.OutputWindowPanes panes = dte.ToolWindows.OutputWindow.OutputWindowPanes; foreach (EnvDTE.OutputWindowPane pane in panes) { if (pane.Name.Contains("Build")) { pane.OutputString(buildMessage + "\n"); pane.Activate(); return; } } }  
```