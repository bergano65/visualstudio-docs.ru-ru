---
title: Управление проектами универсальной Windows | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40d9a160d839b965c4b5f6db2413237af0af30ce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252815"
---
# <a name="managing-universal-windows-projects"></a>Управление универсальными проектами Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Универсальные приложения Windows, приложений, предназначенных для Windows 8.1 и Windows Phone 8.1, что позволяет разработчикам использовать код и другие ресурсы на обеих платформах. Общий код и ресурсы хранятся в общем проекте, хотя специфические для платформы код и ресурсы хранятся в разных проектах, один для Windows, а другой — для Windows Phone. Дополнительные сведения об универсальных приложениях Windows, см. в разделе [универсальных приложений Windows](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Расширения Visual Studio, которые управляют проекты следует иметь в виду, что проекты универсальных приложений для Windows имеют структуру, отличную от одной платформы приложений. В этом пошаговом руководстве показано, как для перемещения общего проекта и общие элементы управления.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="navigate-the-shared-project"></a>Перейдите в общий проект  
  
1.  Создайте проект VSIX C# с именем **TestUniversalProject**. (**Файл, создать, проект** и затем **пакет Visual Studio C#, расширяемость,**). Добавить **настраиваемой команды** шаблона элемента проекта (в обозревателе решений щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**, а затем перейдите к **расширяемости**). Назовите файл **TestUniversalProject**.  
  
2.  Добавьте ссылку на Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll и Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll (в **расширения** раздел).  
  
3.  Откройте TestUniversalProject.cs и добавьте следующий `using` инструкции:  
  
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
  
4.  В классе TestUniversalProject добавьте закрытое поле указывает на **вывода** окна.  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  Задайте ссылку на область вывода внутри конструктора TestUniversalProject:  
  
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
  
6.  Удалите существующий код из `ShowMessageBox` метод:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  Получает объект DTE, который будет использоваться для нескольких различных целей в этом пошаговом руководстве. Кроме того убедитесь, что решение загружено при нажатии кнопки меню.  
  
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
  
8.  Найти общий проект. Общий проект — это чисто контейнер; не создавать и создания выходных значений. Следующий метод находит первый общего проекта в решении, просматривая <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объект, имеющий возможность общего проекта.  
  
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
  
9. В `ShowMessageBox` метод, выходные данные заголовка (имя проекта, которое отображается в **обозревателе решений**) общего проекта.  
  
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
  
10. Получение активной платформы проекта. Проекты платформы — это проекты, содержащие код платформы и ресурсы. Следующий метод использует новое поле <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> для получения активной платформы проекта.  
  
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
  
11. В `ShowMessageBox` метод, выходные данные заголовка активной платформы проекта.  
  
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
  
12. Выполнить итерацию проекты платформы. Следующий метод получает все проекты (платформы), Импорт из общего проекта.  
  
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
    >  Если пользователь открыл проект C++ универсальной Windows приложение в экспериментальном экземпляре, приведенный выше код создает исключение. Это известная проблема. Чтобы избежать этого исключения, замените `foreach` блокировать над следующим:  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. В `ShowMessageBox` метод, выходные данные заголовка элемента проекта каждой платформы. Вставьте следующий код после строки, которая выводит заголовок активной платформы проекта. В этом списке отображаются только проекты платформы, которые будут загружены.  
  
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
  
14. Изменение активной платформы проекта. Следующий метод задает активного проекта с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. В `ShowMessageBox` метод, измените активной платформы проекта. Вставьте этот код в `foreach` блока.  
  
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
  
16. Теперь попробуйте все в деле. Нажмите клавишу F5, чтобы запустить экспериментальный экземпляр. Создайте проект приложения универсальной концентратора C# в экспериментальном экземпляре (в **новый проект** диалоговом окне **Visual C# / Windows / Windows 8 / универсальной / приложение центра**). После загрузки решения, перейдите к **средства** меню и выберите пункт **вызова TestUniversalProject**, а затем проверить текст в **выходные данные** области. Вы должны увидеть примерно следующее:  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>Управление общих элементов в проект платформы  
  
1.  Найти общие элементы в проект платформы. Элементы в общем проекте появляются в проекте платформы как общие элементы. Не удается увидеть их в **обозревателе решений**, но вы можете потренироваться иерархии проекта, чтобы найти их. Следующий метод проходит по иерархии и собирает все общие элементы. При необходимости он выводит заголовок каждого элемента. Общие элементы идентифицируются по новому свойству <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>.  
  
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
  
2.  В `ShowMessageBox` метод, добавьте следующий код для обхода элементов платформы проекта иерархии. Вставить его внутри `foreach` блока.  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  Чтение общих элементов. Общие элементы отображаются в проекте платформы как скрытый связанные файлы, а вы найдете все свойства, как обычные связанные файлы. Следующий код считывает полный путь к первый общий элемент.  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  Теперь попробуйте все в деле. Нажмите клавишу F5, чтобы запустить экспериментальный экземпляр. Создайте проект приложения универсальной концентратора C# в экспериментальном экземпляре (в **новый проект** диалоговом окне **Visual C# / Windows / Windows 8 / универсальной / приложение центра**) перейдите к **средства** меню и выберите пункт **вызова TestUniversalProject**, а затем проверить текст в **выходные данные** области. Вы должны увидеть примерно следующее:  
  
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
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>Обнаружение изменений в проектах платформы и общие проекты  
  
