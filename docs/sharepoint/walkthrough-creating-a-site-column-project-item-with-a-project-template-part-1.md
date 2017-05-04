---
title: "Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "элементы проекта SharePoint, определение собственных типов"
  - "элементы проекта [разработка приложений SharePoint в Visual Studio], определение собственных типов"
  - "проекты SharePoint, создание пользовательских шаблонов"
  - "разработка приложений SharePoint в Visual Studio, определение новых типов элементов проектов"
ms.assetid: b53d48d7-cbf2-45c2-9537-06a6819be397
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1
  Проекты SharePoint представляют собой контейнеры для одного или нескольких элементов проекта SharePoint.  Можно расширить систему проектов SharePoint в Visual Studio путем создания собственных типов элементов проектов SharePoint и затем связать их с шаблоном проекта.  В данном пошаговом руководстве показано, как определить тип элемента проекта для создания столбца сайта, а затем создать шаблон проекта, позволяющий создать новый проект, содержащий элемент "столбец сайта".  
  
 В этом пошаговом руководстве показано выполнение следующих задач.  
  
-   Создание расширения Visual Studio, в котором определяется новый тип элемента проекта SharePoint для столбца сайта.  Тип элемента проекта содержит простое пользовательское свойство, отображаемое в окне **Свойства**.  
  
-   Создание шаблона элемента проекта [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] для данного элемента проекта.  
  
-   Построение пакета расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) для развертывания шаблона проекта и сборки расширения.  
  
