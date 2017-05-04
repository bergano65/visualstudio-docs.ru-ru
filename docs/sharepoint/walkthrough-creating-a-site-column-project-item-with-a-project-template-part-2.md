---
title: "Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элементы проекта [разработка приложений SharePoint в Visual Studio], создание мастеров шаблонов"
  - "Элементы проекта SharePoint, создание мастеров шаблонов"
  - "разработка приложений SharePoint в Visual Studio, определение новых типов элементов проектов"
ms.assetid: da14207d-ac09-41ba-b387-c7f881b2a366
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2
  После того как пользовательский тип элемента проекта SharePoint определен и связан с шаблоном проекта в Visual Studio, имеет смысл также создать мастер для шаблона.  С помощью мастера можно запрашивать информацию у пользователя при создания нового проекта, содержащего элемент проекта, с помощью этого шаблона.  Собранные сведения могут быть использованы для инициализации элемента проекта.  
  
 В данном пошаговом руководстве рассматривается добавление мастера в шаблон проекта столбца сайта, представленный в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  Когда пользователь создает проект столбца сайта, мастер собирает сведения об этом столбце \(например, его базовый тип и группу\) и добавляет их в файл Elements.xml в новом проекте.  
  
 В этом пошаговом руководстве показано выполнение следующих задач.  
  
-   Создание мастера для настраиваемого типа элемента проекта SharePoint, связанного с шаблоном проекта.  
  
-   Определение настраиваемого пользовательского интерфейса мастера, похожего на встроенный мастер для проектов SharePoint в Visual Studio.  
  
