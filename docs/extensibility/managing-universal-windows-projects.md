---
title: "Управление проектами универсальной Windows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Управление проектами универсальной Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Универсальные приложения Windows — приложений, предназначенных для Windows 8.1 и Windows Phone 8.1, благодаря чему разработчики могут использовать код и другие ресурсы на обеих платформах. Общий код и ресурсы хранятся в общий проект, хотя код платформы и ресурсы хранятся в отдельных проектов, один для Windows и другой — для Windows Phone. Дополнительные сведения об универсальных приложениях Windows см. в разделе [универсальных приложений Windows](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Расширения Visual Studio, управление проектами следует иметь в виду, что проектов универсальных приложений Windows имеют структуру, отличную от одной платформы приложений. В этом пошаговом руководстве показано, как переходить общего проекта и управлять ими общих элементов.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Перейдите в общий проект  
  
1.  Создайте проект VSIX C\# с именем **TestUniversalProject**. \(**Файл, создать, проект** и **пакет Visual Studio C\#, расширяемость,**\). Добавить **настраиваемой команды** шаблона элемента проекта \(в обозревателе решений щелкните правой кнопкой мыши узел проекта и выберите **Добавить\-новый элемент**, а затем перейдите к **расширения**\). Присвойте файлу имя **TestUniversalProject**.  
  
2.  Добавьте ссылку на Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll и Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll \(в **расширения** раздел\).  
  
3.  Откройте TestUniversalProject.cs и добавьте следующие `using` инструкции:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4.  В классе TestUniversalProject добавьте закрытое поле команды **вывода** окна.  
  
    ```c#  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Задайте ссылку на панели вывода внутри конструктора TestUniversalProject:  
  
    ```c#  
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
  
6.  Удалите существующий код из `ShowMessageBox` метод:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  Получите объект DTE, который мы будем использовать в различных целях в этом пошаговом руководстве. Кроме того убедитесь, что решение загружается при нажатии кнопки меню.  
  
    ```c#  
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
  
8.  Найти общий проект. Общий проект является чисто контейнера; не создавать и выдать выходные данные. Следующий метод находит первый общего проекта в решении, просматривая <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объект, имеющий возможность общего проекта.  
  
    ```c#  
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
  
9. В `ShowMessageBox` метод вывода заголовок \(имя проекта, которое отображается в **обозревателе решений**\) общего проекта.  
  
    ```c#  
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
  
10. Получение Платформа активного проекта. Проекты платформы, проекты, содержащие код платформы и ресурсы. Следующий метод использует новое поле <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> Платформа активного проекта.  
  
    ```c#  
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
  
11. В `ShowMessageBox` метод вывода заголовка Платформа активного проекта.  
  
    ```c#  
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
  
12. Выполните итерацию проекты платформы. Следующий метод получает Импорт проектов \(платформы\) из общего проекта.  
  
    ```c#  
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
    >  Если пользователь открыл проект универсального приложения Windows C\+\+ в экспериментальном экземпляре, приведенный выше код создает исключение. Это известная проблема. Чтобы избежать этого исключения, замените `foreach` Блокировать над следующим:  
  
    ```c#  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. В `ShowMessageBox` метод вывода Заголовок каждого проекта платформы. Вставьте следующий код после строки, которая выводит заголовок Платформа активного проекта. В этом списке отображаются только платформы проектов, загруженных.  
  
    ```c#  
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
  
14. Измените Платформа активного проекта. Задает следующий метод активного проекта с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
    ```c#  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. В `ShowMessageBox` метода, измените Платформа активного проекта. Вставьте этот код в `foreach` блок.  
  
    ```c#  
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
  
16. Теперь попробуйте все в деле. Нажмите клавишу F5, чтобы запустить экспериментальный экземпляр. Создайте проект приложения C\# универсальных концентратора в экспериментальном экземпляре \(в **Новый проект** диалоговом **Visual C\# \/ Windows и Windows 8 и универсальных и приложение\-концентратор**\). После загрузки решения, перейдите к **средства** меню и выберите пункт **вызова TestUniversalProject**, и затем ознакомьтесь с текстом **вывода** области. Вы увидите примерно следующее:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### Общие элементы в проекте платформы управления  
  
