---
title: Управление универсальными проектами Windows Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc6894bcfe3bfab3b0246d716b0bd85152ad17e2
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744921"
---
# <a name="manage-universal-windows-projects"></a>Управление универсальными проектами Windows

Универсальные приложения Windows — это приложения, ориентированные как на Windows 8.1, так и на Windows Phone 8.1, что позволяет разработчикам использовать код и другие ресурсы на обеих платформах. Общий код и ресурсы хранятся в совместном проекте, в то время как код и ресурсы, специфичные для платформы, хранятся в отдельных проектах, один для Windows, а другой для Windows Phone. Для получения дополнительной информации об универсальных приложениях Windows, [см.](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx) Расширения Visual Studio, которые управляют проектами, должны знать, что универсальные проекты приложений Windows имеют структуру, которая отличается от одноплатформенных приложений. В этом пошаговом показании, как перемещаться по общему проекту и управлять общими элементами.

## <a name="prerequisites"></a>Предварительные требования

Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="navigate-the-shared-project"></a>Навигация по общему проекту

1. Создайте проект СЗ VSIX под названием **TestUniversalProject**. (**Файл** > **Новый** > **проект,** а затем **СЗ** > **Расширяемый** > **Визуальный Studio Package**). Добавить шаблон элемента элемента проекта **Custom Command** (на **Solution Explorer**, правой кнопкой мыши узла проекта и выберите **Добавить** > **новый пункт,** а затем перейдите к **Расширительность).** Назовите файл **TestUniversalProject**.

2. Добавить ссылку на *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* и *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (в разделе **Расширения).**