-   Создание двух *команд SharePoint*, используемых для вызова локального сайта SharePoint во время выполнения мастера.  Команды SharePoint представляют собой методы, используемые расширениями Visual Studio для вызова API серверной объектной модели SharePoint.  Для получения дополнительной информации см. [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Использование подстановочных параметров для инициализации файлов проекта SharePoint с данными, собранными мастером.  
  
-   Создание нового SNK\-файла в каждом новом экземпляре проекта столбца сайта.  Этот файл используется для подписания выходных данных проекта, чтобы сборку решения SharePoint можно было развернуть в глобальном кэше сборок.  
  
-   Отладка и тестирование мастера.  
  
> [!NOTE]  
>  Можно загрузить пример, который содержит проекты завершена, код и другие файлы для этого пошагового руководства из следующего расположения:  [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Обязательные компоненты  
 Для выполнения этого пошагового руководства необходимо сначала создать решение SiteColumnProjectItem, указания из раздела [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Также для выполнения данного пошагового руководства на компьютере разработчика должны быть установлены следующие компоненты.  
  
-   Поддерживаемые выпуски Windows, SharePoint и Visual Studio.  Для получения дополнительной информации см. [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Пакет SDK для Visual Studio.  В этом пошаговом руководстве шаблон **Проект VSIX** из пакета SDK используется для создания пакета VSIX, который служит для развертывания элемента проекта.  Для получения дополнительной информации см. [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Знание следующих подходов может оказаться полезным, но не требуется для выполнения пошагового руководства.  
  
-   Мастера для проектов и шаблонов элементов в Visual Studio.  Дополнительные сведения см. в разделе [Практическое руководство. Использование мастеров для шаблонов проекта](~/extensibility/how-to-use-wizards-with-project-templates.md) и в документации на интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
-   Столбцы сайтов в SharePoint.  Дополнительные сведения см. в [Столбцы](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
##  <a name="wizardcomponents"></a> Общие сведения о компонентах мастера  
 Мастер, представленный в данном руководстве, содержит несколько компонентов.  Эти компоненты описаны в приведенной ниже таблице.  
  
|Компонент|Описание|  
|---------------|--------------|  
|Реализация мастера|Это класс с именем `SiteColumnProjectWizard`, реализующий интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Этот интерфейс определяет методы, вызываемые системой Visual Studio при запуске и закрытии мастера и \(в некоторых ситуациях\) при выполнении мастера.|  
|Пользовательский интерфейс мастера|Это окно с именем `WizardWindow`, основанное на WPF.  В нем содержатся два пользовательских элемента управления с именами `Page1` и `Page2`.  Они представляют две страницы мастера.<br /><br /> В данном пошаговом руководстве метод <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>, реализованный в мастере, отображает пользовательский интерфейс мастера.|  
|Модель данных мастера|Это промежуточный класс с именем `SiteColumnWizardModel`, обеспечивающий промежуточный уровень между пользовательским интерфейсом мастера и реализацией мастера.  В данном примере этот класс используется для внедрения абстракции между реализацией мастера и пользовательским интерфейсом мастера. Этот класс не является обязательным компонентом для любого мастера.<br /><br /> В данном пошаговом руководстве реализация мастера передает объект `SiteColumnWizardModel` окну мастера при отображении пользовательского интерфейса мастера.  Пользовательский интерфейс мастера использует методы этого объекта для сохранения значений элементов управления пользовательского интерфейса и для таких задач, как проверка допустимости введенного URL\-адреса.  После того как пользователь завершает работу мастера, реализация мастера определяет конечное состояние пользовательского интерфейса с помощью объекта `SiteColumnWizardModel`.|  
|Диспетчер подписания проекта|Это вспомогательный класс с именем `ProjectSigningManager`, используемый реализацией мастера для создания нового файла key.snk для каждого нового экземпляра проекта.|  
|Команды SharePoint|Это методы, используемые моделью данных мастера для вызова локального сайта SharePoint во время выполнения мастера.  Поскольку команды SharePoint должны использовать платформу .NET Framework 3.5, они реализуются в сборке, отдельной от остального кода мастера.|  
  
## Создание проектов  
 Для выполнения данного пошагового руководства необходимо добавить несколько проектов в решение SiteColumnProjectItem, созданное согласно инструкциям в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
-   Проект WPF.  Необходимо будет реализовать интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> и определить пользовательский интерфейс мастера в этом проекте.  
  
-   Проект библиотеки классов, определяющий команды SharePoint.  \(в этом проекте необходимо использовать .NET Framework 3.5\).  
  
 Начните выполнение пошагового руководства с создания проектов.  
  
#### Создание проекта WPF  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение SiteColumnProjectItem.  
  
2.  В **Обозреватель решений** откройте контекстное меню для узла решения **SiteColumnProjectItem**, выберите **Добавить**, затем выберите **Создание проекта**.  
  
    > [!NOTE]  
    >  В проектах Visual Basic узел решения отображается, только если в диалоговом окне ["Общие", страница "Проекты и решения", диалоговое окно "Параметры"](http://msdn.microsoft.com/ru-ru/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) установлен флажок **Всегда показывать решение**.  
  
3.  В верхней части диалогового окна **Добавить новый проект** убедитесь, что **.NET Framework 4.5** выбрано в списке версий платформы .NET Framework.  
  
4.  Разверните узел **Visual C\#** или узел **Visual Basic** и выберите узел **Окна**.  
  
5.  В списке шаблонов проектов выберите **Библиотека пользовательских элементов управления WPF** введите имя проекта **ProjectTemplateWizard**, а затем нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит проект **ProjectTemplateWizard** в решение и открыть файл UserControl1.xaml по умолчанию.  
  
6.  Удалите файл UserControl1.xaml из проекта.  
  
#### Создание проекта команд SharePoint  
  
1.  В **Обозреватель решений** откройте контекстное меню для узла решения SiteColumnProjectItem, выберите **Добавить**, затем выберите **Создание проекта**.  
  
2.  В верхней части диалогового окна **Добавить новый проект** выберите **.NET Framework 3.5** в списке версий платформы .NET Framework.  
  
3.  Разверните узел **Visual C\#** или узел  **Visual Basic**, затем выберите узел **Окна**.  
  
4.  Выберите шаблон **Библиотека классов**, назовите проект **SharePointCommands**, а затем нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит проект **SharePointCommands** в решение и открыть файл с кодом Class1 по умолчанию.  
  
5.  Удалите из проекта файл c кодом Class1.  
  
## Настройка проектов  
 Перед созданием мастера необходимо добавить некоторые файлы с кодом и ссылки на сборки в проекты.  
  
#### Настройка проекта мастера  
  
1.  В **Обозреватель решений** откройте контекстное меню для узла проекта **ProjectTemplateWizard** и выберите пункт **Свойства**.  
  
2.  В **Конструктор проектов** перейдите на вкладку **Приложение** для проекта Visual C \# или вкладка **Компилировать** для проекта Visual Basic.  
  
3.  Убедитесь, что требуемая версия .NET Framework задает на платформу .NET Framework 4.5, не платформы .NET Framework 4.5.  
  
     Для получения дополнительной информации см. [Практическое руководство. Определение целевой версии .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Открыть контекстное меню для проекта **ProjectTemplateWizard**, выберите **Добавить**, затем выберите **Создать элемент**.  
  
5.  Выберите элемент **Окно \(WPF\)**, назовите элемент **WizardWindow**, а затем нажмите кнопку **Добавить**.  
  
6.  Добавьте 2 элемента **Пользовательский элемент управления \(WPF\)** в проект и назовите их **Page1** и **Page2**.  
  
7.  Добавьте 4 файла кода в проект и присвойте ему следующие имена:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Открыть контекстное меню для узла проекта **ProjectTemplateWizard** и выберите пункт **Добавить ссылку**.  
  
9. Разверните узел **Сборки** и выберите узел **Расширения**, а затем выделите флажки рядом с следующих сборок:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Нажмите кнопку **ОК** для добавления сборок в проект.  
  
11. В **Обозреватель решений** в папке **Ссылки** проекта **ProjectTemplateWizard**, выберите команду **EnvDTE**.  
  
    > [!NOTE]  
    >  В проектах Visual Basic папка **Ссылки** отображается, только если в окне ["Общие", страница "Проекты и решения", диалоговое окно "Параметры"](http://msdn.microsoft.com/ru-ru/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) установлен флажок **Всегда показывать решение**.  
  
12. В окне **Свойства** измените значение свойства **Внедрить типы взаимодействия** на **False**.  
  
13. При разработке проекта на языке Visual Basic следует импортировать пространство имен ProjectTemplateWizard в проект с помощью **Конструктор проектов**.  
  
     Для получения дополнительной информации см. [Практическое руководство. Добавление или удаление импортированных пространств имен &#40;Visual Basic&#41;](~/ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### Настройка проекта SharePointCommands  
  
1.  В **Обозреватель решений** выберите узел проекта **SharePointCommands**.  
  
2.  В строке меню выберите **Проект**, **Добавление существующего элемента**.  
  
3.  В диалоговом окне **Добавление существующего элемента** перейдите в папку, содержащую файлы с кодом проекта ProjectTemplateWizard, а затем выберите файл кода **CommandIds**.  
  
4.  Нажмите стрелку рядом с кнопкой **Добавить**, а затем выберите пункт **Добавить как связь** в меню.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит файл с кодом в проект **SharePointCommands** в качестве ссылки.  Файл кода находится в проекте **ProjectTemplateWizard**, но в нем код будет также компилироваться в проекте **SharePointCommands**.  
  
5.  Добавьте в проект **SharePointCommands** другие команды с именем файла кода.  
  
6.  Выберите проект SharePointCommands, а затем в строке меню выберите **Проект**, **Добавить ссылку**.  
  
7.  Разверните узел **Сборки** и выберите узел **Расширения**, а затем выделите флажки рядом с следующих сборок:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Нажмите кнопку **ОК** для добавления сборок в проект.  
  
## Создание модели мастера, диспетчера подписания и идентификаторов команд SharePoint  
 Добавьте в проект ProjectTemplateWizard код, реализующий следующие компоненты примера:  
  
-   Идентификаторы команд SharePoint.  Эти строки определяют команды SharePoint, мастер использует.  Далее в этом руководстве мы добавим код в проект SharePointCommands реализации команд.  
  
-   Модель данных мастера.  
  
-   Диспетчер подписания проекта.  
  
 Дополнительные сведения об этих компонентах см. в разделе [Общие сведения о компонентах мастера](#wizardcomponents).  
  
#### Определение идентификаторов команд SharePoint  
  
1.  В проекте ProjectTemplateWizard, откройте файл кода CommandIds, а затем замените все содержимое этого файла следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/commandids.vb#5)]  
  
#### Создание модели мастера  
  
1.  Откройте файл кода SiteColumnWizardModel и замените все содержимое этого файла следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]  
  
#### Создание диспетчера подписания проекта  
  
1.  Откройте файл кода ProjectSigningManager, а затем замените все содержимое этого файла следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/projectsigningmanager.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/projectsigningmanager.vb#8)]  
  
## Создание пользовательского интерфейса мастера  
 Добавьте XAML\-код, определяющий пользовательский интерфейс окна мастера и два пользовательских элемента управления, обеспечивающих пользовательский интерфейс страниц мастера. Затем добавьте код, определяющий поведение окна и элементов управления.  Созданный мастер напоминает встроенный мастер для проектов SharePoint в Visual Studio.  
  
> [!NOTE]  
>  При выполнении следующих шагов руководства при компиляции проекта возникнут некоторые ошибки \(после добавления XAML\-кода в проект\).  Эти ошибки исчезнут при добавлении кода на следующих шагах.  
  
#### Создание пользовательского интерфейса окна мастера  
  
1.  В проекте ProjectTemplateWizard, откройте контекстное меню для файла WizardWindow.xaml, а затем нажмите кнопку **Открыть**, чтобы открыть окно в конструкторе.  
  
2.  В представлении XAML конструктора замените текущий код XAML следующим.  Этот код XAML определяет пользовательский интерфейс, содержащий заголовок, класс <xref:System.Windows.Controls.Grid>, содержащий страницы мастера, и кнопки навигации в нижней части окна.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  Окно, создаваемый в этом XAML является производным от базового класса <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>.  При добавлении настраиваемого диалогового окна WPF в Visual Studio, рекомендуется класс производным от этого класса, чтобы его стиль с другими диалоговыми окнами Visual Studio и избежать проблем модального диалогового окна, которые в противном случае выполнение.  Для получения дополнительной информации см. [Создание и управление модальные диалоговые окна](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
3.  При разработке проекта на языке Visual Basic следует удалить пространство имен `ProjectTemplateWizard` из имени класса `WizardWindow` в атрибуте `x:Class` элемента `Window`.  Этот элемент в первой линии XAML.  После этого первая линия должна выглядеть следующим образом:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Откройте файл кода программной части для файла WizardWindow.xaml.  
  
5.  Замените содержимое этого файла, кроме объявлений `using` в верхней части файла, следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml.cs#4)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/wizardwindow.xaml.vb#4)]  
  
#### Создание пользовательского интерфейса первой страницы мастера  
  
1.  В проекте ProjectTemplateWizard, откройте контекстное меню для файла Той, а затем выберите команду **Открыть**, чтобы открыть пользовательский элемент управления в конструкторе.  
  
2.  В представлении XAML конструктора замените текущий код XAML следующим.  XAML определяет пользовательский интерфейс, содержит текстовое поле, где можно ввести URL\-адрес локальных сайтов, которые требуется использовать для отладки.  Пользовательский интерфейс также содержит значения, с помощью которых пользователи могут указывать изолированными ли проект.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml#11)]  
  
3.  При разработке проекта на языке Visual Basic следует удалить пространство имен `ProjectTemplateWizard` из имени класса `Page1` в атрибуте `x:Class` элемента `UserControl`.  Оно находится в первой строке кода XAML.  После этого первая строка должна выглядеть так, как показано в следующем примере.  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Замените содержимое файла Той, кроме объявлений `using` в верхней части файла, следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml.cs#2)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page1.xaml.vb#2)]  
  
#### Создание пользовательского интерфейса второй страницы мастера  
  
1.  В проекте ProjectTemplateWizard, откройте контекстное меню для файла Page2.xaml, а затем выберите **Открыть**.  
  
     В конструкторе откроется указанный пользовательский элемент управления.  
  
2.  В представлении XAML, замените текущее XAML следующим XAML.  Этот XAML\-код определяет пользовательский интерфейс, включающий в себя раскрывающийся список для выбора базового типа столбца сайта, поле со списком для указания встроенной или настраиваемой группы в коллекции, где будет отображаться столбец сайта, и текстовое поле для указания имени столбца сайта.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml#12)]  
  
3.  При разработке проекта на языке Visual Basic следует удалить пространство имен `ProjectTemplateWizard` из имени класса `Page2` в атрибуте `x:Class` элемента `UserControl`.  Оно находится в первой строке кода XAML.  После этого первая строка должна выглядеть так, как показано в следующем примере.  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Замените содержимое файла с выделенным кодом для файла Page2.xaml, кроме объявлений `using` в верхней части файла, следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml.cs#3)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page2.xaml.vb#3)]  
  
## Реализация мастера  
 Определите основные функциональные возможности мастера, реализовав интерфейс <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Этот интерфейс определяет методы, вызываемые системой Visual Studio при запуске и закрытии мастера и \(в некоторых ситуациях\) при выполнении мастера.  
  
#### Реализация мастера  
  
1.  В проекте ProjectTemplateWizard откройте файл с кодом SiteColumnProjectWizard.  
  
2.  Замените все содержимое этого файла следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]  
  
## Создание команд SharePoint  
 Создайте две настраиваемых команды, которые обращаются к серверной объектной модели SharePoint.  Одна из команд определяет допустимость URL\-адреса, указанного пользователем в мастере.  Другая команда получает все типы полей из указанного сайта SharePoint, чтобы пользователь мог выбрать, на каком из них будет основан новый столбец сайта.  
  
#### Определение команд SharePoint  
  
1.  В проекте **SharePointCommands** откройте файл с кодом Commands.  
  
2.  Замените все содержимое этого файла следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/sharepointcommands/commands.cs#9)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/sharepointcommands/commands.vb#9)]  
  
## Контрольная точка  
 На данном этапе выполнения пошагового руководства проект содержит весь код, необходимый для реализации мастера.  Выполните построение проекта, чтобы убедиться, что компиляция выполняется без ошибок.  
  
#### Построение проекта  
  
1.  В меню **Сборка** выберите **Собрать решение**.  
  
## Удаление файла key.snk из шаблона проекта  
 Шаблон проекта, созданный согласно инструкциям в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), содержит файл key.snk, используемый для подписания каждого экземпляра проекта столбца сайта.  Файл key.snk больше не нужен, поскольку теперь мастер создает файл key.snk для каждого проекта.  Удалите файл key.snk из шаблона проекта и удалите ссылки на этот файл.  
  
#### Удаление файла key.snk из шаблона проекта  
  
1.  В **Обозреватель решений** под узлом **SiteColumnProjectTemplate** откройте контекстное меню для файла **key.snk**, а затем выберите **Удалить**.  
  
2.  В диалоговом окне подтверждения, появившемся на экране, нажмите кнопку **ОК**.  
  
3.  В узле **SiteColumnProjectTemplate** откройте файл SiteColumnProjectTemplate.vstemplate, а затем удалите следующий элемент из него.  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Сохраните и закройте файл.  
  
5.  В узле **SiteColumnProjectTemplate** откройте файл ProjectTemplate.csproj или ProjectTemplate.vbproj, а затем удалите следующий элемент `PropertyGroup` из него.  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  Удалите следующий элемент `None`.  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  Сохраните и закройте файл.  
  
## Привязка мастера к шаблону проекта  
 После реализации мастера необходимо привязать мастер к шаблону проекта **столбец сайта**.  Эта операция состоит из процедур:  
  
1.  подпишите сборку мастера строгим именем;  
  
2.  получите токен открытого ключа для сборки мастера;  
  
3.  добавьте ссылку в сборку мастера в VSTEMPLATE\-файле для шаблона проекта **столбец сайта**.  
  
#### Подписывание сборки мастера строгим именем  
  
1.  В **Обозреватель решений** откройте контекстное меню для проекта **ProjectTemplateWizard** и выберите пункт **Свойства**.  
  
2.  На вкладке **Подписи** установите флажок **Подписать сборку**.  
  
3.  В списке **Выберите файл ключа строгого имени** выберите **\<Новый…\>**.  
  
4.  В диалоговом окне **Создание ключа строгого имени** введите имя нового файла ключа, снимите флажок **Защитить мой файл ключей паролем**, а затем нажмите кнопку **ОК**.  
  
5.  Открыть контекстное меню для проекта **ProjectTemplateWizard**, а затем нажмите кнопку **Построение**, чтобы создать файл ProjectTemplateWizard.dll.  
  
#### Получение токена открытого ключа для сборки мастера  
  
1.  В **Главное меню** выберите **Все программы**, выберите **Microsoft Visual Studio** и выберите **Инструменты Visual Studio**, а затем выберите **Командная строка для разработчиков**.  
  
     В окне командной строки Visual Studio будет открыт.  
  
2.  Выполните следующую команду, заменив *PathToWizardAssembly* полным путем к построенной сборке ProjectTemplateWizard.dll для проекта ProjectTemplateWizard на компьютере разработчика.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Токен открытого ключа для сборки ProjectTemplateWizard.dll выводится в окне командной строки Visual Studio.  
  
3.  Не закрывайте окно командной строки Visual Studio.  Токен открытого ключа необходим для следующей процедуры.  
  
#### Добавление ссылки на сборку мастера в VSTEMPLATE\-файл  
  
1.  В **обозревателе решений** разверните узел проекта **SiteColumnProjectTemplate** и откройте файл SiteColumnProjectTemplate.vstemplate.  
  
2.  Добавьте следующий элемент `WizardExtension` между тегами `</TemplateContent>` и `</VSTemplate>` \(ближе к концу файла\).  Замените *your token* значение атрибута `PublicKeyToken` с токеном открытого ключа, можно получить в предыдущей процедуре.  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Дополнительные сведения об элементе `WizardExtension` см. в разделе [Элемент WizardExtension &#40;шаблоны Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).  
  
3.  Сохраните и закройте файл.  
  
## Добавление подстановочных параметров в файл Elements.xml шаблона проекта  
 Добавьте несколько подстановочных параметров в файл Elements.xml проекта SiteColumnProjectTemplate.  Эти параметры инициализируются методом `RunStarted` класса `SiteColumnProjectWizard`, определенного ранее.  При создании пользователем проекта столбца сайта Visual Studio автоматически заменяет эти параметры в файле Elements.xml нового проекта значениями, указанными пользователем в мастере.  
  
 Подстановочный параметр — это токен, начинающийся и заканчивающийся знаком доллара \($\).  Кроме того, чтобы определить пользовательские подстановочные параметры, можно воспользоваться встроенными параметрами, которые определены и инициализированы системой проектов SharePoint.  Для получения дополнительной информации см. [Подстановочные параметры](../sharepoint/replaceable-parameters.md).  
  
#### Добавление подстановочных параметров в файл Elements.xml  
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла Elements.xml следующим XML\-кодом.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     Новый XML\-код изменит значения атрибутов `Name`, `DisplayName`, `Type` и `Group` настраиваемыми подстановочными параметрами.  
  
2.  Сохраните и закройте файл.  
  
## Добавление мастера в пакет VSIX  
 Для развертывания мастера вместе с пакетом VSIX, содержащим шаблон проекта столбца сайта, следует добавить ссылки на проект мастера и проект команд SharePoint в файл source.extension.vsixmanifest в проекте VSIX.  
  
#### Добавление мастера в пакет VSIX  
  
1.  В **Обозреватель решений** в проекте **SiteColumnProjectItem** откройте контекстное меню для файла **source.extension.vsixmanifest**, а затем выберите **Открыть**.  
  
     Файл будет открыт Visual Studio в редакторе манифестов.  
  
2.  На вкладке **Активы** редактора, нажмите кнопку **Создать**.  
  
     Будет открыто диалоговое окно **Добавить новый актив**.  
  
3.  В списке **Тип** выберите **Microsoft.VisualStudio.Assembly**.  
  
4.  В списке **Источник** выберите **Проект в текущем решении**.  
  
5.  В списке **Проект** выберите **ProjectTemplateWizard**, а затем нажмите кнопку **ОК**.  
  
6.  На вкладке **Активы** редактора, выберите кнопку **Создать** еще раз.  
  
     Будет открыто диалоговое окно **Добавить новый актив**.  
  
7.  В списке **Тип** введите **SharePoint.Commands.v4**.  
  
8.  В списке **Источник** выберите **Проект в текущем решении**.  
  
9. В списке **Проект** выберите проект **SharePointCommands**, а затем нажмите кнопку **ОК**.  
  
10. В строке меню выберите **Построение**, **Построить решение**, а затем убедитесь, что построения решений без ошибок.  
  
## Тестирование мастера  
 Мастер готов к тестированию.  Начните отладку решения SiteColumnProjectItem в экспериментальном экземпляре Visual Studio.  Затем протестируйте мастер для проекта столбца сайта в экспериментальном экземпляре Visual Studio.  И наконец, выполните построение и запуск проекта, чтобы проверить, что столбец сайта работает ожидаемым образом.  
  
#### Начало отладки решения  
  
1.  Перезапустите Visual Studio с правами администратора, а затем откройте решение SiteColumnProjectItem.  
  
2.  В проекте ProjectTemplateWizard, откройте файл кода SiteColumnProjectWizard, а затем добавьте точку останова в первой строке кода в методе `RunStarted`.  
  
3.  В строке меню выберите **Отладка**, **Исключения**.  
  
4.  В диалоговом окне **Исключения** убедитесь, что установлены флажки **Вызванное** и **Не обработанное пользовательским кодом** для **Исключения среды CLR**, а затем кнопку **ОК**. выберитесь  
  
5.  Запустите отладку путем выбора ключа или **F5** в строке меню, выбирая **Отладка**, **Начать отладку**.  
  
     Visual Studio установит расширение для %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Site Column\\1.0 и запустить экспериментальный экземпляр Visual Studio.  При выполнении элемента проекта в этом экземпляре Visual Studio.  
  
#### Тестирование мастера в Visual Studio  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  Разверните узел **Visual C\#** или узел **Visual Basic** \(в зависимости от языка, шаблон проекта\), затем узел **SharePoint** и выберите узел **2010**.  
  
3.  В списке шаблонов проектов выберите **Столбец сайта** введите имя проекта **SiteColumnWizardTest**, а затем нажмите кнопку **ОК**.  
  
4.  Убедитесь, что выполнение кода в другом экземпляре Visual Studio прерывается на точке останова, заданной ранее в методе `RunStarted`.  
  
5.  Продолжить отладку проекта с помощью ключа или **F5** в строке меню, выбирая **Отладка**, **Продолжить**.  
  
6.  В поле **Мастер настройки SharePoint** введите URL\-адрес сайта, который требуется использовать для отладки, и затем нажмите кнопку **Далее**.  
  
7.  На второй странице **Мастера настройки SharePoint** задайте следующие параметры:  
  
    -   В списке **Тип** выберите **логический**.  
  
    -   В списке **Группа** выберите **Пользовательские Yes\/No столбцы**.  
  
    -   В поле **Имя** укажите my Yes\/No столбец, а затем нажмите кнопку **Готово**.  
  
     В **Обозреватель решений** новый проект с именем **Поле1** содержится с элемента проекта и файл будет открыт Visual Studio в редакторе Elements.xml проекта.  
  
8.  Проверьте, что в файле Elements.xml содержатся значения, заданные в мастере.  
  
#### Тестирование столбца сайта в SharePoint  
  
1.  В экспериментальном экземпляре Visual Studio выберите ключ F5.  
  
     Столбец сайта передаются и развертывается на сайт SharePoint, который определяет свойства проекта **URL\-адрес сайта**.  В веб\-браузере будет открыта страница по умолчанию для этого сайта.  
  
    > [!NOTE]  
    >  Если появится диалоговое окно **Отладка скриптов отключена**, нажмите кнопку **Да**, чтобы продолжить отладку проекта.  
  
2.  В меню **Действия сайта** выберите команду **Параметры сайта**.  
  
3.  На странице " параметры сайта, в разделе **Коллекции** выберите ссылку **Столбцы сайта**.  
  
4.  В списке столбцов сайта, убедитесь, что команда **Пользовательские Yes\/No столбцы** содержит файл с именем столбца **Мой Yes\/No столбец**, а затем закройте веб\-браузера.  
  
## Очистка компьютера разработчика  
 После завершения тестирования элемента проекта удалите шаблон проекта из экспериментального экземпляра Visual Studio.  
  
#### Очистка компьютера разработчика  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **Сервис**, **Расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В списке расширений выберите **Столбец сайта**, а затем нажмите кнопку **Удалить**.  
  
3.  В диалоговом окне, появившемся на экране, нажмите кнопку **Да**, чтобы подтвердить удаление расширения, а затем нажмите кнопку **Перезагрузить сейчас** для завершения процесса удаления.  
  
4.  Закройте и экспериментальный экземпляр Visual Studio и экземпляр, в котором решения CustomActionProjectItem открыто.  
  
     Дополнительные сведения о развертывании расширений [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] см. в разделе [Расширения Visual Studio доставки](../extensibility/shipping-visual-studio-extensions.md).  
  
## См. также  
 [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Практическое руководство. Использование мастеров для шаблонов проекта](~/extensibility/how-to-use-wizards-with-project-templates.md)  
  
  