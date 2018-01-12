---
title: "Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2 | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: f0472688f9f36d2b14c89cc904bf6ce4badd6ca6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2"></a>Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2
  После определения пользовательского типа элемента проекта SharePoint и свяжите его с шаблоном проекта в Visual Studio, можно также создать мастер для шаблона. Мастер можно использовать для сбора информации от пользователей, при использовании шаблона для создания нового проекта, содержащего элемент проекта. Собранные сведения могут использоваться для инициализации элемента проекта.  
  
 В этом пошаговом руководстве вы добавите мастер в шаблон проекта столбца сайта, представленный в [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Когда пользователь создает проект столбца сайта, мастер собирает сведения о столбце сайта (например, базовый тип и группу) и добавляет их в файл Elements.xml в новом проекте.  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание мастера для настраиваемого типа элемента проекта SharePoint, который связан с шаблоном проекта.  
  
-   Определение настраиваемого мастера пользовательского интерфейса, похожего на встроенный мастер для проектов SharePoint в Visual Studio.  
  
-   Создание двух *команды SharePoint* , которые используются для вызова локального сайта SharePoint пока запущен мастер. Команды SharePoint, методы, которые могут использоваться расширения Visual Studio для вызова API в серверной объектной модели SharePoint. Дополнительные сведения см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Использование подстановочных параметров для инициализации файлов проекта SharePoint с данными, собранными в мастере.  
  
-   Создание нового SNK-файл в каждый новый экземпляр проекта столбца сайта. Этот файл используется для подписания выходных данных, чтобы сборка решения SharePoint могут развертываться в глобальном кэше сборок проекта.  
  
-   Отладка и тестирование мастера.  
  
> [!NOTE]  
>  Вы можете загрузить пример, содержащий завершенные проекты, код и другие файлы для этого пошагового руководства из следующего расположения: [http://go.microsoft.com/fwlink/?LinkId=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства, необходимо сначала создать решение SiteColumnProjectItem, выполнив [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Также необходимы следующие компоненты на компьютере разработчика для выполнения данного пошагового руководства:  
  
-   Поддерживаемые версии Windows, SharePoint и Visual Studio. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. В этом пошаговом руководстве используется **проект VSIX** шаблона в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. в разделе [расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Изучением приведенных ниже концепций будет полезно, хотя и не требуется для выполнения данного пошагового руководства.  
  
-   Мастеров для шаблонов проектов и элементов в Visual Studio. Дополнительные сведения см. в разделе [как: использование мастеров шаблонов проекта](../extensibility/how-to-use-wizards-with-project-templates.md) и <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейса.  
  
-   Столбцы сайта SharePoint. Дополнительные сведения см. в разделе [столбцы](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
##  <a name="wizardcomponents"></a>Основные сведения о компонентах мастера  
 Мастер, представленный в этом пошаговом руководстве, содержит несколько компонентов. В следующей таблице описаны эти компоненты.  
  
|Компонент|Описание:|  
|---------------|-----------------|  
|Реализация мастера|Это класс, с именем `SiteColumnProjectWizard`, который реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейса. Этот интерфейс определяет методы, вызываемые Visual Studio при запуске мастера и завершения и в определенные моменты при мастер выполняет.|  
|Пользовательский Интерфейс мастера|Это окно на основе WPF, с именем `WizardWindow`. В этом окне включает два элемента управления пользователя, с именем `Page1` и `Page2`. Эти пользовательские элементы управления представляют две страницы мастера.<br /><br /> В этом пошаговом руководстве <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> метод реализации мастер отображает пользовательский Интерфейс мастера.|  
|Мастер модели данных|Это промежуточный класс с именем `SiteColumnWizardModel`, который образует логический уровень между пользовательским Интерфейсом мастера и реализацией мастера. Этот образец использует этот класс для внедрения абстракции между реализацией мастера и пользовательский Интерфейс мастера друг от друга; Этот класс не является обязательным компонентом для всех мастеров.<br /><br /> В этом пошаговом руководстве реализация мастера передает `SiteColumnWizardModel` объект в окно мастера, при отображении пользовательского интерфейса мастера. Пользовательский Интерфейс мастера использует методы этого объекта для сохранения значений элементов управления в пользовательском Интерфейсе и задачи, такие как проверка того, допустимость введенного URL-адреса. По окончании работы мастера, реализация мастер использует `SiteColumnWizardModel` объектом, чтобы определить конечное состояние пользовательского интерфейса.|  
|Подписи руководителя проекта|Это вспомогательный класс с именем `ProjectSigningManager`, который используется для реализации мастера для создания нового файла key.snk в каждый новый экземпляр проекта.|  
|команды SharePoint|Это методы, используемые моделью данных мастера для вызова локального сайта SharePoint пока запущен мастер. Поскольку команды SharePoint должны быть предназначены для .NET Framework 3.5, эти команды выполняются в сборке, отдельной от остального кода мастера.|  
  
## <a name="creating-the-projects"></a>Создание проектов  
 Для выполнения данного пошагового руководства, необходимо добавить несколько проектов в решение SiteColumnProjectItem, который был создан в [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
-   Проект WPF. Следует реализовать <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс и определить пользовательский Интерфейс мастера в этом проекте.  
  
-   Проект библиотеки классов, определяющий команды SharePoint. Этот проект должен использовать.NET Framework 3.5.  
  
 Пошаговое руководство начинается с создания проектов.  
  
#### <a name="to-create-the-wpf-project"></a>Создание проекта WPF  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение SiteColumnProjectItem.  
  
2.  В **обозревателе решений**, откройте контекстное меню для **SiteColumnProjectItem** узел решения, выберите **добавить**и нажмите кнопку **новый проект**.  
  
3.  В верхней части **Добавление нового проекта** диалогового окна поле, убедитесь, что **.NET Framework 4.5** выбирается в списке версий .NET Framework.  
  
4.  Разверните **Visual C#** узел или **Visual Basic** узел и выберите **Windows** узла.  
  
5.  В списке шаблонов проектов выберите **Библиотека пользовательских элементов управления WPF**, назовите проект **ProjectTemplateWizard**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Добавляет **ProjectTemplateWizard** проекта в решение и откроет файл UserControl1.xaml по умолчанию.  
  
6.  Удалите файл UserControl1.xaml из проекта.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Чтобы создать проект команды SharePoint  
  
1.  В **обозревателе решений**откройте контекстное меню узла решения SiteColumnProjectItem, выберите **добавить**и нажмите кнопку **новый проект**.  
  
2.  В верхней части **Добавление нового проекта** диалогового окна выберите **.NET Framework 3.5** в списке версий .NET Framework.  
  
3.  Разверните **Visual C#** узел или **Visual Basic** узел и выберите **Windows** узла.  
  
4.  Выберите **библиотеки классов** шаблон проекта, присвойте проекту имя **SharePointCommands**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Добавляет **SharePointCommands** в решение проект и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
## <a name="configuring-the-projects"></a>Настройка проектов  
 Перед созданием мастера необходимо добавить некоторые файлы кода и ссылок на сборки в проектах.  
  
#### <a name="to-configure-the-wizard-project"></a>Настройка проекта мастера  
  
1.  В **обозревателе решений**, откройте контекстное меню для **ProjectTemplateWizard** узел проекта, а затем выберите **свойства**.  
  
2.  В **конструктора проектов**, выберите **приложения** вкладку в проекте Visual C# или **компиляции** вкладки для проекта Visual Basic.  
  
3.  Убедитесь, что требуемая версия .NET framework имеет значение .NET Framework 4.5, не 4.5 клиентский профиль .NET Framework.  
  
     Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Откройте контекстное меню для **ProjectTemplateWizard** проекта, выбор **добавить**, а затем выберите **новый элемент**.  
  
5.  Выберите **Window (WPF)** товара, имя элемента **WizardWindow**, а затем выберите **добавить** кнопки.  
  
6.  Добавление двух **пользовательский элемент управления (WPF)** элементов в проект и назовите их **Page1** и **страница 2**.  
  
7.  Добавьте четыре файла кода в проект и предоставьте им следующие имена:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   Идентификаторы команд CommandIds  
  
8.  Откройте контекстное меню для **ProjectTemplateWizard** узел проекта, а затем выберите **добавить ссылку**.  
  
9. Разверните **сборки** узел, выберите **расширения** узел, а затем выберите флажки для следующих сборок:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Выберите **ОК** кнопку, чтобы добавить сборки в проект.  
  
11. В **обозревателе решений**в разделе **ссылки** папку для **ProjectTemplateWizard** проекта, выбор **EnvDTE**.  
  
12. В **свойства** окна, измените значение **внедрить типы взаимодействия** свойства **False**.  
  
13. Если вы разрабатываете проект Visual Basic, ProjectTemplateWizard пространство имен импортировано в проект с помощью **конструктора проектов**.  
  
     Дополнительные сведения см. в разделе [как: Добавление или удаление Импортируемые пространства имен &#40; Visual Basic &#41; ](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Чтобы настроить проект SharePointCommands  
  
1.  В **обозревателе решений**, выберите **SharePointCommands** узел проекта.  
  
2.  В строке меню выберите **проекта**, **Добавление существующего элемента**.  
  
3.  В **Добавление существующего элемента** диалоговое окно, перейдите к папке, в которой содержатся файлы кода для проекта ProjectTemplateWizard и выберите **идентификаторы команд CommandIds** файл кода.  
  
4.  Щелкните стрелку рядом с **добавить** , а затем кнопку **ссылку Добавить** в появившемся меню.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Добавление файла кода для **SharePointCommands** проект в качестве связи. Файл кода находится в **ProjectTemplateWizard** также скомпилирована в проект, но код в файле **SharePointCommands** проекта.  
  
5.  В **SharePointCommands** проект, добавить другой файл кода с именем команды.  
  
6.  Выберите проект SharePointCommands, а затем в строке меню выберите **проекта**, **добавить ссылку**.  
  
7.  Разверните **сборки** узел, выберите **расширения** узел, а затем выберите флажки для следующих сборок:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Выберите **ОК** кнопку, чтобы добавить сборки в проект.  
  
## <a name="creating-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Создание модели мастера, диспетчера подписания и идентификаторов команд SharePoint  
 Добавьте код в проект ProjectTemplateWizard, чтобы установить следующие компоненты в образце:  
  
-   Идентификаторы команд SharePoint. Эти строки идентификации команды SharePoint, используемые мастером. Далее в этом пошаговом руководстве вы добавите код в проект SharePointCommands для реализации этих команд.  
  
-   Модель данных мастера.  
  
-   Диспетчер подписания проекта.  
  
 Дополнительные сведения об этих компонентах см. в разделе [основные сведения о компонентах мастера](#wizardcomponents).  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>Для определения идентификаторов команд SharePoint  
  
1.  В проекте ProjectTemplateWizard откройте файл кода идентификаторы команд CommandIds и затем замените все содержимое этого файла следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>Для создания модели мастер  
  
1.  Откройте файл кода SiteColumnWizardModel и замените все содержимое этого файла следующим кодом.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>Для создания подписи руководителя проекта  
  
1.  Откройте файл кода ProjectSigningManager и замените все содержимое этого файла следующим кодом.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="creating-the-wizard-ui"></a>Создание пользовательского интерфейса мастера  
 Добавьте код XAML для определения пользовательского интерфейса окна мастера и два пользовательских элементов управления, которые предоставляют пользовательский Интерфейс для страниц мастера и добавьте код для определения поведения окна и пользовательских элементов управления. Мастер, который вы создаете напоминает встроенный мастер для проектов SharePoint в Visual Studio.  
  
> [!NOTE]  
>  В следующих шагах проект будет содержать ошибки компиляции, после добавления XAML-кода в проект. Эти ошибки исчезнут при добавлении кода в последующих шагах.  
  
#### <a name="to-create-the-wizard-window-ui"></a>Для создания пользовательского интерфейса окна мастера  
  
1.  В проекте ProjectTemplateWizard, откройте контекстное меню для файла WizardWindow.xaml и выберите **откройте** Открытие окна в конструкторе.  
  
2.  В представлении XAML в конструкторе замените текущий XAML следующим кодом XAML. Этот код XAML определяет пользовательский Интерфейс, содержащий заголовок, <xref:System.Windows.Controls.Grid> , содержащий страницы мастера, и кнопки навигации в нижней части окна.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  Окна, созданную в этот код XAML является производным от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> базового класса. При добавлении настраиваемого поля диалогового окна WPF в Visual Studio, мы рекомендуем, диалогового окна производными этого класса стилей согласованное с другими диалоговыми окнами Visual Studio и избежать проблем модальное диалоговое окно, в противном случае может произойти. Дополнительные сведения см. в разделе [Создание и управление модальные диалоговые окна](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Если вы разрабатываете проект Visual Basic, удалите `ProjectTemplateWizard` пространства имен из `WizardWindow` имя класса в `x:Class` атрибут `Window` элемента. Этот элемент находится в первой строке кода XAML. После завершения, первая строка должна выглядеть как в следующем примере.  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Откройте файл кода для файла WizardWindow.xaml.  
  
5.  Замените содержимое этого файла, за исключением `using` объявления в верхней части файла, следующим кодом.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>Создание пользовательского интерфейса первой страницы мастера  
  
1.  В проекте ProjectTemplateWizard, откройте контекстное меню для файла Page1.xaml и выберите **откройте** Открытие пользовательского элемента управления в конструкторе.  
  
2.  В представлении XAML в конструкторе замените текущий XAML следующим кодом XAML. Этот код XAML определяет пользовательский Интерфейс, который содержит текстовое поле для ввода URL-адреса локальных сайтов, которые они хотят использовать для отладки. Пользовательский Интерфейс также переключателей, с помощью которого пользователи могут указать способ изолированного.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  Если вы разрабатываете проект Visual Basic, удалите `ProjectTemplateWizard` пространства имен из `Page1` имя класса в `x:Class` атрибут `UserControl` элемента. Это в первой строке кода XAML. Когда закончите, первая строка должна выглядеть следующим образом.  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Замените содержимое файла Page1.xaml, за исключением `using` объявления в верхней части файла, следующим кодом.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>Создание пользовательского интерфейса второй страницы мастера  
  
1.  В проекте ProjectTemplateWizard, откройте контекстное меню для файла Page2.xaml и выберите **откройте**.  
  
     Пользовательский элемент управления откроется в конструкторе.  
  
2.  В представлении XAML замените текущий XAML следующим кодом XAML. Этот код XAML определяет пользовательский Интерфейс, который включает в себя раскрывающегося списка для выбора базового типа столбца сайта, поле со списком для указания встроенной или настраиваемой группы, к которой отображается столбец сайта в галерее и текстовое поле для указания имени столбца сайта.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  Если вы разрабатываете проект Visual Basic, удалите `ProjectTemplateWizard` пространства имен из `Page2` имя класса в `x:Class` атрибут `UserControl` элемента. Это в первой строке кода XAML. Когда закончите, первая строка должна выглядеть следующим образом.  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Замените содержимое файла кода для файла Page2.xaml, за исключением `using` объявления в верхней части файла, следующим кодом.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implementing-the-wizard"></a>Реализация мастера  
 Определите основную функциональность мастера, реализовав <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейса. Этот интерфейс определяет методы, вызываемые Visual Studio при запуске мастера и завершения и в определенные моменты при мастер выполняет.  
  
#### <a name="to-implement-the-wizard"></a>Реализация мастера  
  
1.  В проекте ProjectTemplateWizard откройте файл кода SiteColumnProjectWizard.  
  
2.  Замените все содержимое этого файла следующим кодом.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="creating-the-sharepoint-commands"></a>Создание команды SharePoint  
 Создание двух пользовательских команд, которые вызывают объектную модель сервера SharePoint. Одна команда определяет, является ли допустимым URL-адрес сайта, введенная пользователем в мастере. Другая команда получает все типы полей из указанного сайта SharePoint, чтобы пользователи могли выбирать какой из них следует использовать в качестве основы для новый столбец сайта.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Для определения команды SharePoint  
  
1.  В **SharePointCommands** проекта, откройте файл кода команды.  
  
2.  Замените все содержимое этого файла следующим кодом.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>Контрольная точка  
 На этом этапе в пошаговом руководстве, весь код мастер теперь находится в проекте. Постройте проект, чтобы убедиться в том, что оно компилируется без ошибок.  
  
#### <a name="to-build-your-project"></a>Построение проекта  
  
1.  В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>Удаление файла key.snk из шаблона проекта  
 В [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), созданный вами шаблон проекта содержит файл key.snk, используемый для подписания каждого экземпляра проекта столбца сайта. Файл key.snk больше не требуется, так как теперь мастер создает файл key.snk для каждого проекта. Удалите файл key.snk из шаблона проекта и ссылки на этот файл.  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Чтобы удалить файл key.snk из шаблона проекта  
  
1.  В **обозревателе решений**в разделе **SiteColumnProjectTemplate** узел, откройте контекстное меню для **key.snk** файлу и нажмите кнопку **удаление**.  
  
2.  В диалоговом окне подтверждения выберите **ОК** кнопки.  
  
3.  В разделе **SiteColumnProjectTemplate** узел, откройте файл SiteColumnProjectTemplate.vstemplate и удалите следующий элемент из него.  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Сохраните и закройте файл.  
  
5.  В разделе **SiteColumnProjectTemplate** узел, откройте файл ProjectTemplate.csproj или ProjectTemplate.vbproj, а затем удалите следующие `PropertyGroup` элемент из него.  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  Удалите следующий `None` элемента.  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  Сохраните и закройте файл.  
  
## <a name="associating-the-wizard-with-the-project-template"></a>Привязка с использованием шаблона проекта мастера  
 Теперь, когда реализации мастера необходимо привязать мастер с **столбец сайта** шаблона проекта. Существует три процедуры, которые необходимо выполнить для этого:  
  
1.  Подпишите сборку строгим именем мастера.  
  
2.  Получите токен открытого ключа для сборки мастера.  
  
3.  Добавьте ссылку в сборку мастера в VSTEMPLATE-файле **столбец сайта** шаблона проекта.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Для подписи сборки строгим именем мастера  
  
1.  В **обозревателе решений**, откройте контекстное меню для **ProjectTemplateWizard** проекта, а затем выберите **свойства**.  
  
2.  На **подписывание** выберите **подписать сборку** флажок.  
  
3.  В **выберите файл ключей строгого имени** выберите  **\<создать... >**.  
  
4.  В **Создание ключа строгого имени** диалогового окна введите имя для нового файла ключа снимите **защитить мой файл ключей паролем** флажок и нажмите кнопку **ОК** кнопки.  
  
5.  Откройте контекстное меню для **ProjectTemplateWizard** проекта, а затем выберите **построения** для создания файла ProjectTemplateWizard.dll.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Чтобы получить токен открытого ключа для сборки мастера  
  
1.  На **меню "Пуск"**, выберите **все программы**, выберите **Microsoft Visual Studio**, выберите **набора средств Visual Studio**, а затем выберите  **Командная строка разработчика**.  
  
     Откроется окно командной строки Visual Studio.  
  
2.  Выполните следующую команду, заменив *PathToWizardAssembly* с указанием полного пути к сборке ProjectTemplateWizard.dll ProjectTemplateWizard проекта на компьютере разработчика:  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Токен открытого ключа сборки ProjectTemplateWizard.dll записывается в окно командной строки Visual Studio.  
  
3.  Не закрывайте окно командной строки Visual Studio. Токен открытого ключа потребуются для следующей процедуры.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Чтобы добавить ссылку на сборку мастера в VSTEMPLATE-файл  
  
1.  В **обозревателе решений**, разверните **SiteColumnProjectTemplate** узел проекта и откройте файл SiteColumnProjectTemplate.vstemplate.  
  
2.  В конце файла добавьте следующие `WizardExtension` элемент между `</TemplateContent>` и `</VSTemplate>` тегов. Замените *ваш токен* значение `PublicKeyToken` атрибута с токен открытого ключа, полученное в предыдущей процедуре.  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Дополнительные сведения о `WizardExtension` элемент, в разделе [элемент WizardExtension &#40; Шаблоны Visual Studio &#41; ](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Сохраните и закройте файл.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Добавление подстановочных параметров в файл Elements.xml в шаблоне проекта  
 Добавьте несколько подстановочных параметров в файл Elements.xml в проект SiteColumnProjectTemplate. Эти параметры инициализируются `RunStarted` метод `SiteColumnProjectWizard` класса, которое было определено ранее. Когда пользователь создает проект столбца сайта, Visual Studio автоматически заменяет эти параметры в файл Elements.xml в новом проекте со значениями, указанными в мастере.  
  
 Заменяемый параметр представляет маркер, который начинается и заканчивается символом доллара ($). Кроме определения собственных подстановочные параметры, можно использовать встроенные параметры, которые определены и инициализированы системой проектов SharePoint. Дополнительные сведения см. в разделе [подстановочные параметры](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Чтобы добавить в файл Elements.xml подстановочные параметры  
  
1.  В проекте SiteColumnProjectTemplate Замените содержимое файла Elements.xml следующий XML-код.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     Новый XML-код изменяет значения `Name`, `DisplayName`, `Type`, и `Group` атрибуты настраиваемыми подстановочными параметрами.  
  
2.  Сохраните и закройте файл.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Мастер добавления пакета VSIX  
 Чтобы развернуть пакет VSIX, который содержит шаблон проекта столбца сайта в мастере, добавьте ссылки на проект мастера и проект команды SharePoint файл source.extension.vsixmanifest в проекте VSIX.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Чтобы добавить мастер пакета VSIX  
  
1.  В **обозревателе решений**в **SiteColumnProjectItem** проекта, откройте контекстное меню для **source.extension.vsixmanifest** файл, а затем выберите **Открыть**.  
  
     Visual Studio открывает файл в редакторе манифестов.  
  
2.  На **активы** вкладка редактора выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
3.  В **тип** выберите **Microsoft.VisualStudio.Assembly**.  
  
4.  В **источника** выберите **проект в текущем решении**.  
  
5.  В **проекта** выберите **ProjectTemplateWizard**, а затем выберите **ОК** кнопки.  
  
6.  На **активы** вкладка редактора выберите **New** еще раз.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
7.  В **тип** введите **SharePoint.Commands.v4**.  
  
8.  В **источника** выберите **проект в текущем решении**.  
  
9. В **проекта** выберите **SharePointCommands** проекта, а затем выберите **ОК** кнопки.  
  
10. В строке меню выберите **построения**, **построить решение**, а затем убедитесь, что сборка решения выполняется без ошибок.  
  
## <a name="testing-the-wizard"></a>Тестирование мастера  
 Теперь все готово для тестирования мастера. Начните отладку решение SiteColumnProjectItem в экспериментальном экземпляре Visual Studio. Затем протестируйте мастер для проекта столбца сайта в экспериментальном экземпляре Visual Studio. Наконец Постройте и запустите проект, чтобы проверить, что столбец сайта работает должным образом.  
  
#### <a name="to-start-debugging-the-solution"></a>Чтобы начать отладку решения  
  
1.  Перезапустите Visual Studio с правами администратора и откройте решение SiteColumnProjectItem.  
  
2.  В проекте ProjectTemplateWizard, откройте файл кода SiteColumnProjectWizard и затем добавьте точку останова в первой строке кода в `RunStarted` метод.  
  
3.  В строке меню выберите **отладки**, **исключения**.  
  
4.  В **исключения** диалогового окна поле, убедитесь, что **вызванное** и **пользовательским кодом** флажки для **исключения среды CLR**очищаются, а затем выберите **ОК** кнопки.  
  
5.  Начать отладку, выбрав **F5** ключа или выберите в строке меню, выберите **отладки**, **начать отладку**.  
  
     Visual Studio устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 и запуске экспериментального экземпляра Visual Studio. В этом экземпляре Visual Studio, вы сможете протестировать элемент проекта.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Чтобы проверить мастер в Visual Studio  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **файл**, **New**, **проекта**.  
  
2.  Разверните **Visual C#** узел или **Visual Basic** развернуть узел (в зависимости от языка, поддерживаемого шаблоном проекта), **SharePoint** узел и нажмите кнопку **2010** узла.  
  
3.  В списке шаблонов проектов выберите **столбец сайта**, присвойте проекту имя **SiteColumnWizardTest**, а затем выберите **ОК** кнопки.  
  
4.  Убедитесь, что код в другом экземпляре Visual Studio прервано на точке останова, заданной ранее в `RunStarted` метод.  
  
5.  Продолжить отладку проекта, выбрав **F5** ключа или выберите в строке меню, выберите **отладки**, **Продолжить**.  
  
6.  В **мастер настройки SharePoint**, введите URL-адрес сайта, который требуется использовать для отладки и нажмите кнопку **Далее** кнопки.  
  
7.  На второй странице **мастер настройки SharePoint**, задайте следующие параметры:  
  
    -   В **тип** выберите **логическое**.  
  
    -   В **группы** выберите **Yes/No настраиваемые столбцы**.  
  
    -   В **имя** введите **Мой столбец**, а затем выберите **Готово** кнопки.  
  
     В **обозревателе решений**, появится новый проект и содержит элемент проекта с именем **Field1**, и Visual Studio открывает файл Elements.xml проекта в редакторе.  
  
8.  Убедитесь, что файл Elements.xml содержит значения, которые указаны в мастере.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Чтобы проверить столбец сайта в SharePoint  
  
1.  В экспериментальном экземпляре Visual Studio нажмите клавишу F5.  
  
     Столбец сайта упаковывается и развернуты в SharePoint сайта, **URL-адрес сайта** указывает свойство проекта. Веб-браузере откроется страница по умолчанию этого сайта.  
  
    > [!NOTE]  
    >  Если **отладка скриптов отключена** диалоговое окно, выберите **Да** кнопку, чтобы продолжить отладку проекта.  
  
2.  На **действия сайта** меню, выберите **параметры сайта**.  
  
3.  На странице «Параметры сайта» в разделе **галерей**, выберите **столбцы сайта** ссылку.  
  
4.  В списке столбцов сайта, убедитесь, что **настраиваемые столбцы Yes/No** группа содержит столбец с именем **Мой столбец**, а затем закройте веб-браузер.  
  
## <a name="cleaning-up-the-development-computer"></a>Очистка компьютера разработчика  
 После завершения тестирования элемента проекта удалите шаблон проекта из экспериментального экземпляра Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Очистка компьютера разработчика  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **средства**, **расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В списке расширений выберите **столбец сайта**и нажмите кнопку **удаления** кнопки.  
  
3.  В появившемся диалоговом окне, выберите **Да** кнопку, чтобы убедиться, что вы хотите удалить расширение, а затем выберите **Перезагрузить сейчас** кнопку, чтобы завершить удаление.  
  
4.  Закройте экспериментальный экземпляр Visual Studio и экземпляр, в котором открыт решение CustomActionProjectItem.  
  
     Дополнительные сведения о развертывании [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] расширения, в разделе [доставки расширений Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Определение типов элементов проектов SharePoint, пользовательские](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Справочник по схеме шаблонов Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Практическое руководство. Использование мастеров для шаблонов проекта](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
  