---
title: Как создать расширение проекта SharePoint | Документация Майкрософт
description: Узнайте, как создать расширение проекта, чтобы можно было добавлять функциональные возможности в любой проект SharePoint, Открытый в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/28/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 88d2a7b411097bdf2a90ec04456bfc4419e31c30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923341"
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>Как создать расширение проекта SharePoint
  Создайте расширение проекта, если необходимо добавить функциональные возможности в любой проект SharePoint, Открытый в Visual Studio. Дополнительные сведения см. в разделе [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="to-create-a-project-extension"></a>Создание расширения проекта

1. Создайте проект библиотеки классов.

2. Добавьте ссылки на следующие сборки:

    - Microsoft. VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.

4. Добавьте в <xref:System.ComponentModel.Composition.ExportAttribute> класс. Этот атрибут позволяет Visual Studio обнаруживать и загружать <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> реализацию. Передайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> тип в конструктор атрибута.

5. В реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метода используйте члены параметра *прожектсервице* , чтобы определить поведение вашего расширения. Этот параметр является <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> объектом, предоставляющим доступ к событиям, определенным в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> интерфейсе.

## <a name="example"></a>Пример
 В следующем примере кода показано, как создать простое расширение проекта, которое обрабатывает большинство событий проекта SharePoint, определенных <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> интерфейсом. Чтобы протестировать код, создайте проект SharePoint в, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] а затем добавьте в него другие проекты, измените значения свойств проекта или удалите или исключите проект. Расширение уведомляет вас о событиях, записывая сообщения в окно **вывода** и **Список ошибок** окно.

  ```vb
    Imports Microsoft.VisualStudio.SharePoint
    Imports System.ComponentModel
    Imports System.ComponentModel.Composition

    Namespace Contoso.ExampleProjectExtension
      <Export(GetType(ISharePointProjectExtension))> _
      Class ExampleProjectExtension
        Implements ISharePointProjectExtension

        Private WithEvents projectService As ISharePointProjectService

        Public Sub Initialize(ByVal projectService As ISharePointProjectService) _
            Implements ISharePointProjectExtension.Initialize
            Me.projectService = projectService
        End Sub

        ' A project was added.
        Private Sub projectService_ProjectAdded(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectAdded
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was added: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was loaded in the IDE.
        Private Sub projectService_ProjectInitialized(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectInitialized
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being initialized: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' The name of a property was changed.
        Private Sub projectService_ProjectNameChanged(ByVal sender As Object, ByVal e As NameChangedEventArgs) _
            Handles projectService.ProjectNameChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project property value was changed.
        Private Sub ProjectPropertyChanged(ByVal sender As Object, ByVal e As PropertyChangedEventArgs) _
            Handles projectService.ProjectPropertyChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project is being removed or unloaded.
        Private Sub projectService_ProjectRemoved(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectRemoved
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was removed or unloaded.
        Private Sub projectService_ProjectDisposing(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectDisposing
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub
      End Class
    End Namespace
    ```

    ```csharp
    using Microsoft.VisualStudio.SharePoint;
    using System;
    using System.ComponentModel;
    using System.ComponentModel.Composition;

    namespace Contoso.ExampleProjectExtension
    {
      [Export(typeof(ISharePointProjectExtension))]
      internal class ExampleProjectExtension : ISharePointProjectExtension
      {
        public void Initialize(ISharePointProjectService projectService)
        {
            projectService.ProjectAdded += projectService_ProjectAdded;
            projectService.ProjectInitialized += projectService_ProjectInitialized;
            projectService.ProjectNameChanged += projectService_ProjectNameChanged;
            projectService.ProjectPropertyChanged += projectService_ProjectPropertyChanged;
            projectService.ProjectRemoved += projectService_ProjectRemoved;
            projectService.ProjectDisposing += projectService_ProjectDisposing;
        }

        // A project was added.
        void projectService_ProjectAdded(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was added: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is loaded in the IDE.
        void projectService_ProjectInitialized(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being initialized: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // The name of a project was changed.
        void projectService_ProjectNameChanged(object sender, NameChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project property value was changed.
        private void projectService_ProjectPropertyChanged(object sender, PropertyChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is being removed or unloaded.
        void projectService_ProjectRemoved(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project was removed or unloaded.
        void projectService_ProjectDisposing(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }
     }
  }
  ```

В этом примере используется служба проекта SharePoint для записи сообщения в окно **вывода** и **Список ошибок** окно. Дополнительные сведения см. [в статье Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

 Примеры, демонстрирующие обработку <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> событий и, см. в разделе [как добавить пункт контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) и [как добавить свойство в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

## <a name="compile-the-code"></a>Компиляция кода
 Для этого примера требуются ссылки на следующие сборки:

- Microsoft. VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Развертывание расширения
 Чтобы развернуть расширение, создайте [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX) для сборки и всех остальных файлов, которые требуется распространить с расширением. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Как добавить пункт контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Как добавить свойство в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Пошаговое руководство. Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