1.  Иерархии и проекта события можно использовать для обнаружения изменений в общих проектов, так же, как для платформы проектов. Тем не менее элементы проекта в общем проекте не отображаются, это означает, что некоторые события не срабатывают при изменении элементов в общем проекте.  
  
     Рассмотрим последовательность событий при переименовании файла в проекте:  
  
    1.  Имя файла изменяется на диске.  
  
    2.  Файл проекта обновляется с учетом нового имени файла.  
  
     События иерархии (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) обычно отслеживания изменений, отображаемый в пользовательском Интерфейсе, как показано на **обозревателе решений**. События иерархии рассмотрим операции переименования файла, состоящий из удаление файлов, а затем добавление файла. Тем не менее, при изменении невидимые элементы иерархии система запускает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> событий, но не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> событий. Таким образом, при переименовании файла в проекте платформы, вы получаете оба <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, но при переименовании файла в общий проект, вы получаете только <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.  
  
     Для отслеживания изменений в элементах проекта, можно обрабатывать события элемента проекта DTE (те из них см. в <xref:EnvDTE.ProjectItemsEventsClass>). Тем не менее, если обрабатывается большое количество событий, можно получить более высокую производительность, обработка событий в <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. В этом пошаговом руководстве мы покажем, как только иерархии события и события DTE. В этой процедуре Добавление прослушивателя событий для общего проекта и платформу проекта. Затем при переименовании один файл в общем проекте и другой файл в проекте платформы, вы увидите события, инициируемые для каждой операции переименования.  
  
     В этой процедуре Добавление прослушивателя событий для общего проекта и платформу проекта. Затем при переименовании один файл в общем проекте и другой файл в проекте платформы, вы увидите события, инициируемые для каждой операции переименования.  
  
2.  Добавление прослушивателя событий. Добавьте новый файл класса в проект и назовите его HierarchyEventListener.cs.  
  
3.  Откройте файл HierarchyEventListener.cs и добавьте следующие операторы using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  У `HierarchyEventListener` Реализуйте класс <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```csharp  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  Реализовать члены <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, как показано в приведенном ниже коде.  
  
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
  
6.  В этом же классе добавляться другой обработчик событий для события DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, который возникает при переименовании элемента проекта.  
  
    ```csharp  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  Подписаться на события иерархии. Вам нужно зарегистрироваться отдельно для каждого проекта, в которой выполняется трассировка. Добавьте следующий код в `ShowMessageBox`, один для общего проекта, а другой — для одного из проектов платформы.  
  
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
  
8.  Зарегистрируйтесь для события элемента проекта DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Добавьте следующий код после подключить второго прослушивателя.  
  
    ```csharp  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. Изменение общего элемента. Нельзя изменять общие элементы в проекте платформы; Вместо этого необходимо изменить их в общий проект, который является действительным владельцем этих элементов. Можно получить идентификатор соответствующего элемента в общем проекте с <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, предоставляя ему полный путь для общего элемента. Затем можно изменить общий элемент. Изменение распространяется на проекты платформы.  
  
    > [!IMPORTANT]
    >  Вы должны докопаться ли элемент проекта является общий элемент перед внесением изменений.  
  
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
  
10. Вызовите этот метод в конце концов другой код в `ShowMessageBox` изменить имя файла элемента в общем проекте. Вставьте это после кода, который получает полный путь элемента в общем проекте.  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. Постройте и запустите проект. Создать приложение универсальной центра C# в экспериментальном экземпляре, перейдите к **средства** меню и выберите пункт **вызова TestUniversalProject**и ознакомьтесь с текстом в общей области вывода. Имя первого элемента в общий проект (ожидается, что его в файл App.xaml) следует изменить, и вы увидите, что <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> события. В этом случае так как переименование App.xaml приводит к App.xaml.cs, который требуется переименовать, а также, вы увидите четыре события (два для каждого проекта платформы). (DTE события не отслеживать элементы в общем проекте.) Должны отобразиться два <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> события (по одному для каждого проекта платформы), но не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> события.  
  
12. Теперь попробуйте переименовать файл в проект платформы, и можно было увидеть разницу в событиях получить триггерами. Добавьте следующий код в `ShowMessageBox` после вызова `ModifyFileName`.  
  
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
  
13. Постройте и запустите проект. Создание универсального проекта C# в экспериментальном экземпляре, перейдите к **средства** меню и выберите пункт **вызова TestUniversalProject**и ознакомьтесь с текстом в общей области вывода. После переименования файла в проект платформы, вы увидите оба <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> событий и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> событий. Так как файл вызвало никаких других файлов, которые необходимо изменить, и поскольку изменения элементов в проекте платформы не распространяются в любом месте, то только по одной из этих событий.

