---
title: Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2 | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e0445e66b10ca8bfa0ae4f5d2c35246d71745788
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604874"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2
  После определения пользовательского типа элемента проекта SharePoint и свяжите ее с помощью шаблона проекта в Visual Studio, можно также содержат мастер для шаблона. Мастер можно использовать для сбора сведений от пользователей, при использовании шаблона для создания нового проекта, который содержит элемент проекта. Собранные сведения могут использоваться для инициализации элемента проекта.

 В этом пошаговом руководстве вы добавите мастера шаблон проекта столбца сайта, представленный в [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Когда пользователь создает проект столбца сайта, мастер собирает сведения об этом столбце (например, базовый тип и группу) и добавляет эту информацию, чтобы *Elements.xml* файл в новом проекте.

 В этом пошаговом руководстве описаны следующие задачи.

-   Создание мастера для настраиваемого типа элемента проекта SharePoint, который связан с шаблоном проекта.

-   Определение настраиваемого мастера пользовательского интерфейса, похожего на встроенный мастер для проектов SharePoint в Visual Studio.

-   Создав два *команд SharePoint* , которые используются для вызова в локальном сайте SharePoint, во время работы мастера. Команды SharePoint представляют собой методы, которые могут использоваться расширениями Visual Studio для вызова интерфейсов API в серверной объектной модели SharePoint. Дополнительные сведения см. в разделе [обращение к объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

-   Использование подстановочных параметров для инициализации файлов проекта SharePoint с данными, собранными в мастере.

-   Создание нового SNK-файл в каждый новый экземпляр проекта столбца сайта. Этот файл используется для подписывания проекта, выходные данные, чтобы сборка решения SharePoint могут развертываться в глобальном кэше сборок.

-   Отладка и тестирование мастера.

> [!NOTE]
> Ряд образцы рабочих процессов, см. в разделе [примеры рабочего процесса SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства, необходимо сначала создать решение SiteColumnProjectItem, выполнив [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Также необходимы следующие компоненты на компьютере разработчика для выполнения этого пошагового руководства:

- Поддерживаемые версии Windows, SharePoint и Visual Studio.

- Visual Studio SDK. В этом пошаговом руководстве использует **проект VSIX** шаблона в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. в разделе [расширения инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Знание следующие основные понятия будут полезны, но не требуется для выполнения данного пошагового руководства:

- Мастеров для шаблонов проектов и элементов в Visual Studio. Дополнительные сведения см. в разделе [Как Использование мастеров для шаблонов проектов](../extensibility/how-to-use-wizards-with-project-templates.md) и <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс.

- Столбцы сайта в SharePoint. Дополнительные сведения см. в разделе [столбцы](http://go.microsoft.com/fwlink/?LinkId=183547).

## <a name="understand-the-wizard-components"></a>Основные сведения о компонентах мастера
 Мастер, представленный в этом пошаговом руководстве, содержит несколько компонентов. В следующей таблице описаны эти компоненты.

|Компонент|Описание:|
|---------------|-----------------|
|Мастер реализации|Это класс, называемый `SiteColumnProjectWizard`, который реализует <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс. Этот интерфейс определяет методы, которые Visual Studio вызывает при мастера начинается и завершается в определенное время, а мастер.|
|Мастер пользовательского интерфейса|Это окно на основе WPF, с именем `WizardWindow`. Это окно содержит две пользовательские элементы управления, с именем `Page1` и `Page2`. Эти пользовательские элементы управления представляют две страницы мастера.<br /><br /> В этом пошаговом руководстве <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> метод реализации мастер отображает пользовательский Интерфейс мастера.|
|Мастер модели данных|Это промежуточный класс, с именем `SiteColumnWizardModel`, который обеспечивает слой между пользовательским Интерфейсом мастера и реализацией мастера. В этом примере этот класс используется для внедрения абстракции между реализацией мастера и пользовательском Интерфейсе мастера друг от друга; Этот класс не является обязательным компонентом для всех мастеров.<br /><br /> В этом пошаговом руководстве реализация мастера передает `SiteColumnWizardModel` объект в окно мастера, при отображении пользовательского интерфейса мастера. Мастер пользовательского интерфейса использует методы этого объекта для сохранения значений элементов управления в пользовательском Интерфейсе и для выполнения задач, таких как проверка допустимости введенного URL-адреса. По окончании работы мастера, реализация мастер использует `SiteColumnWizardModel` объект и определяет конечное состояние пользовательского интерфейса.|
|Подписи руководителя проекта|Это вспомогательный класс с именем `ProjectSigningManager`, используемый реализацией мастера, чтобы создать новый файл key.snk в каждый новый экземпляр проекта.|
|команды SharePoint|Это методы, используемые моделью данных мастера для вызова локального сайта SharePoint во время работы мастера. Поскольку команды SharePoint должны быть предназначены для .NET Framework 3.5, эти команды будут реализованы в сборке, отдельной от остальной части кода мастера.|

## <a name="create-the-projects"></a>Создание проектов
 Для выполнения этого пошагового руководства, необходимо добавить несколько проектов в решение SiteColumnProjectItem, созданный в [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Проект WPF. Вы реализуете <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейса и определения пользовательского интерфейса мастера в этом проекте.

- Проект библиотеки классов, определяющий команды SharePoint. Этот проект должен использовать.NET Framework 3.5.

  Начало выполнения пошагового руководства по созданию проектов.

#### <a name="to-create-the-wpf-project"></a>Создание проекта WPF

1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение SiteColumnProjectItem.

2.  В **обозревателе решений**, откройте контекстное меню для **SiteColumnProjectItem** узел решения, выберите **добавить**, а затем выберите **новый проект**.

3.  В верхней части **Добавление нового проекта** диалоговом окне убедитесь, что **.NET Framework 4.5** выбирается в списке версий .NET Framework.

4.  Разверните **Visual C#** узел или **Visual Basic** узел и выберите **Windows** узла.

5.  В списке шаблонов проектов выберите **Библиотека пользовательских элементов управления WPF**, назовите проект **ProjectTemplateWizard**, а затем выберите **ОК** кнопки.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **ProjectTemplateWizard** проекта в решение и откроет файл UserControl1.xaml по умолчанию.

6.  Удалите файл UserControl1.xaml из проекта.

#### <a name="to-create-the-sharepoint-commands-project"></a>Чтобы создать проект команды SharePoint

1.  В **обозревателе решений**, откройте контекстное меню узла решения SiteColumnProjectItem, выберите **добавить**, а затем выберите **новый проект**.

2.  В верхней части **Добавление нового проекта** диалоговое окно, выберите **.NET Framework 3.5** в списке версий .NET Framework.

3.  Разверните **Visual C#** узел или **Visual Basic** узел, а затем выберите **Windows** узла.

4.  Выберите **библиотеки классов** шаблон проекта, присвойте проекту имя **SharePointCommands**, а затем выберите **ОК** кнопки.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **SharePointCommands** проекта в решение и открывает файл кода по умолчанию Class1.

5.  Удалите файл Class1 код из проекта.

## <a name="configure-the-projects"></a>Настройка проектов
 Перед созданием мастера, необходимо добавить некоторые файлы кода и ссылки на сборки в проекты.

#### <a name="to-configure-the-wizard-project"></a>Настройка проекта мастера

1.  В **обозревателе решений**, откройте контекстное меню для **ProjectTemplateWizard** узел проекта, а затем выберите **свойства**.

2.  В **конструктор проектов**, выберите **приложения** вкладку для проекта Visual C# или **компиляции** вкладку для проекта Visual Basic.

3.  Убедитесь, что требуемая версия .NET framework имеет значение .NET Framework 4.5, не 4.5 клиентский профиль .NET Framework.

     Дополнительные сведения см. в разделе [Как определить целевую версию .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

4.  Откройте контекстное меню для **ProjectTemplateWizard** проекта, выберите **добавить**, а затем выберите **новый элемент**.

5.  Выберите **Window (WPF)** товара, присвойте элементу имя **WizardWindow**, а затем выберите **добавить** кнопки.

6.  Добавьте два **пользовательский элемент управления (WPF)** элементов в проект и назовите их **Page1** и **Page2**.

7.  Добавьте четыре файла кода в проект и предоставить им следующие имена:

    -   SiteColumnProjectWizard

    -   SiteColumnWizardModel

    -   ProjectSigningManager

    -   Идентификаторы команд CommandIds

8.  Откройте контекстное меню для **ProjectTemplateWizard** узел проекта, а затем выберите **добавить ссылку**.

9. Разверните **сборки** узел, выберите **расширения** узел, а затем выберите флажки для соответствующей следующие сборки:

    -   EnvDTE

    -   Microsoft.VisualStudio.OLE.Interop

    -   Microsoft.VisualStudio.SharePoint

    -   Microsoft.VisualStudio.Shell.11.0

    -   Microsoft.VisualStudio.Shell.Interop.10.0

    -   Microsoft.VisualStudio.Shell.Interop.11.0

    -   Microsoft.VisualStudio.TemplateWizardInterface

10. Выберите **ОК** кнопка для добавления сборки в проект.

11. В **обозревателе решений**в разделе **ссылки** папку для **ProjectTemplateWizard** проекта, выберите **EnvDTE**.

12. В **свойства** окна, измените значение свойства **Embed Interop Types** свойства **False**.

13. Если вы разрабатываете проект Visual Basic, импортировать пространство имен ProjectTemplateWizard в проект с помощью **конструктор проектов**.

     Дополнительные сведения см. в разделе [Как Добавление или удаление импортированных пространств имен &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>Чтобы настроить проект SharePointcommands

1.  В **обозревателе решений**, выберите **SharePointCommands** узел проекта.

2.  В строке меню выберите **проекта**, **добавить существующий элемент**.

3.  В **добавить существующий элемент** диалоговом окне перейдите к папке, содержащей файлы кода для проекта ProjectTemplateWizard и выберите **CommandIds** файл кода.

4.  Выберите стрелку рядом с пунктом **добавить** кнопку, а затем выберите **добавить как ссылку** в появившемся меню.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет файл кода, чтобы **SharePointCommands** проект в виде ссылки. Файл кода находится в **ProjectTemplateWizard** проект, но код в файле также компилируется в **SharePointCommands** проекта.

5.  В **SharePointCommands** проекта, добавьте еще один файл кода с именем команды.

6.  Выберите проект SharePointCommands, а затем в строке меню выберите **проекта** > **добавить ссылку**.

7.  Разверните **сборки** узел, выберите **расширения** узел, а затем выберите флажки для соответствующей следующие сборки:

    -   Microsoft.SharePoint

    -   Microsoft.VisualStudio.SharePoint.Commands

8.  Выберите **ОК** кнопка для добавления сборки в проект.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Создание модели мастера, Диспетчер подписания и идентификаторы команд SharePoint
 Добавьте код к проекту ProjectTemplateWizard, чтобы установить следующие компоненты в образце:

- Идентификаторы команд SharePoint. Эти строки идентификации команды SharePoint, используемые мастером. Далее в этом пошаговом руководстве вы добавите код в проект SharePointCommands для реализации этих команд.

- Мастер модели данных.

- Подписи руководителем проекта.

  Дополнительные сведения об этих компонентах см. в разделе [основные сведения о компонентах мастера](#wizardcomponents).

#### <a name="to-define-the-sharepoint-command-ids"></a>Для определения идентификаторов команд SharePoint

1.  В проекте ProjectTemplateWizard откройте файл кода CommandIds и затем замените все содержимое этого файла следующим кодом.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>Для создания модели мастера

1.  Откройте файл кода SiteColumnWizardModel и замените все содержимое этого файла следующим кодом.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>Для создания подписи руководителя проекта

1.  Откройте файл кода ProjectSigningManager и замените все содержимое этого файла следующим кодом.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>Создание пользовательского интерфейса мастера
 Добавьте XAML для определения пользовательского интерфейса в окне мастера и двумя элементами управления, которые предоставляют пользовательский Интерфейс для страницы мастера и добавьте код для определения поведения элементов управления окна и пользователем. Мастер, который создается напоминает встроенного мастера для проектов SharePoint в Visual Studio.

> [!NOTE]
>  В следующих шагах проект будет содержать некоторые ошибки компиляции, после добавления XAML или кода в проект. Эти ошибки исчезнут при добавлении кода в последующих шагах.

#### <a name="to-create-the-wizard-window-ui"></a>Для создания пользовательского интерфейса в окне мастера

1.  В проекте ProjectTemplateWizard, откройте контекстное меню для файла WizardWindow.xaml и затем выберите **откройте** чтобы открыть окно в конструкторе.

2.  В представлении XAML в конструкторе замените текущий XAML следующий XAML. XAML определяет пользовательский Интерфейс, который включает в себя заголовок, <xref:System.Windows.Controls.Grid> , содержащий страницы мастера, и кнопки навигации в нижней части окна.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    >  Окно, которое создается в этом XAML является производным от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> базового класса. При добавлении настраиваемого поля диалогового окна WPF в Visual Studio, мы рекомендуем, что диалоговое окно производными этого класса иметь согласованный Дизайн с другими диалоговыми окнами Visual Studio и избежать проблем модального диалогового окна, которые могут возникать. Дополнительные сведения см. в разделе [Создание и управление модальные диалоговые окна](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).

3.  Если вы разрабатываете проект Visual Basic, удалите `ProjectTemplateWizard` пространства имен из `WizardWindow` имени класса в `x:Class` атрибут `Window` элемента. Этот элемент находится в первой строке XAML. Когда все будет готово, первая строка будет выглядеть как в следующем примере.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4.  Откройте файл с выделенным кодом для файла WizardWindow.xaml.

5.  Замените содержимое этого файла, за исключением `using` объявления в верхней части файла, следующим кодом.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>Чтобы создать первую страницу мастера пользовательского интерфейса

1.  В проекте ProjectTemplateWizard, откройте контекстное меню для файла Page1.xaml и затем выберите **откройте** чтобы открыть пользовательский элемент управления в конструкторе.

2.  В представлении XAML в конструкторе замените текущий XAML следующий XAML. XAML определяет пользовательский Интерфейс, который содержит текстовое поле, где пользователи могут вводить URL-адрес локальных сайтов, которые они хотят использовать для отладки. Пользовательский Интерфейс также переключателей, с помощью которого пользователи могут указать, хранятся ли проект в изолированной среде.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3.  Если вы разрабатываете проект Visual Basic, удалите `ProjectTemplateWizard` пространства имен из `Page1` имени класса в `x:Class` атрибут `UserControl` элемента. Это первая часть XAML. Когда вы закончите, первая строка должна выглядеть следующим образом.

    ```xml
    <UserControl x:Class="Page1"
    ```

4.  Замените содержимое файла Page1.xaml, за исключением `using` объявления в верхней части файла, следующим кодом.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>Чтобы создать второй странице мастера пользовательского интерфейса

1.  В проекте ProjectTemplateWizard, откройте контекстное меню для файла Page2.xaml и затем выберите **откройте**.

     Пользовательский элемент управления откроется в конструкторе.

2.  В представлении XAML замените следующий XAML текущего XAML. XAML определяет пользовательский Интерфейс, который включает в себя стрелку раскрывающегося списка для выбора базового типа столбца сайта, поле со списком для указания встроенные или пользовательские группы, к которой отображается столбец сайта в коллекции и текстовое поле для указания имени столбца сайта.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3.  Если вы разрабатываете проект Visual Basic, удалите `ProjectTemplateWizard` пространства имен из `Page2` имени класса в `x:Class` атрибут `UserControl` элемента. Это первая часть XAML. Когда вы закончите, первая строка должна выглядеть следующим образом.

    ```xml
    <UserControl x:Class="Page2"
    ```

4.  Замените содержимое файла кода для файла Page2.xaml, за исключением `using` объявления в верхней части файла, следующим кодом.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>Мастер реализации
 Определите основные функции мастера, реализовав <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс. Этот интерфейс определяет методы, которые Visual Studio вызывает при мастера начинается и завершается в определенное время, а мастер.

#### <a name="to-implement-the-wizard"></a>Реализация мастера

1.  В проекте ProjectTemplateWizard откройте файл кода SiteColumnProjectWizard.

2.  Замените все содержимое этого файла следующим кодом.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>Создание команды SharePoint
 Создайте два пользовательских команд, которые вызывают объектную модель сервера SharePoint. Одна команда определяет, является ли допустимым URL-адрес сайта, который пользователь вводит в мастере. Другая команда получает все типы полей в указанном сайте SharePoint, чтобы пользователи могут выбрать какой из них следует использовать в качестве основы для новый столбец сайта.

#### <a name="to-define-the-sharepoint-commands"></a>Для определения команды SharePoint

1.  В **SharePointCommands** проекта, откройте файл кода команды.

2.  Замените все содержимое этого файла следующим кодом.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>Контрольная точка
 На этом этапе в этом пошаговом руководстве, весь код для мастера теперь находится в проекте. Постройте проект, чтобы убедиться в том, что оно компилируется без ошибок.

#### <a name="to-build-your-project"></a>Построение проекта

1.  В строке меню последовательно выберите **Сборка**  >  **Собрать решение**.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Удаление файла key.snk из шаблона проекта
 В [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), что созданный шаблон проекта содержит файл key.snk, используемый для подписания каждого экземпляра проекта столбца сайта. Этот файл key.snk больше не требуется, так как теперь мастер создает файл key.snk для каждого проекта. Удалите файл key.snk из шаблона проекта и ссылки на этот файл.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Чтобы удалить файл key.snk из шаблона проекта

1.  В **обозревателе решений**в разделе **SiteColumnProjectTemplate** узел, откройте контекстное меню для **key.snk** файл, а затем выберите **удалить**.

2.  В диалоговом окне подтверждения выберите **ОК** кнопки.

3.  В разделе **SiteColumnProjectTemplate** узел, откройте файл SiteColumnProjectTemplate.vstemplate и удалите следующий элемент из него.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4.  Сохраните и закройте файл.

5.  В разделе **SiteColumnProjectTemplate** узел, откройте файл ProjectTemplate.csproj или ProjectTemplate.vbproj, а затем удалите следующие `PropertyGroup` элемент из него.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6.  Удалите следующий `None` элемент.

    ```xml
    <None Include="key.snk" />
    ```

7.  Сохраните и закройте файл.

## <a name="associating-the-wizard-with-the-project-template"></a>Привязка с использованием шаблона проекта мастера
 Теперь, когда вы реализовали мастер, необходимо связать в мастере **столбец сайта** шаблона проекта. Существует три процедуры, которые необходимо выполнить для этого:

1.  Подпишите сборку строгим именем мастера.

2.  Получение токена открытого ключа для сборки мастера.

3.  Добавьте ссылку на сборку мастера в файле .vstemplate для **столбец сайта** шаблона проекта.

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Чтобы подписать сборку строгим именем мастера

1.  В **обозревателе решений**, откройте контекстное меню для **ProjectTemplateWizard** проекта, а затем выберите **свойства**.

2.  На **подписывание** выберите **подписать сборку** "флажок".

3.  В **выберите файл ключа строгого имени** выберите  **\<создать... >**.

4.  В **Создание ключа строгого имени** диалогового окна введите имя для нового файла ключа, снимите флажок **защитить мой файл ключей паролем** , а затем нажать **ОК** кнопки.

5.  Откройте контекстное меню для **ProjectTemplateWizard** проекта, а затем выберите **построения** для создания файла ProjectTemplateWizard.dll.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Чтобы получить маркер открытого ключа для сборки мастера

1.  На **меню "Пуск"**, выберите **все программы**, выберите **Microsoft Visual Studio**, выберите **средств Visual Studio**, а затем выберите  **Командная строка разработчика**.

     Откроется окно командной строки Visual Studio.

2.  Выполните следующую команду, заменив *PathToWizardAssembly* с указанием полного пути к сборке ProjectTemplateWizard.dll ProjectTemplateWizard проекта на компьютере разработчика:

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Токен открытого ключа для сборки ProjectTemplateWizard.dll записываются в окно командной строки Visual Studio.

3.  Не закрывайте окно командной строки Visual Studio. Вам потребуется токен открытого ключа для следующей процедуры.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Чтобы добавить ссылку в сборку мастера в VSTEMPLATE-файл

1.  В **обозревателе решений**, разверните **SiteColumnProjectTemplate** узел проекта и откройте файл SiteColumnProjectTemplate.vstemplate.

2.  В конце файла добавьте следующий `WizardExtension` элемент между `</TemplateContent>` и `</VSTemplate>` теги. Замените *срок действия токена* значение `PublicKeyToken` атрибута с токен открытого ключа, полученный в предыдущей процедуре.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Дополнительные сведения о `WizardExtension` элемент, см. в разделе [элемент WizardExtension &#40;шаблоны Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).

3.  Сохраните и закройте файл.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Добавьте в файл Elements.xml в шаблоне проекта подстановочные параметры
 Добавьте несколько подстановочных параметров для *Elements.xml* файл в проекте SiteColumnProjectTemplate. Эти параметры инициализируются в `RunStarted` метод в `SiteColumnProjectWizard` класс, который вы задали ранее. Когда пользователь создает проект столбца сайта, Visual Studio автоматически заменяет эти параметры в *Elements.xml* файл в новом проекте со значениями, указанными в мастере.

 Можно заменить параметр является маркер, который начинается и заканчивается символом доллара ($). Кроме определения собственных подстановочных параметров, можно использовать встроенные параметры, которые определены и инициализированы в системе проекта SharePoint. Дополнительные сведения см. в разделе [подстановочных параметров](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Чтобы добавить в файл Elements.xml подстановочные параметры

1.  В проекте SiteColumnProjectTemplate, замените содержимое файла *Elements.xml* файл следующий XML-код.

    ```xml
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

     Новый XML-код изменяет значения `Name`, `DisplayName`, `Type`, и `Group` атрибуты для пользовательских подстановочных параметров.

2.  Сохраните и закройте файл.

## <a name="add-the-wizard-to-the-vsix-package"></a>Мастер добавления в пакет VSIX
 Чтобы развернуть пакет VSIX, содержащий шаблон проекта столбца сайта в мастере, добавьте ссылки на проект мастера и проект команды SharePoint файл source.extension.vsixmanifest в проект VSIX.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Чтобы добавить мастер пакет VSIX

1.  В **обозревателе решений**в **SiteColumnProjectItem** проекта, откройте контекстное меню для **source.extension.vsixmanifest** файл, а затем выберите **Открыть**.

     Visual Studio открывает файл в редакторе манифестов.

2.  На **активы** вкладка редактора выберите **New** кнопки.

     **Добавить новый актив** откроется диалоговое окно.

3.  В **тип** выберите **Microsoft.VisualStudio.Assembly**.

4.  В **источника** выберите **проект в текущем решении**.

5.  В **проекта** выберите **ProjectTemplateWizard**, а затем выберите **ОК** кнопки.

6.  На **активы** вкладка редактора выберите **New** еще раз.

     **Добавить новый актив** откроется диалоговое окно.

7.  В **тип** , введите **SharePoint.Commands.v4**.

8.  В **источника** выберите **проект в текущем решении**.

9. В **проекта** выберите **SharePointCommands** проекта, а затем выберите **ОК** кнопки.

10. В строке меню выберите **построения** > **построить решение**и убедитесь, что сборка решения выполняется без ошибок.

## <a name="test-the-wizard"></a>Протестируйте мастер
 Теперь вы готовы для тестирования мастер. Начните отладку решения SiteColumnProjectItem в экспериментальном экземпляре Visual Studio. Затем протестируйте мастер для проекта столбца сайта в экспериментальном экземпляре Visual Studio. Наконец создайте и запустите проект, чтобы убедиться, что столбец сайта работает должным образом.

#### <a name="to-start-debugging-the-solution"></a>Чтобы начать отладку решения

1.  Перезапустите Visual Studio от имени администратора и откройте решение SiteColumnProjectItem.

2.  В проекте ProjectTemplateWizard, откройте файл кода SiteColumnProjectWizard и затем добавьте точку останова в первой строке кода в `RunStarted` метод.

3.  В строке меню выберите **Отладка** > **исключения**.

4.  В **исключения** диалоговом окне убедитесь, что **вызванное** и **не обработанное пользовательским кодом** флажки для **исключения среды CLR**очищаются, а затем выберите **ОК** кнопки.

5.  Начать отладку, выбрав **F5** ключа или в строке меню выберите **Отладка** > **начать отладку**.

     Visual Studio устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 и запускает экспериментальный экземпляр Visual Studio. В этом экземпляре Visual Studio будет тестировать элемент проекта.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Для тестирования мастер в Visual Studio

1. В экспериментальном экземпляре Visual Studio в строке меню выберите **файл** > **New** > **проекта**.

2. Разверните **Visual C#** узел или **Visual Basic** (в зависимости от языка, который поддерживает шаблон проекта), раскройте **SharePoint** узел, а затем выберите **2010** узла.

3. В списке шаблонов проектов выберите **столбец сайта**, присвойте проекту имя **SiteColumnWizardTest**, а затем выберите **ОК** кнопки.

4. Убедитесь, что выполнение кода в другом экземпляре Visual Studio будет приостановлено в точке останова, заданной ранее в `RunStarted` метод.

5. Продолжить отладку проекта, выбрав **F5** ключа или в строке меню выберите **Отладка** > **Продолжить**.

6. В **мастер настройки SharePoint**, введите URL-адрес сайта, который вы хотите использовать для отладки, а затем выберите **Далее** кнопки.

7. На второй странице **мастер настройки SharePoint**, задайте следующие параметры:

   - В **тип** выберите **логическое**.

   - В **группы** выберите **настраиваемые столбцы Yes/No**.

   - В **имя** введите **Мой столбец**, а затем выберите **Готово** кнопки.

     В **обозревателе решений**, появится новый проект и содержит элемент проекта с именем **Field1**, и Visual Studio откроется проект *Elements.xml* файл в редакторе.

8. Убедитесь, что *Elements.xml* содержит значения, заданные в мастере.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Проверяемый столбец сайта в SharePoint

1.  В экспериментальном экземпляре Visual Studio, выберите **F5** ключ.

     Столбец сайта упаковывается и развертывается в SharePoint сайта, **URL-адрес сайта** указывает свойство проекта. Веб-браузер открывает страницу по умолчанию для этого сайта.

    > [!NOTE]
    >  Если **отладка скриптов отключена** открывшемся диалоговом окне выберите **Да** кнопку, чтобы продолжить отладку проекта.

2.  На **действия сайта** меню, выберите **параметры сайта**.

3.  На странице "Параметры сайта" в разделе **галереи**, выберите **столбцы сайта** ссылку.

4.  В списке столбцов сайта, убедитесь, что **Yes/No настраиваемые столбцы** группа содержит столбец с именем **Мой столбец**, а затем закройте веб-браузера.

## <a name="clean-up-the-development-computer"></a>Очистка компьютера разработчика
 После завершения тестирования элемента проекта, удалите шаблона проекта в экспериментальном экземпляре Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Для очистки компьютера разработчика

1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **средства** > **расширения и обновления**.

     Появится диалоговое окно **Расширения и обновления**.

2.  В список расширений, выберите **столбец сайта**, а затем выберите **удаления** кнопки.

3.  В появившемся диалоговом окне, выберите **Да** кнопку, чтобы убедиться, что вы хотите удалить расширение, а затем выберите **Перезагрузить сейчас** кнопку, чтобы завершить удаление.

4.  Закройте экспериментальный экземпляр Visual Studio и экземпляр, в котором открыто решение CustomActionProjectItem.

     Сведения о развертывании [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] расширения, см. в разделе [доставка расширений Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Справочник по схеме шаблонов Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Практическое руководство. Использование мастеров для шаблонов проектов](../extensibility/how-to-use-wizards-with-project-templates.md)