3. Откройте *TestUniversalProject.cs* и `using` добавьте следующие директивы:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. В `TestUniversalProject` классе добавьте частное поле, указывавщее на окно **вывода.**

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Установите ссылку на выходное стекло внутри конструктора TestUniversalProject:

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }

        // get a reference to the Output window
        output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. Удалите существующий `ShowMessageBox` код из метода:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Получите объект DTE, который мы будем использовать для нескольких различных целей в этом пошаговом пошаговом пошаговом пошаге. Кроме того, убедитесь, что решение загружается при нажатии кнопки меню.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Найдите общий проект. Общий проект представляет собой чистый контейнер; он не создает и не производит продукцию. Следующий метод находит первый общий проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> в решении, ища объект, который имеет общую возможность проекта.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. В `ShowMessageBox` методе вывежаем заголовок (имя проекта, которое отображается в **Solution Explorer)** совместного проекта.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Получить активный проект платформы. Проекты платформы — это проекты, содержащие код и ресурсы, связанные с платформой. Следующий метод использует <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> новое поле для получения активного проекта платформы.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. В `ShowMessageBox` методе выводится подпись проекта активной платформы.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                    MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Итерировать через платформу проектов. Следующий метод получает все импортные (платформенные) проекты из общего проекта.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Если пользователь открыл универсальный проект приложения Windows в экспериментальном экземпляре, приведенный выше код выбрасывает исключение. Это известная проблема Чтобы избежать исключения, `foreach` замените вышеуказанный блок следующим:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. В `ShowMessageBox` методе выводится подпись каждого проекта платформы. Вставьте следующий код после строки, которая выводит заголовок проекта активной платформы. В этом списке отображаются только загруженные проекты платформы.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Измените проект активной платформы. Следующий метод устанавливает активный <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>проект с помощью .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. В `ShowMessageBox` методе измените проект активной платформы. Вставьте этот `foreach` код внутри блока.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Теперь попробуйте его. Нажмите F5 для запуска экспериментального экземпляра. Создайте проект универсального концентраторного приложения в экспериментальном экземпляре (в диалоговом окне **нового проекта,** **Visual C'** > **Windows** > **8** > **Universal** > Hub**App).** После загрузки решения перейдите в меню **Tools** и нажмите **Найдите Invoke TestUniversalProject,** а затем проверьте текст в **панели вывода.** Вы должны увидеть нечто вроде этого:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Управление общими элементами в проекте платформы

1. Найдите общие элементы в проекте платформы. Элементы совместного проекта отображаются в проекте платформы в виде общих элементов. Вы не можете увидеть их в **solution Explorer,** но вы можете пройти иерархию проекта, чтобы найти их. Следующий метод ходит по иерархии и собирает все общие элементы. Он дополнительно выводит заголовок каждого элемента,. Общие элементы идентифицируются <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>новым свойством.

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
        }
    }
    ```

2. В `ShowMessageBox` методе добавьте следующий код для ходьбы элементов иерархии проектов платформы. Вставьте его `foreach` в блок.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Прочитайте общие элементы. Общие элементы отображаются в проекте платформы как скрытые связанные файлы, и вы можете прочитать все свойства как обычные связанные файлы. Следующий код считывает полный путь первого общего элемента.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Теперь попробуйте его. Нажмите **F5** для запуска экспериментального экземпляра. Создайте проект универсального концентраторного приложения в экспериментальном экземпляре (в диалоговом окне **нового проекта,** **Visual C'** > **Windows** > **8** > **Universal** > Hub**App)** перейдите в меню **Инструментов** и нажмите **Найдите Invoke TestUniversalProject,** а затем проверьте текст в панели **вывода.** Вы должны увидеть нечто вроде этого:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Обнаружение изменений в платформенных проектах и общих проектах

1. Можно использовать иерархию и события проекта для обнаружения изменений в общих проектах, точно так же, как это возможно для проектов платформ. Однако элементы проекта в совместном проекте не видны, что означает, что некоторые события не сравниваются при изменении общих элементов проекта.

    Рассмотрим последовательность событий при переименовании файла в проекте:

   1. Имя файла изменено на диске.

   2. Файл проекта обновляется, чтобы включить новое имя файла.

      События иерархии (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) обычно отслеживают изменения, отображаемые в ui, как в Solution **Explorer**. События иерархии считают, что операция переименования файла состоит из удаления файла, а затем добавления файла. Однако при изменении невидимых элементов система <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> события иерархии запускает событие, а не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> событие. Поэтому, если вы переименуете файл в <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>платформы, вы получите и то, и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>другое, но если вы переименуете файл в общий проект, вы получите только.

      Чтобы отслеживать изменения в элементах проекта, можно обрабатывать события <xref:EnvDTE.ProjectItemsEventsClass>элемента проекта DTE (те, которые находятся в). Однако, если вы обрабатываете большое количество событий, вы <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>можете получить лучшую производительность обработки событий в . В этом пошаговом шаге мы показываем только события иерархии и события DTE. В этой процедуре вы добавляете слушателя события в общий проект и проект платформы. Затем при переименовании одного файла в общий проект и другого файла в проекте платформы можно увидеть события, которые будут запущены для каждой операции переименования.

      В этой процедуре вы добавляете слушателя события в общий проект и проект платформы. Затем при переименовании одного файла в общий проект и другого файла в проекте платформы можно увидеть события, которые будут запущены для каждой операции переименования.

2. Добавьте слушателя события. Добавьте в проект новый файл класса и назовите его *HierarchyEventListener.cs.*

3. Откройте *файл HierarchyEventListener.cs* и добавьте следующие директивы:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Исесть <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>класса реализации: `HierarchyEventListener`

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>членов, как в коде ниже.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. В этом же классе добавьте еще <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>один обработчик событий для события DTE, который происходит всякий раз, когда элемент проекта переименовывается.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Подпишитесь на события иерархии. Вы должны зарегистрироваться отдельно для каждого проекта, который вы отслеживаете. Добавьте следующий `ShowMessageBox`код в один для общего проекта, а другой для одного из проектов платформы.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. Подпишитесь на событие <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>элемента проекта DTE. Добавьте следующий код после подключения второго слушателя.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Измените общий элемент. Вы не можете изменить общие элементы в проекте платформы; вместо этого необходимо изменить их в общем проекте, который является фактическим владельцем этих элементов. Вы можете получить соответствующий идентификатор элемента в общем проекте с, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>придав ему полный путь общего элемента. Затем можно изменить общий элемент. Изменение распространяется на проекты платформы.

    > [!IMPORTANT]
    > Прежде чем изменять его, необходимо выяснить, является ли элемент проекта общим элементом.

     Следующий метод изменяет имя файла элемента проекта.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Вызовите этот метод после `ShowMessageBox` того, как все другие коды в изменить имя файла элемент в совместном проекте. Вставьте это после кода, который получает полный путь элемента в совместном проекте.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Постройте и запустите проект. Создайте универсальное приложение концентратора в экспериментальном экземпляре, перейдите в меню **Tools** и нажмите **Найдите Invoke TestUniversalProject**и проверьте текст в общем выходном стекле. Имя первого элемента в общем проекте (мы ожидаем, что это будет файл *App.xaml)* должно быть изменено, и вы должны увидеть, что <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> событие было запущено. В этом случае, поскольку переименование *App.xaml* приводит к *App.xaml.cs* быть переименован, вы должны увидеть четыре события (два для каждого проекта платформы). (События DTE не отслеживают элементы совместного проекта.) Вы должны <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> увидеть два события (по одному <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> для каждого из проектов платформы), но никаких событий.

12. Теперь попробуйте переименовать файл в проект платформы, и вы можете увидеть разницу в событиях, которые будут уволены. Добавьте следующий `ShowMessageBox` код после `ModifyFileName`вызова.

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Постройте и запустите проект. Создайте универсальный проект c', перейдите в меню **Инструментов** и нажмите **Найдите Invoke TestUniversalProject**и проверьте текст в общем выходном стекле. После того, как файл в проекте платформы <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> будет <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> переименован, вы должны увидеть как событие, так и событие. Поскольку изменение файла не привело к изменению других файлов, а поскольку изменения в элементах в проекте платформы нигде не распространяются, есть только одно из этих событий.
