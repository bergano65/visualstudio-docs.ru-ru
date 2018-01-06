---
title: "Получение свойств проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 58a24a37de7986ef47acb916d488bd4661c5a4d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="getting-project-properties"></a>Получение свойств проекта
В этом пошаговом руководстве показано, как свойства проекта отображается в окне инструментов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Создайте проект VSIX и добавление окна инструментов  
  
1.  Все расширения Visual Studio начинается с проект развертывания VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `ProjectPropertiesExtension`. Шаблон проекта VSIX в можно найти **новый проект** диалогового окна в разделе **Visual C# / Extensibility**.  
  
2.  Добавить окно инструментов, добавив шаблон элемента пользовательского окна инструментов с именем `ProjectPropertiesToolWindow`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **диалоговое окно добавления нового элемента**, перейдите в меню **элементы Visual C# / расширяемости** и выберите **окно инструментов настраиваемый**. В **имя** в нижней части диалогового окна, измените имя файла для `ProjectPropertiesToolWindow.cs`. Дополнительные сведения о создании пользовательского окна инструментов см. в разделе [создания расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Выполните сборку решения и убедитесь в том, что оно компилируется без ошибок.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Для отображения свойств проекта в окне инструментов  
  
1.  В файле ProjectPropertiesToolWindowCommand.cs добавьте следующие операторы using.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  В ProjectPropertiesToolWindowControl.xaml удалите существующую кнопку и добавьте TreeView из области элементов. Можно также удалить из файла ProjectPropertiesToolWindowControl.xaml.cs обработчик события нажатия кнопки.  
  
3.  В ProjectPropertiesToolWindowCommand.cs используйте метод ShowToolWindow() для открытия проекта и чтения его свойства, а затем добавьте свойства для TreeView. Код для ShowToolWindow должен выглядеть следующим образом:  
  
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
  
4.  Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.  
  
5.  В экспериментальном экземпляре откройте проект.  
  
6.  В **представления и другие окна** щелкните **ProjectPropertiesToolWindow**.  
  
     Вы увидите дерево в окне инструментов вместе с именем первого проекта и всех его свойств проекта.