1.  Поиск общих элементов в проекте платформы. Элементы из общего проекта отображаются в проекте платформы как общие элементы. Не удается увидеть их в **Обозреватель решений**, но можно пройти иерархии проекта для их поиска. Следующий метод проходит иерархии и собирает все общие элементы. При необходимости он выводит заголовок каждого элемента. Общие элементы определяются новое свойство <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  
  
    ```c#  
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
  
2.  В `ShowMessageBox` метод, добавьте следующий код для обхода элементов иерархии платформы проекта. Вставьте его в `foreach` блок.  
  
    ```c#  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Чтение общих элементов. Общие элементы отображаются в проекте платформы как скрытые файлы, связанные, и можно прочитать все свойства как обычный связанные файлы. Следующий код считывает полный путь к общей первым.  
  
    ```c#  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Теперь попробуйте все в деле. Нажмите клавишу F5, чтобы запустить экспериментальный экземпляр. Создайте проект приложения C\# универсальных концентратора в экспериментальном экземпляре \(в **Новый проект** диалоговом **Visual C\# или Windows и Windows 8 и универсальных и приложение\-концентратор**\) перейдите на **средства** меню и выберите пункт **вызова TestUniversalProject**, и затем ознакомьтесь с текстом **Выходные данные** области. Вы увидите примерно следующее:  
  
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
  
### Обнаружение изменений в проекты платформы и общие проекты  
  
1.  Иерархии и проекта события можно использовать для обнаружения изменений в общих проектов, так же, как для проектов на платформах. Тем не менее элементы проекта в общем проекте не отображаются, это означает, что некоторые события не запускаются при изменении элементов общего проекта.  
  
     Рассмотрим последовательность событий при переименовании файла в проекте.  
  
    1.  Имя файла меняется на диске.  
  
    2.  Файл проекта обновляется с учетом нового имени файла.  
  
     Иерархии событий \(например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>\) обычно отслеживания изменений, отображаются в пользовательском Интерфейсе в виде **обозревателе решений**. Иерархии событий рекомендуется состоят из удаления файлов, а затем добавление файла операции переименования файла. Тем не менее, при изменении невидимые элементы иерархии система запускает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> событий, но не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> события. Таким образом, при переименовании файла в проекте платформы имеет оба <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, но при переименовании файла в общий проект, вы получите только <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  
  
     Для отслеживания изменений в элементах проекта, может обработать события элемента проекта DTE \(найти те в <xref:EnvDTE.ProjectItemsEventsClass>\). Тем не менее, если обрабатывается большое количество событий, можно получить более высокую производительность обработки событий в <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. В этом пошаговом руководстве мы покажем, как только иерархии события и события DTE. В этой процедуре добавить прослушиватель событий для общего проекта и платформы проекта. Затем при переименовании один файл в общем проекте и другой файл в проекте платформы, можно увидеть события, которые срабатывают для каждой операции переименования.  
  
     В этой процедуре добавить прослушиватель событий для общего проекта и платформы проекта. Затем при переименовании один файл в общем проекте и другой файл в проекте платформы, можно увидеть события, которые срабатывают для каждой операции переименования.  
  
2.  Добавьте прослушиватель событий. Добавьте новый файл класса в проект и назовите его HierarchyEventListener.cs.  
  
3.  Откройте файл HierarchyEventListener.cs и добавьте следующие операторы using:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  У `HierarchyEventListener` реализовать класс <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```c#  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  Реализовать члены <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, как показано в следующем примере кода.  
  
    ```c#  
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
  
6.  В том же классе добавьте другой обработчик событий для события DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, которая возникает при переименовании элемента проекта.  
  
    ```c#  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  Регистрируйтесь на мероприятиях иерархии. Необходимо зарегистрироваться отдельно для каждого проекта, в которой выполняется трассировка. Добавьте следующий код в `ShowMessageBox`, один для общего проекта, а другая — для одного или нескольких проектов платформы.  
  
    ```c#  
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
  
8.  Подписаться на событие элемента проекта DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Добавьте следующий код после подключить второй прослушивателя.  
  
    ```c#  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. Изменение общего элемента. Не удается изменить общие элементы в проекте платформы; Вместо этого необходимо изменить их в общий проект, который является действительным владельцем этих элементов. Можно получить идентификатор соответствующего элемента в общий проект с <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, что дает полный путь общего элемента. Затем можно изменить общий элемент. Изменение распространяется на проекты платформы.  
  
    > [!IMPORTANT]
    >  Вы должны докопаться ли элемент проекта является общий элемент перед его изменением.  
  
     Следующий метод изменяет имя файла элемента проекта.  
  
    ```c#  
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
  
10. Этот метод в конце концов код в `ShowMessageBox` Чтобы изменить имя файла элемента в общий проект. Вставьте следующий после кода, который возвращает полный путь к элементу в общий проект.  
  
    ```c#  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Постройте и запустите проект. Создайте приложение C\# универсальных концентратора в экспериментальном экземпляре, перейдите к **средства** меню и выберите пункт **вызова TestUniversalProject**, и ознакомьтесь с текстом в области Общие вывода. Имя первого элемента в общий проект \(мы надлежащим образом файл App.xaml\) должны изменяться, и вы увидите, <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> события. В этом случае так как переименование App.xaml приводит к App.xaml.cs также требуется переименовать, вы увидите четыре события \(два для каждого проекта платформы\). \(DTE события не отслеживать элементы из общего проекта\). Вы увидите два <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> событий \(по одному для каждого из проектов на платформах\), но не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> события.  
  
12. Теперь попробуйте переименовать файл в проекте платформы, и можно было увидеть разницу в события, которые вызвана. Добавьте следующий код в `ShowMessageBox` после вызова `ModifyFileName`.  
  
    ```c#  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. Постройте и запустите проект. Создание универсальных проекта C\# в экспериментальном экземпляре, перейдите к **средства** меню и выберите пункт **вызова TestUniversalProject**, и ознакомьтесь с текстом в области Общие вывода. После переименования файла в проекте платформы должны появиться оба <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> событий и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> события. С момента изменения файла вызвало никаких других файлов должен быть изменен, и поскольку изменения элементов в проекте платформы не распространяются в любом месте, то только одному из этих событий.