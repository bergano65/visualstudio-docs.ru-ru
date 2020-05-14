---
title: Получение свойства проекта (ru) Документы Майкрософт
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711415"
---
# <a name="get-project-properties"></a>Получить свойства проекта

В этом пошаговом показании, как отображать свойства проекта в окне инструмента.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Создать проект VSIX и добавить окно инструмента

1. Каждое расширение Visual Studio начинается с проекта развертывания VSIX, который будет содержать активы расширения. Создайте [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект VSIX под названием `ProjectPropertiesExtension`. Шаблон проекта VSIX можно найти в диалоге **нового проекта,** ища "vsix".

2. Добавьте окно инструмента, добавив шаблон элемента Custom Tool Window под названием. `ProjectPropertiesToolWindow` В **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт**. В **диалоге Добавить новый элемент**, перейдите к **Visual C' Элементы** > **Расширяемость** и выберите **пользовательский инструмент окно**. В поле **«Имя»** в нижней части диалога `ProjectPropertiesToolWindow.cs`измените имя файла на . Для получения дополнительной информации о том, как создать пользовательское окно инструмента, [см.](../extensibility/creating-an-extension-with-a-tool-window.md)

3. Выполните сборку решения и убедитесь в том, что оно компилируется без ошибок.

### <a name="to-display-project-properties-in-a-tool-window"></a>Отобразить свойства проекта в окне инструмента

1. В ProjectPropertiesToolWindowCommand.cs файла добавьте следующие директивы с помощью.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. В *ProjectPropertiesToolWindowControl.xaml*удалите существующую кнопку и добавьте TreeView из коробки инструментов. Можно также удалить обработчик события щелчка из файла *ProjectPropertiesToolWindowControl.xaml.cs.*

3. В *ProjectPropertiesToolWindowCommand.cs,* `ShowToolWindow()` используйте метод, чтобы открыть проект и прочитать его свойства, а затем добавить свойства в TreeView. Код для ShowToolWindow должен выглядеть следующим образом:

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

4. Выполните сборку решения и запустите отладку. Экспериментальный экземпляр должен появиться.

5. Откройте проект в экспериментальном экземпляре.

6. В **просмотре** > **Другие Windows** нажмите **ProjectPropertiesToolWindow**.

  Вы должны видеть управление деревом в окне инструмента вместе с названием первого проекта и всеми его свойствами проекта.
