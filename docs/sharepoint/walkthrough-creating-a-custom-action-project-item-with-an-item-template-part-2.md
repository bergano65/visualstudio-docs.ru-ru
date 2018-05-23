---
title: 'Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2 | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b617230c7a30ee437ac1d1120793e567e14c7814
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2"></a>Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2
  После определения пользовательского типа элемента проекта SharePoint и свяжите его с шаблоном элемента в Visual Studio, можно также создать мастер для шаблона. Мастер можно использовать для сбора информации от пользователей, при использовании шаблона для добавления в проект новый экземпляр элемента проекта. Собранные сведения могут использоваться для инициализации элемента проекта.  
  
 В этом пошаговом руководстве вы добавите мастер элемента проекта настраиваемого действия, которое продемонстрировано в [Пошаговое руководство: создание элемент проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). При добавлении пользователем элемента проекта настраиваемого действия в проект SharePoint, мастер собирает сведения о настраиваемое действие (например, его расположение и URL-адрес для перехода в случае конечный пользователь выберет) и добавляет их в файл Elements.xml в новом элемент проекта.  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание мастера для настраиваемого типа элемента проекта SharePoint, который связан с шаблоном элемента.  
  
-   Определение настраиваемого мастера пользовательского интерфейса, похожего на встроенный мастер для элементов проекта SharePoint в Visual Studio.  
  
-   Использование подстановочных параметров для инициализации файлов проекта SharePoint с данными, собранными в мастере.  
  
-   Отладка и тестирование мастера.  
  
