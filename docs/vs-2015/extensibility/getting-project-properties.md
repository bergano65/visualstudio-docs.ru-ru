---
title: Получение свойств проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d0557d08c318eda47853ec69c6204739cbece560
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204319"
---
# <a name="getting-project-properties"></a>Получение свойств проекта
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как отобразить свойства проекта в окне инструментов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Создание проекта VSIX и Добавление окна инструментов  
  
1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать ресурсы расширения. Создайте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проект VSIX с именем `ProjectPropertiesExtension` . Шаблон проекта VSIX можно найти в диалоговом окне **Новый проект** в разделе **Visual C#/Extensibility (расширяемость**).  
  
2. Добавьте окно инструментов, добавив пользовательский шаблон элемента окна инструментов с именем `ProjectPropertiesToolWindow` . В **Обозреватель решений**щелкните правой кнопкой мыши узел проекта и выберите **Добавить/новый элемент**. В **диалоговом окне Добавление нового элемента**перейдите к **элементу Visual C# элементы/Расширяемость** и выберите **настраиваемое окно инструментов**. В поле **имя** в нижней части диалогового окна измените имя файла на `ProjectPropertiesToolWindow.cs` . Дополнительные сведения о создании настраиваемого окна инструментов см. в разделе [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. Выполните сборку решения и убедитесь в том, что оно компилируется без ошибок.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Отображение свойств проекта в окне инструментов  
  
1. В файле ProjectPropertiesToolWindowCommand.cs добавьте следующие операторы using.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2. В Прожектпропертиестулвиндовконтрол. XAML удалите существующую кнопку и добавьте TreeView из панели элементов. Кроме того, можно удалить обработчик событий щелчка из файла ProjectPropertiesToolWindowControl.xaml.cs.  
  
3. В ProjectPropertiesToolWindowCommand.cs используйте метод Шовтулвиндов (), чтобы открыть проект и прочитать его свойства, а затем добавьте свойства в TreeView. Код для Шовтулвиндов должен выглядеть следующим образом:  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр.  
  
5. В экспериментальном экземпляре откройте проект.  
  
6. В **представлении или других окнах** щелкните **прожектпропертиестулвиндов**.  
  
     Элемент управления "дерево" должен отображаться в окне инструментов вместе с именем первого проекта и всех его свойств.
