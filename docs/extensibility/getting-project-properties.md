---
title: Получение свойств проекта | Документация Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6708759796639886d84a46003fbb894b988a714
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194999"
---
# <a name="get-project-properties"></a>Получение свойств проекта

В этом пошаговом руководстве показано, как к свойствам проекта отображается в окне инструментов.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Создайте проект VSIX и добавить окно инструментов

1. Все расширения Visual Studio начинается с развертывания проект VSIX, который будет содержать средств расширения. Создание [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX с именем `ProjectPropertiesExtension`. Вы найдете шаблон проекта VSIX в **новый проект** диалоговое окно, выполняя поиск «vsix».

2. Добавление окна инструментов, добавив шаблон элемента пользовательского окна инструментов с именем `ProjectPropertiesToolWindow`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить** > **новый элемент**. В **диалоговое окно Add New Item**, перейдите в меню **элементы Visual C#** > **расширяемости** и выберите **окно инструментов Custom**. В **имя** в нижней части диалогового окна, измените имя файла для `ProjectPropertiesToolWindow.cs`. Дополнительные сведения о создании пользовательского окна инструментов см. в разделе [создание расширения с окном инструментов](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Выполните сборку решения и убедитесь в том, что оно компилируется без ошибок.

### <a name="to-display-project-properties-in-a-tool-window"></a>Для отображения свойств проекта в окне инструментов

1. В файле ProjectPropertiesToolWindowCommand.cs, добавьте следующие операторы using.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. В *ProjectPropertiesToolWindowControl.xaml*, удалить существующую кнопку и добавление элемента управления TreeView из области элементов. Можно также удалить обработчик событий click из *ProjectPropertiesToolWindowControl.xaml.cs* файла.

3. В *ProjectPropertiesToolWindowCommand.cs*, используйте `ShowToolWindow()` метод, чтобы открыть проект и прочитать его свойства, затем добавьте свойства в виде дерева. Код для ShowToolWindow должен выглядеть следующим образом:

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

4. Выполните сборку решения и запустите отладку. Откроется экспериментальный экземпляр.

5. Откройте проект в экспериментальном экземпляре.

6. В **представление** > **Other Windows** щелкните **ProjectPropertiesToolWindow**.

  Вы увидите дерево в окне инструментов вместе с именем первого проекта и всех его свойств проекта.