-   Отладка и тестирование элемента проекта.  
  
 Это пошаговое руководство является отдельным.  По завершении данного пошагового руководства вы сможете усовершенствовать элемент проекта, добавив мастер в шаблон проекта.  Для получения дополнительной информации см. [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
>  Можно загрузить пример, который содержит проекты завершена, код и другие файлы для этого пошагового руководства из следующего расположения: [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Обязательные компоненты  
 Для выполнения данного пошагового руководства на компьютере разработчика должны быть установлены следующие компоненты:  
  
-   Поддерживаемые выпуски Microsoft Windows, SharePoint и [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Для получения дополнительной информации см. [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  В этом пошаговом руководстве шаблон **Проект VSIX** из пакета SDK используется для создания пакета VSIX, который служит для развертывания элемента проекта.  Для получения дополнительной информации см. [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Возможно, знание следующего подхода пригодится, однако оно не требуется для выполнения пошагового руководства.  
  
-   Столбцы сайтов в SharePoint.  Дополнительные сведения см. в [Столбцы](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
-   Шаблоны проектов в Visual Studio.  Для получения дополнительной информации см. [Создание пользовательских шаблонов проектов и элементов в Visual Studio](../ide/creating-project-and-item-templates.md).  
  
## Создание проектов  
 Чтобы выполнить это пошаговое руководство, необходимо создать три проекта:  
  
-   Проект VSIX.  Этот проект содержит пакет VSIX для развертывания элемента проекта "столбец сайта" и шаблона проекта.  
  
-   Проект шаблона проекта.  Этот проект создает шаблон проекта, с помощью которого можно создать новый проект SharePoint, содержащий элемент "столбец сайта".  
  
-   Проект библиотеки классов.  Этот проект реализует расширение Visual Studio, определяющее поведение элемента проекта "столбец сайта".  
  
 Начните выполнение пошагового руководства с создания проектов.  
  
#### Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите **Создать**, **Проект**.  
  
3.  В верхней части диалогового окна **Создание проекта** убедитесь, что **.NET Framework 4.5** выбрано в списке версий платформы .NET Framework.  
  
4.  Разверните узел **Visual Basic** или **Visual C\#**, а затем выберите узел **Расширение среды**.  
  
    > [!NOTE]  
    >  Узел **Расширение среды** доступен только в том случае, если необходимо установить пакет SDK для Visual Studio.  Дополнительные сведения см. в параграфе предварительных требований ранее в этом разделе.  
  
5.  В списке шаблонов проектов выберите **Проект VSIX**.  
  
6.  В поле **Имя** введите **SiteColumnProjectItem**, а затем нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавляет проект **SiteColumnProjectItem** в **Обозреватель решений**.  
  
#### Создание проекта шаблона проекта  
  
1.  В **Обозреватель решений** откройте контекстное меню для узла решения, выберите **Добавить**, а затем выберите **Создание проекта**.  
  
    > [!NOTE]  
    >  В проектах Visual Basic узел решения отображается в **обозревателе решений**, только если в диалоговом окне ["Общие", страница "Проекты и решения", диалоговое окно "Параметры"](http://msdn.microsoft.com/ru-ru/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) установлен флажок **Всегда показывать решение**.  
  
2.  В верхней части диалогового окна **Создание проекта** убедитесь, что **.NET Framework 4.5** выбрано в списке версий платформы .NET Framework.  
  
3.  Разверните узел **Visual C\#** или **Visual Basic**, а затем выберите узел **Расширение среды**.  
  
4.  В списке шаблонов проектов выберите шаблон **Шаблон проекта C** или **Шаблон проекта Visual Basic**.  
  
5.  В поле **Имя** введите **SiteColumnProjectTemplate**, а затем нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит проект **SiteColumnProjectTemplate** в решение.  
  
6.  Удалите из проекта файл c кодом Class1.  
  
7.  Если создан проект Visual Basic, необходимо также удалить из проекта следующие файлы:  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.settings  
  
#### Создание проекта расширения  
  
1.  В **Обозреватель решений** откройте контекстное меню для узла решения, выберите **Добавить**, а затем выберите **Создание проекта**.  
  
2.  В верхней части диалогового окна **Создание проекта** убедитесь, что **.NET Framework 4.5** выбрано в списке версий платформы .NET Framework.  
  
3.  Разверните узел **Visual C\#** или узел **Visual Basic**, выберите **Окна**, а затем выберите шаблон **Библиотека классов**.  
  
4.  В поле **Имя** введите **ProjectItemTypeDefinition**, а затем нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавит проект **ProjectItemTypeDefinition** в решение и откроет файл кода по умолчанию Class1.  
  
5.  Удалите из проекта файл c кодом Class1.  
  
## Настройка проекта расширения  
 Добавьте ссылки на файлы с кодом и сборки для настройки проекта расширения.  
  
#### Настройка проекта  
  
1.  В проекте ProjectItemTypeDefinition добавьте с файлом под именем **SiteColumnProjectItemTypeProvider**.  
  
2.  В меню **Проект** выберите **Добавить ссылку**.  
  
3.  В диалоговом окне **Диспетчер ссылок — ProjectItemTypeDefinition** разверните узел **Сборки**, выберите узел **основа**, а затем выделите флажок System.ComponentModel.Composition.  
  
4.  Выберите узел **Расширения** выберите флажок рядом с сборкой Microsoft.VisualStudio.SharePoint, а затем нажмите кнопку **ОК**.  
  
## Определение нового типа элемента проекта SharePoint  
 Создайте класс, реализующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>, чтобы определить поведение нового типа элемента проекта.  Этот интерфейс следует реализовывать всякий раз, когда требуется определить новый тип элемента проекта.  
  
#### Определение нового типа элемента проекта SharePoint  
  
1.  В файле кода **SiteColumnProjectItemTypeProvider** замените код по умолчанию следующим кодом, и сохраните файл.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## Создание шаблона проекта Visual Studio  
 Можно создать шаблон проекта, вы разрешаете другим разработчикам, создающим проекты SharePoint, содержащие элементы проекта столбца сайта.  Шаблон проекта SharePoint содержит файлы, необходимые для всех проектов в Visual Studio, например файлы CSPROJ или VBPROJ VSTEMPLATE и файлы, относящихся к проектам SharePoint.  Для получения дополнительной информации см. [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 В этой процедуре создается пустой проект SharePoint для создания файлов, относящихся к проектам SharePoint.  Затем необходимо добавить их в проект SiteColumnProjectTemplate, чтобы они были включены в шаблон, созданный из этого проекта.  Можно также настроить файл проекта SiteColumnProjectTemplate, указав местоположение шаблона проекта в диалоговом окне **Создание проекта**.  
  
#### Создание файлов для шаблона проекта  
  
1.  Запустите второй экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с правами администратора.  
  
2.  Создайте файл с именем **BaseSharePointProject** проекта SharePoint 2010.  
  
    > [!IMPORTANT]  
    >  В поле **Мастер настройки SharePoint** не выделите переключатель **Развернуть как решение фермы**.  
  
3.  Добавьте пустой элемент в проект и назовите элемент **Field1**.  
  
4.  Сохраните проект, а затем закройте второй экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5.  В экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], где открыто решение SiteColumnProjectItem, в **Обозреватель решений**, чтобы открыть контекстное меню для узла проекта **SiteColumnProjectTemplate**, выберите **Добавить**, затем выберите **Существующий элемент**.  
  
6.  В диалоговом окне **Добавление существующего элемента**, чтобы открыть список расширений файлов, а затем выберите **Все файлы \(\*.\*\)**.  
  
7.  В папке, содержащей проект BaseSharePointProject, выделите файл key.snk, а затем нажмите кнопку **Добавить**.  
  
    > [!NOTE]  
    >  В этом пошаговом руководстве, шаблон проекта, который будет создан использует тот же файл key.snk подписи для каждого проекта, созданного с помощью шаблона.  Чтобы получить сведения о том, как развернуть в этом примере, чтобы создать новый файл key.snk для каждого экземпляра проекта см. в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8.  Повторите шаги 5\-8, добавив следующие файлы из указанных вложенных папок в каталоге BaseSharePointProject:  
  
    -   \\Field1\\Elements.xml  
  
    -   \\Field1\\SharePointProjectItem.spdata  
  
    -   \\Features\\Feature1\\Feature1.feature  
  
    -   \\Features\\Feature1\\Feature1.Template.xml  
  
    -   \\Package\\Package.package  
  
    -   \\Package\\Package.Template.xml  
  
     Добавьте эти файлы непосредственно в проект SiteColumnProjectTemplate; не воссоздают вложенные папки Field1, функции или пакета в проекте.  Дополнительные сведения об этих файлах см. в разделе [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### Для настройки способа разработчиков шаблона проекта в диалоговом окне " новый проект "  
  
1.  В **Обозреватель решений** откройте контекстное меню для узла проекта **SiteColumnProjectTemplate** и выберите пункт **Выгрузить проект**.  При выводе запроса на сохранение изменений файлов, нажмите кнопку **Да**.  
  
2.  Раскрывайте контекстное меню узла **SiteColumnProjectTemplate** снова, после чего нажать кнопку **Правка SiteColumnProjectTemplate.csproj** или **Правка SiteColumnProjectTemplate.vbproj**.  
  
3.  В файле проекта, найдите следующий элемент `VSTemplate`.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Замените элемент следующим XML\-кодом.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Элемент `OutputSubPath` задает путь к дополнительным папкам, в которых при построении проекта создается шаблон проекта.  Заданные здесь папки обеспечивают доступность шаблона проекта будет доступен только клиенты при открытии диалогового окна **Создание проекта**, разверните узел **SharePoint**, а затем выбрать узел **2010**.  
  
5.  Сохраните и закройте файл.  
  
6.  В **Обозреватель решений** откройте контекстное меню для проекта **SiteColumnProjectTemplate** и выберите пункт **Перезагрузить проект**.  
  
## Редактирование файлов шаблона проекта  
 В проекте SiteColumnProjectTemplate, правка следующие файлы для определения расширения функциональности шаблона проекта:  
  
-   AssemblyInfo.cs или AssemblyInfo.vb  
  
-   Elements.xml  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.feature  
  
-   Package.package  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj или ProjectTemplate.vbproj  
  
 В следующих процедурах следует добавить подстановочные параметры в некоторые из этих файлов.  Подстановочный параметр токен, начинающийся и заканчивающийся знаком доллара \($\).  Когда пользователь использует этот шаблон проекта используется для создания проекта Visual Studio автоматически заменяет эти параметры в новом проекте конкретными значениями.  Для получения дополнительной информации см. [Подстановочные параметры](../sharepoint/replaceable-parameters.md).  
  
#### Изменение файла AssemblyInfo.cs или AssemblyInfo.vb  
  
1.  В проекте SiteColumnProjectTemplate, откройте файл AssemblyInfo.cs или AssemblyInfo.vb, а затем добавьте следующую выписка в начало его:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Если свойство проекта SharePoint **Изолированное решение** имеет значение **True**, Visual Studio добавляет атрибут <xref:System.Security.AllowPartiallyTrustedCallersAttribute> в файл кода AssemblyInfo.  Однако файл кода AssemblyInfo в шаблоне проекта не импортировать пространство имен <xref:System.Security> по умолчанию.  Необходимо добавить оператор **using** или **Imports** для предотвращения ошибок при компиляции.  
  
2.  Сохраните и закройте файл.  
  
#### Изменение файла Elements.xml  
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла Elements.xml следующим XML\-кодом.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Новый XML\-код добавляет элемент `Field`, определяющий имя столбца сайта, его базовый тип, и в какой группе коллекции он отображается.  Дополнительные сведения о содержимое этого файла см. в разделе [В схеме определения поля](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Сохраните и закройте файл.  
  
#### Редактирование файла SharePointProjectItem.spdata  
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла SharePointProjectItem.spdata следующим XML\-кодом.  
  
    ```  
  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     Новый XML\-код вносит следующие изменения в файл.  
  
    -   Изменить атрибут `Type` элемента `ProjectItem` становится строка, переданная атрибуту <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> определения элемента проекта \(класса `SiteColumnProjectItemTypeProvider`, который был создан ранее в этом пошаговом руководстве\).  
  
    -   Удаляет атрибуты `SupportedTrustLevels` и `SupportedDeploymentScopes` из элемента `ProjectItem`.  Эти значения атрибутов необязательны, потому что уровни доверия и области развертывания заданы в классе `SiteColumnProjectItemTypeProvider` проекта ProjectItemTypeDefinition.  
  
     Дополнительные сведения о содержимом SPDATA\-файлов см. в разделе [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2.  Сохраните и закройте файл.  
  
#### Изменение файла Feature1.feature  
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла Feature1.feature следующим XML\-кодом.  
  
    ```  
  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     Новый XML\-код вносит следующие изменения в файл.  
  
    -   Изменяет значения атрибутов `Id` и `featureId` элемента `feature` значение `$guid4$`.  
  
    -   Изменяет значения атрибута `itemId` элемента `projectItemReference` значение `$guid2$`.  
  
     Дополнительные сведения о FEATURE\-файлах см. в разделе [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Сохраните и закройте файл.  
  
#### Изменение файла Package.package  
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла Package.package следующим XML\-кодом.  
  
    ```  
  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     Новый XML\-код вносит следующие изменения в файл.  
  
    -   Изменяет значения атрибутов `Id` и `solutionId` элемента `package` значение `$guid3$`.  
  
    -   Изменяет значения атрибута `itemId` элемента `featureReference` значение `$guid4$`.  
  
     Дополнительные сведения о PACKAGE\-файлах см. в разделе [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Сохраните и закройте файл.  
  
#### Изменение файла SiteColumnProjectTemplate.vstemplate  
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла SiteColumnProjectTemplate.vstemplate одним из следующих фрагментов XML\-кода.  
  
    -   При создании шаблона проекта Visual C \#, используйте следующий XML\-код.  
  
    ```  
  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
    -   При создании шаблона проекта Visual Basic, используйте следующий XML\-код.  
  
    ```  
  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>VisualBasic</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Новый XML\-код вносит следующие изменения в файл.  
  
    -   Задает элемент `Name` значение **Столбец сайта**. \(Это имя отображается в диалоговом окне **Создание проекта** \).  
  
    -   Добавляет элементы `ProjectItem` для каждого filethat, включенные в каждом экземпляре проекта.  
  
    -   Использует пространство имен «http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005».  Другие файлы проекта в этом решении используют пространство имен «http:\/\/schemas.microsoft.com\/developer\/msbuild\/2003».  Поэтому будут созданы, но можно предупреждения схемы XML пропускают их в этом пошаговом руководстве.  
  
     Дополнительные сведения о содержимом VSTEMPLATE\-файлов см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
2.  Сохраните и закройте файл.  
  
#### Изменение файла ProjectTemplate.csproj или ProjectTemplate.vbproj  
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла файл ProjectTemplate.csproj или ProjectTemplate.vbproj одним из следующих фрагментов XML\-кода.  
  
    -   При создании шаблона проекта Visual C \#, используйте следующий XML\-код.  
  
    ```  
  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  При создании шаблона проекта Visual Basic, используйте следующий XML\-код.  
  
    ```  
  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     Новый XML\-код вносит следующие изменения в файл.  
  
    -   Элемент `TargetFrameworkVersion` используется для определения платформы .NET Framework 3.5, а не 4.5.  
  
    -   Добавляет элементы `SignAssembly` и `AssemblyOriginatorKeyFile` для подписания выходных данных проекта.  
  
    -   Добавляет элементы `Reference` для ссылок на сборки, проекты SharePoint используют.  
  
    -   Добавляет элементы для каждого файла по умолчанию в проекте, таких как Elements.xml и SharePointProjectItem.spdata.  
  
2.  Сохраните и закройте файл.  
  
## Создание пакета VSIX для развертывания шаблона проекта  
 Для развертывания расширения воспользуйтесь проектом VSIX в решении **SiteColumnProjectItem** для создания пакета VSIX.  Сначала настройте пакет VSIX, изменив содержимое файла source.extension.vsixmanifest, входящего в состав проекта VSIX.  Затем создайте пакет VSIX, выполнив построение решения.  
  
#### Настройка и создание пакета VSIX  
  
1.  В **Обозреватель решений** в проекте **SiteColumnProjectItem** откройте файл source.extension.vsixmanifest в редакторе манифестов.  
  
     Файл source.extension.vsixmanifest является основой для файла extension.vsixmanifest которого все пакеты VSIX требуют.  Дополнительные сведения об этом файле см. в разделе [Справочник по схеме расширения VSIX](http://msdn.microsoft.com/ru-ru/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В поле **Название продукта** введите **Столбец сайта**.  
  
3.  В поле **Автор** введите **Contoso**.  
  
4.  В поле **Описание** введите **Проект SharePoint для создания столбцы сайтов**.  
  
5.  Откройте вкладку **Активы**, а затем нажмите кнопку **Создать**.  
  
     Будет открыто диалоговое окно **Добавить новый актив**.  
  
6.  В списке **Тип** выберите **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Это значение соответствует элементу `ProjectTemplate`, описанному в файле extension.vsixmanifest.  Этот элемент определяет вложенную папку в пакете VSIX, содержащую шаблон проекта.  Для получения дополнительной информации см. [NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/ru-ru/87add64c-9dcd-495f-8815-209dab182cb1).  
  
7.  В списке **Источник** выберите **Проект в текущем решении**.  
  
8.  В списке **Проект**, и выберите команду **SiteColumnProjectTemplate**, а затем нажмите кнопку **ОК**.  
  
9. Выберите кнопку **Создать** еще раз.  
  
     Будет открыто диалоговое окно **Добавить новый актив**.  
  
10. В списке **Тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Это значение соответствует элементу `MefComponent`, описанному в файле extension.vsixmanifest.  Этот элемент задает имя сборки расширения в пакете VSIX.  Для получения дополнительной информации см. [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ru-ru/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. В списке **Источник** выберите **Проект в текущем решении**.  
  
12. В списке **Проект** выберите **ProjectItemTypeDefinition**, а затем нажмите кнопку **ОК**.  
  
13. В строке меню выберите **Построение**, **Построить решение**, а затем убедитесь, что проект компилируется без ошибок.  
  
## Проверка шаблона проекта  
 Шаблон проекта готов к тестированию.  Начните отладку решения SiteColumnProjectItem в экспериментальном экземпляре Visual Studio.  Затем протестируйте проект **столбца сайта** в экспериментальном экземпляре Visual Studio.  И наконец, выполните построение и запуск проекта SharePoint, чтобы проверить, что столбец сайта работает ожидаемым образом.  
  
#### Начало отладки решения  
  
1.  Перезапустите Visual Studio с правами администратора, а затем откройте решение SiteColumnProjectItem.  
  
2.  В файле кода SiteColumnProjectItemTypeProvider добавьте точку останова в первой строке кода в методе `InitializeType`, а затем выберите ключ **F5**, чтобы начать отладку.  
  
     Visual Studio установит расширение в папку %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Site Column\\1.0 и запустит экспериментальный экземпляр Visual Studio.  После этого можно тестировать элемент проекта в открытом экземпляре Visual Studio.  
  
#### Тестирование проекта в Visual Studio  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **Файл**, **Создать**, **Проект**.  
  
2.  Разверните узел **Visual C\#** или **Visual Basic** \(в зависимости от языка, шаблон проекта\), затем узел **SharePoint** и выберите узел **2010**.  
  
3.  В списке шаблонов проектов выберите шаблон **Столбец сайта**.  
  
4.  В поле **Имя** введите **SiteColumnTest**, а затем нажмите кнопку **ОК**.  
  
     В поле **Обозреватель решений**, отображается новый проект с именем **Поле1** элемента проекта.  
  
5.  Убедитесь, что выполнение кода в другом экземпляре Visual Studio прерывается на точке останова, заданные ранее в методе `InitializeType`, а затем выбрать ключ **F5**, чтобы продолжить для отладки проекта.  
  
6.  В **Обозреватель решений** выберите узел **Поле1** и выберите пункт **F4** ключ.  
  
     Будет открыто окно **Свойства**.  
  
7.  В свойствах списка, убедитесь, что свойство **Свойство Example**.  
  
#### Тестирование столбца сайта в SharePoint  
  
1.  В **Обозреватель решений** выберите узел **SiteColumnTest**.  
  
2.  В окне **Свойства** в текстовом поле рядом с свойством **URL\-адрес сайта**, введите **http:\/\/localhost**.  
  
     Этот шаг определяет локальный сайт SharePoint на компьютере разработчика, который требуется использовать для отладки.  
  
    > [!NOTE]  
    >  Свойство **URL\-адрес сайта** по умолчанию пустое, поскольку в шаблоне проекта столбца сайта не предоставляет мастер для получения этого значения при создании проекта.  Сведения о том, как добавить мастер, запрашивающий это значение у разработчика и настраивающий это свойство в новом проекте, см. в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Нажмите клавишу **F5**.  
  
     Столбец сайта передаются и развертывается на сайт SharePoint, который задан в свойстве **URL\-адрес сайта** проекта.  В веб\-браузере будет открыта страница по умолчанию для этого сайта.  
  
    > [!NOTE]  
    >  Если появится диалоговое окно **Отладка скриптов отключена**, нажмите кнопку **Да**, чтобы продолжить отладку проекта.  
  
4.  В меню **Действия сайта** выберите команду **Параметры сайта**.  
  
5.  На странице **Параметры сайта**, в списке **Коллекции** выберите ссылку **Столбцы сайта**.  
  
6.  В списке столбцов сайта, убедитесь, что команда **Настраиваемый столбец** содержит столбец с именем **SiteColumnTest**.  
  
7.  Закройте веб\-браузера.  
  
## Очистка компьютера разработчика  
 После завершения тестирования проекта удалите шаблон проекта из экспериментального экземпляра Visual Studio.  
  
#### Очистка компьютера разработчика  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **Сервис**, **Расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В списке расширений выберите расширение **Столбец сайта**, а затем нажмите кнопку **Удалить**.  
  
3.  В диалоговом окне, появившемся на экране, нажмите кнопку **Да**, чтобы подтвердить удаление расширения.  
  
4.  Нажмите кнопку **Закрыть** для завершения процесса удаления.  
  
5.  Закройте оба экземпляра Visual Studio \(экспериментальный экземпляр и экземпляр Visual Studio, в котором открыто решение SiteColumnProjectItem\).  
  
## Следующие действия  
 По завершении данного пошагового руководства вы можете добавить мастер в шаблон проекта.  Когда пользователь создает проект столбца сайта, мастер запрашивает у пользователя URL\-адрес сайта, используемый для отладки, и является ли решение изолированным. Мастер настраивает новый проект, используя эту информацию.  Мастер также собирает сведения о столбце \(например, его базовый тип и группу, в которой должен быть указан столбец в коллекции столбцов сайта\) и добавляет их в файл Elements.xml в новом проекте.  Для получения дополнительной информации см. [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## См. также  
 [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  