> [!NOTE]  
>  Вы можете загрузить пример, содержащий завершенные проекты, код и другие файлы для этого пошагового руководства из следующего расположения: [файлы проекта для пошаговых руководств расширения средств SharePoint](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения данного пошагового руководства, необходимо сначала создать решение CustomActionProjectItem, выполнив [Пошаговое руководство: создание элемент проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Также необходимы следующие компоненты на компьютере разработчика для выполнения данного пошагового руководства:  
  
-   Поддерживаемые версии Windows, SharePoint и Visual Studio. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. В этом пошаговом руководстве используется **проект VSIX** шаблона в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. в разделе [расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Изучением приведенных ниже концепций будет полезно, хотя и не требуется для выполнения данного пошагового руководства.  
  
-   Мастеров для шаблонов проектов и элементов в Visual Studio. Дополнительные сведения см. в разделе [как: использование мастеров шаблонов проекта](../extensibility/how-to-use-wizards-with-project-templates.md) и <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейса.  
  
-   Настраиваемые действия в SharePoint. Дополнительные сведения см. в разделе [пользовательское действие](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="creating-the-wizard-project"></a>Создание проекта мастера  
 Для выполнения данного пошагового руководства, необходимо добавить проект в решение CustomActionProjectItem, созданную в [Пошаговое руководство: создание элемент проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Следует реализовать <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс и определить пользовательский Интерфейс мастера в этом проекте.  
  
#### <a name="to-create-the-wizard-project"></a>Создание проекта мастера  
  
1.  В Visual Studio откройте решение CustomActionProjectItem  
  
2.  В **обозреватель решений**откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
3.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic** узлов и нажмите кнопку **Windows** узла.  
  
4.  В верхней части **новый проект** диалогового окна поле, убедитесь, что **.NET Framework 4.5** выбирается в списке версий .NET Framework.  
  
5.  Выберите **Библиотека пользовательских элементов управления WPF** шаблон проекта, присвойте проекту имя **ItemTemplateWizard**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **ItemTemplateWizard** проекта в решение.  
  
6.  Удаление элемента управления UserControl1 из проекта.  
  
## <a name="configuring-the-wizard-project"></a>Настройка проекта мастера  
 Перед созданием мастера необходимо добавить окно Windows Presentation Foundation (WPF), файл кода и ссылок на сборки в проект.  
  
#### <a name="to-configure-the-wizard-project"></a>Настройка проекта мастера  
  
1.  В **обозревателе решений**, откройте контекстное меню **ItemTemplateWizard** узел проекта, а затем выберите **свойства**.  
  
2.  В **конструктора проектов**, убедитесь, что требуемая версия .NET framework имеет значение .NET Framework 4.5.  
  
     Для проектов Visual C# можно задать это значение на **приложения** вкладки. Для проектов Visual Basic, можно задать это значение на **компиляции** вкладки. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  В **ItemTemplateWizard** проект, добавить **Window (WPF)** в проект и назовите элемент **WizardWindow**.  
  
4.  Добавление двух файлах кода, которые именуются CustomActionWizard и строки.  
  
5.  Откройте контекстное меню для **ItemTemplateWizard** проекта, а затем выберите **добавить ссылку**.  
  
6.  В **диспетчер ссылок - ItemTemplateWizard** диалогового **сборки** узел, выберите **расширения** узла.  
  
7.  Установите флажки рядом со следующими сборками и нажмите кнопку **ОК** кнопки:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  В **обозревателе решений**в **ссылки** выберите папку для проекта ItemTemplateWizard **EnvDTE** ссылки.  
  
9. В **свойства** окна, измените значение **внедрить типы взаимодействия** свойства **False**.  
  
## <a name="defining-the-default-location-and-id-strings-for-custom-actions"></a>Определение расположения по умолчанию и идентификатор строки для пользовательских действий  
 Любого настраиваемого действия есть расположение и идентификатор, который указан в `GroupID` и `Location` атрибуты `CustomAction` в файле Elements.xml. На этом шаге задаются некоторые допустимые значения для этих атрибутов в проекте ItemTemplateWizard. После выполнения данного пошагового руководства, эти строки записываются в файл Elements.xml в элемент проекта настраиваемого действия при пользователи указывают расположение и идентификатор, в мастере.  
  
 Для простоты в этом образце поддерживает только подмножество доступных по умолчанию расположений и идентификаторов. Полный список см. в разделе [предопределенные пользовательские действия и идентификаторы](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Чтобы определить расположение по умолчанию, а также идентификатор строки  
  
1.  Открыть.  
  
2.  В **ItemTemplateWizard** проекта, замените код в файле кода строки с помощью следующего кода.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="creating-the-wizard-ui"></a>Создание пользовательского интерфейса мастера  
 Добавьте код XAML для определения пользовательского интерфейса мастера и добавьте код для привязки элементов управления в мастере на идентификатор строки. Мастер, который вы создаете напоминает встроенный мастер для проектов SharePoint в Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>Создание пользовательского интерфейса мастера  
  
1.  В **ItemTemplateWizard** проекта, откройте контекстное меню для **WizardWindow.xaml** файлу и нажмите кнопку **откройте** Открытие окна в конструкторе.  
  
2.  В представлении XAML замените текущий XAML следующим кодом XAML. Этот код XAML определяет пользовательский Интерфейс, содержащий заголовок, элементы управления для указания поведения настраиваемого действия и кнопки навигации в нижней части окна.  
  
    > [!NOTE]  
    >  Проект будет содержать ошибки компиляции, после добавления этого кода. Эти ошибки исчезнут при добавлении кода в последующих шагах.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  Окна, созданную в этот код XAML является производным от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> базового класса. При добавлении настраиваемого поля диалогового окна WPF в Visual Studio, мы рекомендуем, диалогового окна производными этого класса для стиль соответствовал стилю других диалоговых окон в Visual Studio и избежать проблем, которые могут возникать с модальные диалоговые окна. Дополнительные сведения см. в разделе [Создание и управление модальные диалоговые окна](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Если вы разрабатываете проект Visual Basic, удалите `ItemTemplateWizard` пространства имен из `WizardWindow` имя класса в `x:Class` атрибут `Window` элемента. Этот элемент находится в первой строке кода XAML. Когда закончите, первая строка должна выглядеть следующим образом:  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  В файле кода для файла WizardWindow.xaml замените текущий код следующим кодом.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implementing-the-wizard"></a>Реализация мастера  
 Определите функциональность мастера, реализовав <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейса.  
  
#### <a name="to-implement-the-wizard"></a>Реализация мастера  
  
1.  В **ItemTemplateWizard** откройте проект **CustomActionWizard** файл кода, а затем заменить текущий код в этом файле следующим кодом:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Контрольная точка  
 На этом этапе в пошаговом руководстве, весь код мастер теперь находится в проекте. Постройте проект, чтобы убедиться в том, что оно компилируется без ошибок.  
  
#### <a name="to-build-your-project"></a>Построение проекта  
  
1.  В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
## <a name="associating-the-wizard-with-the-item-template"></a>Привязка мастера шаблона элемента  
 Теперь, после реализации мастера, необходимо связать его с **пользовательское действие** шаблона элемента, выполнив три основных шагов:  
  
1.  Подпишите сборку строгим именем мастера.  
  
2.  Получите токен открытого ключа для сборки мастера.  
  
3.  Добавьте ссылку в сборку мастера в VSTEMPLATE-файле **пользовательское действие** шаблона элемента.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Для подписи сборки строгим именем мастера  
  
1.  В **обозревателе решений**, откройте контекстное меню **ItemTemplateWizard** узел проекта, а затем выберите **свойства**.  
  
2.  На **подписывание** выберите **подписать сборку** флажок.  
  
3.  В **выберите файл ключей строгого имени** выберите  **\<создать... >**.  
  
4.  В **Создание ключа строгого имени** диалогового окна введите имя, снимите **защитить мой файл ключей паролем** флажок и нажмите кнопку **ОК** кнопки.  
  
5.  В строке меню последовательно выберите **Сборка**и **Собрать решение**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Чтобы получить токен открытого ключа для сборки мастера  
  
1.  В окне командной строки Visual Studio, выполните следующую команду, заменив *PathToWizardAssembly* с указанием полного пути к сборке ItemTemplateWizard.dll для проекта ItemTemplateWizard на разработку компьютер.  
  
    ```xml  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Токен открытого ключа сборки ItemTemplateWizard.dll записывается в окно командной строки Visual Studio.  
  
2.  Не закрывайте окно командной строки Visual Studio. Вам понадобятся токен открытого ключа для выполнения следующей процедуры.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Чтобы добавить ссылку на сборку мастера в VSTEMPLATE-файл  
  
1.  В **обозревателе решений**, разверните **ItemTemplate** узел проекта, а затем откройте файл ItemTemplate.vstemplate.  
  
2.  В конце файла добавьте следующие `WizardExtension` элемент между `</TemplateContent>` и `</VSTemplate>` тегов. Замените *YourToken* значение `PublicKeyToken` атрибута с токен открытого ключа, полученное в предыдущей процедуре.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Дополнительные сведения о `WizardExtension` элемент, в разделе [элемент WizardExtension &#40;шаблоны Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Сохраните и закройте файл.  
  
## <a name="adding-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Добавление подстановочных параметров в файл Elements.xml в шаблоне элемента  
 Добавьте несколько подстановочных параметров в файл Elements.xml в проекте ItemTemplate. Эти параметры инициализируются `PopulateReplacementDictionary` метод `CustomActionWizard` класса, которое было определено ранее. При добавлении элемента проекта настраиваемого действия в проект Visual Studio автоматически заменяет эти параметры в файл Elements.xml в новый элемент проекта со значениями, указанными в мастере.  
  
 Заменяемый параметр представляет маркер, который начинается и заканчивается символом доллара ($). Кроме определения собственных подстановочные параметры, можно использовать встроенные параметры, системы проектов SharePoint определяет и инициализирует. Дополнительные сведения см. в разделе [подстановочные параметры](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Чтобы добавить в файл Elements.xml подстановочные параметры  
  
1.  В проекте ItemTemplate Замените содержимое файла Elements.xml следующий XML-код.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Новый XML-код изменяет значения `Id`, `GroupId`, `Location`, `Description`, и `Url` атрибуты подстановочные параметры.  
  
2.  Сохраните и закройте файл.  
  
## <a name="adding-the-wizard-to-the-vsix-package"></a>Мастер добавления пакета VSIX  
 В файле source.extension.vsixmanifest в проекте VSIX добавьте ссылку на проект мастера, чтобы он развертывается в составе пакета VSIX, который содержит элемент проекта.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Чтобы добавить мастер пакета VSIX  
  
1.  В **обозревателе решений**, откройте контекстное меню **source.extension.vsixmanifest** файлу в проекте CustomActionProjectItem и нажмите кнопку **откройте** для открытия файл в редакторе манифестов.  
  
2.  В редакторе манифеста выберите **активы** вкладку, а затем выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
3.  В **тип** выберите **Microsoft.VisualStudio.Assembly**.  
  
4.  В **источника** выберите **проект в текущем решении**.  
  
5.  В **проекта** выберите **ItemTemplateWizard**, а затем выберите **ОК** кнопки.  
  
6.  В строке меню выберите **построения**, **построить решение**, а затем убедитесь, что решение компилируется без ошибок.  
  
## <a name="testing-the-wizard"></a>Тестирование мастера  
 Теперь все готово для тестирования мастера. Начните отладку решение CustomActionProjectItem в экспериментальном экземпляре Visual Studio. Затем протестируйте мастер для элемента проекта настраиваемого действия в проект SharePoint в экспериментальном экземпляре Visual Studio. Наконец сборку и запуск проекта SharePoint, чтобы убедиться, что настраиваемое действие работает должным образом.  
  
#### <a name="to-start-to-debug-the-solution"></a>Чтобы приступить к отладке решения  
  
1.  Перезапустите Visual Studio с правами администратора и откройте решение CustomActionProjectItem.  
  
2.  В проекте ItemTemplateWizard, откройте файл кода CustomActionWizard и затем добавьте точку останова в первой строке кода в `RunStarted` метод.  
  
3.  В строке меню выберите **отладки**, **исключения**.  
  
4.  В **исключения** диалогового окна поле, убедитесь, что **вызванное** и **пользовательским кодом** флажки для **исключения среды CLR**очищаются, а затем выберите **ОК** кнопки.  
  
5.  Запустите отладку, нажав клавишу F5 или в строке меню, выбрав **отладки**, **начать отладку**.  
  
     Visual Studio устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 действия проекта и запускает экспериментальный экземпляр Visual Studio. В этом экземпляре Visual Studio, вы сможете протестировать элемент проекта.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Чтобы проверить мастер в Visual Studio  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **файл**, **New**, **проекта**.  
  
2.  Разверните **Visual C#** или **Visual Basic** разверните узел (в зависимости от языка, поддерживаемого шаблоном элемента), **SharePoint** узел, а затем выберите **2010** узла.  
  
3.  В списке шаблонов проектов выберите **проект SharePoint 2010**, назовите проект **CustomActionWizardTest**, а затем выберите **ОК** кнопки.  
  
4.  В **мастер настройки SharePoint**, введите URL-адрес сайта, который требуется использовать для отладки и нажмите кнопку **Готово** кнопки.  
  
5.  В **обозреватель решений**, откройте контекстное меню узла проекта и последовательно выберите **добавить**, а затем выберите **новый элемент**.  
  
6.  В **добавить новый элемент — CustomItemWizardTest** диалогового окна разверните **SharePoint** узел и разверните **2010** узла.  
  
7.  В списке элементов проекта, выберите **пользовательское действие** элемента, а затем выберите **добавить** кнопки.  
  
8.  Убедитесь, что код в другом экземпляре Visual Studio прервано на точке останова, заданной ранее в `RunStarted` метод.  
  
9. Продолжить отладку проекта, нажав клавишу F5 или выберите в строке меню, выберите **отладки**, **Продолжить**.  
  
     Появится мастер настройки SharePoint.  
  
10. В разделе **расположение**, выберите **редактирование списка** переключатель.  
  
11. В **идентификатор группы** выберите **связи**.  
  
12. В **заголовок** введите **центр разработки SharePoint**.  
  
13. В **описание** введите **открывает центр разработки SharePoint веб-сайт**.  
  
14. В **URL-адрес** введите **http://msdn.microsoft.com/sharepoint/default.aspx**, а затем выберите **Готово** кнопки.  
  
     isual Studio добавляет элемент с именем **CustomAction1** в проект и открывает файл Elements.xml в редакторе. Убедитесь, что файл Elements.xml содержит значения, которые указаны в мастере.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Чтобы протестировать пользовательское действие в SharePoint  
  
1.  В экспериментальном экземпляре Visual Studio, нажмите клавишу F5 или, в строке меню выберите **отладки**, **начать отладку**.  
  
     Пользовательское действие является упаковываются и развертываются на сайте SharePoint, определяемое **URL-адрес сайта** свойства проекта и веб-браузере откроется страница по умолчанию этого сайта.  
  
    > [!NOTE]  
    >  Если **отладка скриптов отключена** диалоговое окно, выберите **Да** кнопки.  
  
2.  В области списки на сайте SharePoint, выберите **задачи** ссылку.  
  
     **Задачи: все задачи** появится страница.  
  
3.  На **Инструменты списка** вкладку на ленте, выберите **списка** вкладку и затем в **параметры** выберите **параметры списка**.  
  
     **Параметры списка** появится страница.  
  
4.  В разделе **связи** заголовок в верхней части страницы выберите **центр разработки SharePoint** связывания, убедитесь, что в браузере будет открыта веб-сайт http://msdn.microsoft.com/sharepoint/default.aspxи затем закройте браузер.  
  
## <a name="cleaning-up-the-development-computer"></a>Очистка компьютера разработчика  
 После завершения тестирования элемента проекта удалите шаблон элемента проекта из экспериментального экземпляра Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Очистка компьютера разработчика  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **средства**, **расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В списке расширений выберите **элемент проекта настраиваемого действия** расширения и нажмите кнопку **удаления** кнопки.  
  
3.  В появившемся диалоговом окне, выберите **Да** кнопку, чтобы убедиться, что вы хотите удалить расширение, а затем выберите **Перезагрузить сейчас** кнопку, чтобы завершить удаление.  
  
4.  Закройте оба экземпляра Visual Studio (экспериментальный экземпляр и экземпляр Visual Studio, в котором открыт решение CustomActionProjectItem).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Определение типов элементов проектов SharePoint, пользовательские](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Справочник по схеме шаблонов Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Как: использование мастеров для шаблонов проектов](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [Идентификаторы и расположения настраиваемое действие по умолчанию](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  