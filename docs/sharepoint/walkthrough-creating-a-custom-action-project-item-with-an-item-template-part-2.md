---
title: Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2 | Документация Майкрософт
ms.date: 02/02/2017
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
ms.openlocfilehash: 4305fd980252515f126df2c1b3848c0676cd2079
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913940"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2
  После определения пользовательского типа элемента проекта SharePoint и свяжите ее с шаблоном элемента в Visual Studio, можно также содержат мастер для шаблона. Мастер можно использовать для сбора сведений от пользователей, при использовании шаблона, чтобы добавить новый экземпляр элемента проекта в проект. Собранные сведения могут использоваться для инициализации элемента проекта.  
  
 В этом пошаговом руководстве вы добавите мастер элемента проекта настраиваемого действия, которое продемонстрировано в [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Когда пользователь добавляет элемент проекта настраиваемого действия в проект SharePoint, мастер собирает сведения о настраиваемого действия (например, его расположение и URL-адрес для перехода к, когда пользователь выбирает его) и добавляет эту информацию, чтобы *Elements.xml* файл в новый элемент проекта.  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание мастера для настраиваемого типа элемента проекта SharePoint, который связан с шаблоном элемента.  
  
-   Определение настраиваемого мастера пользовательского интерфейса, похожего на встроенный мастер для элементов проекта SharePoint в Visual Studio.  
  
-   Использование подстановочных параметров для инициализации файлов проекта SharePoint с данными, собранными в мастере.  
  
-   Отладка и тестирование мастера.  
  
> [!NOTE]  
>  Вы можете скачать пример из [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , показано, как создавать собственные действия для рабочего процесса.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства, необходимо сначала создать решение CustomActionProjectItem, выполнив [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Также необходимы следующие компоненты на компьютере разработчика для выполнения этого пошагового руководства:  
  
- Поддерживаемые версии Windows, SharePoint и Visual Studio.
  
- Visual Studio SDK. В этом пошаговом руководстве использует **проект VSIX** шаблона в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. в разделе [расширения инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Знание следующие основные понятия будут полезны, но не требуется для выполнения данного пошагового руководства:  
  
- Мастеров для шаблонов проектов и элементов в Visual Studio. Дополнительные сведения см. в разделе [Как Использование мастеров для шаблонов проектов](../extensibility/how-to-use-wizards-with-project-templates.md) и <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс.  
  
- Пользовательские действия в SharePoint. Дополнительные сведения см. в разделе [настраиваемое действие](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="create-the-wizard-project"></a>Создание проекта мастера
 Для выполнения этого пошагового руководства, необходимо добавить проект в решение CustomActionProjectItem, созданный в [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Вы реализуете <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейса и определения пользовательского интерфейса мастера в этом проекте.  
  
#### <a name="to-create-the-wizard-project"></a>Создание проекта мастера  
  
1.  В Visual Studio откройте решение CustomActionProjectItem  
  
2.  В **обозревателе решений**, откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
3.  В **новый проект** диалоговое окно последовательно раскройте элементы **Visual C#** или **Visual Basic** узлов, а затем выберите **Windows** узла.  
  
4.  В верхней части **новый проект** диалоговом окне убедитесь, что **.NET Framework 4.5** выбирается в списке версий .NET Framework.  
  
5.  Выберите **Библиотека пользовательских элементов управления WPF** шаблон проекта, присвойте проекту имя **ItemTemplateWizard**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **ItemTemplateWizard** проекта к решению.  
  
6.  Удалите элемент UserControl1 из проекта.  
  
## <a name="configure-the-wizard-project"></a>Настройка проекта мастера
 Перед созданием мастера, необходимо добавить окна Windows Presentation Foundation (WPF), файл кода и ссылки на сборки в проект.  
  
#### <a name="to-configure-the-wizard-project"></a>Настройка проекта мастера  
  
1.  В **обозревателе решений**, откройте контекстное меню из **ItemTemplateWizard** узел проекта, а затем выберите **свойства**.  
  
2.  В **конструктор проектов**, убедитесь, что требуемая версия .NET framework имеет значение .NET Framework 4.5.  
  
     Для проектов Visual C#, можно задать это значение на **приложения** вкладки. Для проектов Visual Basic, можно задать это значение на **компиляции** вкладки. Дополнительные сведения см. в разделе [Как определить целевую версию .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  В **ItemTemplateWizard** проект, добавить **Window (WPF)** элемент в проект, а затем введите имя элемента **WizardWindow**.  
  
4.  Добавьте два файла кода, которые называются CustomActionWizard и строки.  
  
5.  Откройте контекстное меню для **ItemTemplateWizard** проекта, а затем выберите **добавить ссылку**.  
  
6.  В **диспетчер ссылок - ItemTemplateWizard** диалогового **сборки** узел, выберите **расширения** узла.  
  
7.  Установите флажки рядом с следующие сборки, а затем выберите **ОК** кнопки:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  В **обозревателе решений**в **ссылки** выберите папку для проекта ItemTemplateWizard, **EnvDTE** ссылки.  
  
9. В **свойства** окна, измените значение свойства **Embed Interop Types** свойства **False**.  
  
## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Определив расположение по умолчанию и идентификатор строки для выполнения пользовательских действий
 Любого настраиваемого действия есть расположение и идентификатор, который указан в `GroupID` и `Location` атрибуты `CustomAction` элемент в *Elements.xml* файл. На этом этапе вы определите некоторые допустимые значения для этих атрибутов в проекте ItemTemplateWizard. После выполнения этого пошагового руководства, эти строки будут записываться *Elements.xml* файл элемента проекта настраиваемого действия, если пользователи указывают расположение и идентификатор, в мастере.  
  
 Для простоты в этом примере поддерживает только подмножество доступных по умолчанию расположений и идентификаторов. Полный список см. в разделе [по умолчанию действие настраиваемых расположений и идентификаторы](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Чтобы определить расположение по умолчанию и строки Идентификаторов
  
1.  Открыть.  
  
2.  В **ItemTemplateWizard** проект, замените код в файле кода строки со следующим кодом.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="create-the-wizard-ui"></a>Создание пользовательского интерфейса мастера
 Добавьте XAML для определения пользовательского интерфейса мастера и добавьте код для привязки элементов управления в мастере создания строк Идентификаторов. Мастер, который создается напоминает встроенного мастера для проектов SharePoint в Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>Для создания пользовательского интерфейса мастера
  
1.  В **ItemTemplateWizard** проекта, откройте контекстное меню для **WizardWindow.xaml** файл, а затем выберите **откройте** чтобы открыть окно в конструкторе.  
  
2.  В представлении XAML замените следующий XAML текущего XAML. XAML определяет пользовательский Интерфейс, содержащий заголовок, элементы управления для указания поведения настраиваемого действия и кнопки навигации в нижней части окна.  
  
    > [!NOTE]  
    >  Проект будет содержать некоторые ошибки компиляции, после добавления этого кода. Эти ошибки исчезнут при добавлении кода в последующих шагах.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  Окно, которое создается в этом XAML является производным от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> базового класса. При добавлении настраиваемого поля диалогового окна WPF в Visual Studio, мы рекомендуем, что диалоговое окно производными этого класса иметь согласованный Дизайн с другими диалоговыми окнами в Visual Studio и избежать проблем, которые могут возникать с модальные диалоговые окна. Дополнительные сведения см. в разделе [Создание и управление модальные диалоговые окна](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Если вы разрабатываете проект Visual Basic, удалите `ItemTemplateWizard` пространства имен из `WizardWindow` имени класса в `x:Class` атрибут `Window` элемента. Этот элемент находится в первой строке XAML. Когда все будет готово, первая строка должна выглядеть следующим образом:  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  В файле кода для файла WizardWindow.xaml замените текущий код следующим кодом.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implement-the-wizard"></a>Мастер реализации
 Определить функциональные возможности мастера путем реализации <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс.  
  
#### <a name="to-implement-the-wizard"></a>Реализация мастера  
  
1.  В **ItemTemplateWizard** откройте проект **CustomActionWizard** файл кода, а затем замените текущий код в этом файле следующим кодом:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Контрольная точка  
 На этом этапе в этом пошаговом руководстве, весь код для мастера теперь находится в проекте. Постройте проект, чтобы убедиться в том, что оно компилируется без ошибок.  
  
#### <a name="to-build-your-project"></a>Построение проекта  
  
1.  В строке меню последовательно выберите **Сборка**  >  **Собрать решение**.  
  
## <a name="associate-the-wizard-with-the-item-template"></a>Мастер взаимосвязей с помощью шаблона элемента
 Теперь, когда вы реализовали мастер, необходимо связать ее с **настраиваемое действие** шаблона элемента, выполнив три основных этапа:  
  
1.  Подпишите сборку строгим именем мастера.  
  
2.  Получение токена открытого ключа для сборки мастера.  
  
3.  Добавьте ссылку на сборку мастера в файле .vstemplate для **настраиваемое действие** шаблона элемента.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Чтобы подписать сборку строгим именем мастера  
  
1.  В **обозревателе решений**, откройте контекстное меню из **ItemTemplateWizard** узел проекта, а затем выберите **свойства**.  
  
2.  На **подписывание** выберите **подписать сборку** "флажок".  
  
3.  В **выберите файл ключа строгого имени** выберите  **\<создать... >**.  
  
4.  В **Создание ключа строгого имени** диалоговом окне введите имя, снимите флажок **защитить мой файл ключей паролем** флажок, а затем выберите **ОК** кнопку.  
  
5.  В строке меню последовательно выберите **Сборка**  >  **Собрать решение**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Чтобы получить маркер открытого ключа для сборки мастера  
  
1.  В окне командной строки Visual Studio, выполните следующую команду, заменив *PathToWizardAssembly* с указанием полного пути к ItemTemplateWizard.dll сборку для проекта ItemTemplateWizard на разработки компьютер.  
  
    ```xml  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Токен открытого ключа для *ItemTemplateWizard.dll* записи сборки в окно командной строки Visual Studio.  
  
2.  Не закрывайте окно командной строки Visual Studio. Вам потребуется токен открытого ключа для выполнения следующей процедуры.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Чтобы добавить ссылку в сборку мастера в VSTEMPLATE-файл  
  
1.  В **обозревателе решений**, разверните **ItemTemplate** узел проекта, а затем откройте *ItemTemplate.vstemplate* файла.  
  
2.  В конце файла добавьте следующий `WizardExtension` элемент между `</TemplateContent>` и `</VSTemplate>` теги. Замените *YourToken* значение `PublicKeyToken` атрибута с токен открытого ключа, полученный в предыдущей процедуре.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Дополнительные сведения о `WizardExtension` элемент, см. в разделе [элемент WizardExtension &#40;шаблоны Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Сохраните и закройте файл.  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Подстановочные параметры, чтобы добавить *Elements.xml* файл в шаблоне элемента
 Добавьте несколько подстановочных параметров для *Elements.xml* файл в проекте ItemTemplate. Эти параметры инициализируются в `PopulateReplacementDictionary` метод в `CustomActionWizard` класс, который вы задали ранее. Когда пользователь добавляет элемент проекта настраиваемого действия в проект, Visual Studio автоматически заменяет эти параметры в *Elements.xml* файл в новый элемент проекта со значениями, указанными в мастере.  
  
 Заменяемый параметр — это маркер, который начинается и заканчивается символом доллара ($). Кроме определения собственных подстановочных параметров, можно использовать встроенные параметры, системы проектов SharePoint определяет и инициализирует. Дополнительные сведения см. в разделе [подстановочных параметров](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Чтобы добавить подстановочные параметры для *Elements.xml* файла
  
1.  В проекте ItemTemplate, замените содержимое файла *Elements.xml* файл следующий XML-код.  
  
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
  
     Новый XML-код изменяет значения `Id`, `GroupId`, `Location`, `Description`, и `Url` атрибуты к подстановочных параметров.  
  
2.  Сохраните и закройте файл.  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>Мастер добавления в пакет VSIX
 В файле source.extension.vsixmanifest в проект VSIX добавьте ссылку на проект мастера, чтобы он развертывается в составе пакета VSIX, который содержит элемент проекта.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Чтобы добавить мастер пакет VSIX  
  
1.  В **обозревателе решений**, откройте контекстное меню из **source.extension.vsixmanifest** файл в проекте CustomActionProjectItem, а затем выберите **откройте** для открытия файл в редакторе манифестов.  
  
2.  В редакторе манифеста выберите **активы** , а затем выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
3.  В **тип** выберите **Microsoft.VisualStudio.Assembly**.  
  
4.  В **источника** выберите **проект в текущем решении**.  
  
5.  В **проекта** выберите **ItemTemplateWizard**, а затем выберите **ОК** кнопки.  
  
6.  В строке меню выберите **построения** > **построить решение**и убедитесь, что решение компилируется без ошибок.  
  
## <a name="test-the-wizard"></a>Протестируйте мастер
 Теперь вы готовы для тестирования мастер. Во-первых начните отладку решение CustomActionProjectItem в экспериментальном экземпляре Visual Studio. Затем протестируйте мастер для элемента проекта настраиваемого действия в проекте SharePoint в экспериментальном экземпляре Visual Studio. Наконец Постройте и запустите проект SharePoint, чтобы убедиться, что настраиваемое действие работает должным образом.  
  
#### <a name="to-start-to-debug-the-solution"></a>Чтобы начать отладку решения  
  
1.  Перезапустите Visual Studio от имени администратора и откройте решение CustomActionProjectItem.  
  
2.  В проекте ItemTemplateWizard, откройте файл кода CustomActionWizard и затем добавьте точку останова в первой строке кода в `RunStarted` метод.  
  
3.  В строке меню выберите **Отладка** > **исключения**.  
  
4.  В **исключения** диалоговом окне убедитесь, что **вызванное** и **не обработанное пользовательским кодом** флажки для **исключения среды CLR**очищаются, а затем выберите **ОК** кнопки.  
  
5.  Начать отладку, выбрав **F5** ключа, или в строке меню выберите **Отладка** > **начать отладку**.  
  
     Visual Studio устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 действия проекта и запускает экспериментальный экземпляр Visual Studio. В этом экземпляре Visual Studio будет тестировать элемент проекта.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Для тестирования мастер в Visual Studio  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **файл** > **New** > **проекта**.  
  
2.  Разверните **Visual C#** или **Visual Basic** (в зависимости от языка, который поддерживает шаблон элемента), раскройте **SharePoint** узел, а затем выберите **2010** узла.  
  
3.  В списке шаблонов проектов выберите **проект SharePoint 2010**, назовите проект **CustomActionWizardTest**, а затем выберите **ОК** кнопки.  
  
4.  В **мастер настройки SharePoint**, введите URL-адрес сайта, который вы хотите использовать для отладки, а затем выберите **Готово** кнопки.  
  
5.  В **обозревателе решений**, откройте контекстное меню для узла проекта, выберите **добавить**, а затем выберите **новый элемент**.  
  
6.  В **Добавление нового элемента — CustomItemWizardTest** диалоговое окно последовательно раскройте элементы **SharePoint** узел, а затем разверните **2010** узла.  
  
7.  В списке элементов проекта, выберите **настраиваемое действие** элемента, а затем выберите **добавить** кнопки.  
  
8.  Убедитесь, что выполнение кода в другом экземпляре Visual Studio будет приостановлено в точке останова, заданной ранее в `RunStarted` метод.  
  
9. Продолжить отладку проекта, выбрав **F5** ключа или в строке меню выберите **Отладка** > **Продолжить**.  
  
     Откроется мастер настройки SharePoint.  
  
10. В разделе **расположение**, выберите **редактирование списка** переключатель.  
  
11. В **идентификатор группы** выберите **Communications**.  
  
12. В **Title** введите **Центр разработчиков SharePoint**.  
  
13. В **описание** введите **открывается веб-сайт SharePoint Developer Center**.  
  
14. В **URL-адрес** введите **https://docs.microsoft.com/sharepoint/dev/**, а затем выберите **Готово** кнопки.  
  
     Visual Studio добавляет элемент с именем **CustomAction1** к проекту и откроется *Elements.xml* файл в редакторе. Убедитесь, что *Elements.xml* содержит значения, заданные в мастере.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Для проверки настраиваемого действия в SharePoint  
  
1.  В экспериментальном экземпляре Visual Studio, выберите **F5** ключа, либо в строке меню выберите **Отладка** > **начать отладку**.  
  
     Настраиваемое действие упаковывается и развертывается на сайте SharePoint, определяемое **URL-адрес сайта** свойства проекта и веб-браузер открывает страницу по умолчанию для этого сайта.  
  
    > [!NOTE]  
    >  Если **отладка скриптов отключена** открывшемся диалоговом окне выберите **Да** кнопки.  
  
2.  В области списков узла SharePoint, выберите **задачи** ссылку.  
  
     **Задачи — все задачи** появится страница.  
  
3.  На **Инструменты списка** вкладку на ленте, выберите **списка** вкладку, а затем в **параметры** группе, выберите **параметры списка**.  
  
     **Параметры списка** появится страница.  
  
4.  В разделе **Communications** заголовок в верхней части страницы выберите **Центр разработчиков SharePoint** связать, убедитесь, что в браузере откроется веб-сайт https://docs.microsoft.com/sharepoint/dev/, а затем закройте браузер.  
  
## <a name="cleaning-up-the-development-computer"></a>Очистка компьютера разработчика
 После завершения тестирования элемента проекта, удалите шаблона элемента проекта в экспериментальном экземпляре Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Для очистки компьютера разработчика  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **средства** > **расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В список расширений, выберите **элемент проекта настраиваемого действия** расширения, а затем выберите **удаления** кнопки.  
  
3.  В появившемся диалоговом окне, выберите **Да** кнопку, чтобы убедиться, что вы хотите удалить расширение, а затем выберите **Перезагрузить сейчас** кнопку, чтобы завершить удаление.  
  
4.  Закройте оба экземпляра Visual Studio (экспериментальный экземпляр и экземпляр Visual Studio, в котором открыто решение CustomActionProjectItem).  
  
## <a name="see-also"></a>См. также
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Создание шаблонов элементов и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Справочник по схеме шаблонов Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Практическое руководство. Использование мастеров для шаблонов проектов](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [Расположения по умолчанию настраиваемое действие и идентификаторы](http://go.microsoft.com/fwlink/?LinkId=181964)  
