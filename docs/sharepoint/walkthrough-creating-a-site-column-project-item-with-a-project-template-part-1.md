---
title: 'Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1 | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3d34c03d74aae6ba1fb82e7357b6159b261cc2ad
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119537"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1
  Проекты SharePoint являются контейнерами для одного или нескольких элементов проекта SharePoint. Системы проектов SharePoint в Visual Studio можно расширить путем создания собственных типов элементов проектов SharePoint и связывая их с шаблоном проекта. В этом пошаговом руководстве мы определим тип элемента проекта для создания столбца сайта, и затем вы создадите шаблон проекта, который может использоваться для создания нового проекта, содержащего элемента проекта столбца сайта.  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание расширения Visual Studio, который определяет новый тип элемента проекта SharePoint для столбца сайта. Тип элемента проекта содержит простое пользовательское свойство, которое отображается в **свойства** окна.  
  
-   Создание [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] шаблон проекта для элемента проекта.  
  
-   Построение [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакета Extension (VSIX) для развертывания шаблона проекта и сборки расширения.  
  
-   Отладка и тестирование элемента проекта.  
  
 Это автономный Пошаговое руководство. После выполнения этого пошагового руководства, элемент проекта можно улучшить, добавив мастер к шаблону проекта. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
> Ряд образцы рабочих процессов, см. в разделе [примеры рабочего процесса SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимы следующие компоненты на компьютере разработчика для выполнения этого пошагового руководства.  
  
-   Поддерживаемые версии Microsoft Windows, SharePoint и [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. В этом пошаговом руководстве использует **проект VSIX** шаблона в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. в разделе [расширения инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Знания следующие понятия будут полезны, но не требуется для выполнения данного пошагового руководства:  
  
-   Столбцы сайта в SharePoint. Дополнительные сведения см. в разделе [столбцы](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
-   Шаблоны проектов в Visual Studio. Дополнительные сведения см. в статье [Creating Project and Item Templates](/visualstudio/ide/creating-project-and-item-templates) (Создание шаблонов проектов и элементов).  
  
## <a name="create-the-projects"></a>Создание проектов
 Для выполнения этого пошагового руководства, необходимо создать три проекта:  
  
-   Проект VSIX. Этот проект создает пакет VSIX для развертывания элемента проекта столбца сайта и шаблона проекта.  
  
-   Проект шаблона проекта. Этот проект создает шаблон проекта, который может использоваться для создания нового проекта SharePoint, который содержит элемент проекта столбца сайта.  
  
-   Проект библиотеки классов. Этот проект, который реализует расширение Visual Studio, которое определяет поведение элемента проекта столбца сайта.  
  
 Начало выполнения пошагового руководства по созданию проектов.  
  
#### <a name="to-create-the-vsix-project"></a>Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В строке меню выберите **Файл** > **Создать** > **Проект**.  
  
3.  В верхней части **новый проект** диалоговом окне убедитесь, что **.NET Framework 4.5** выбирается в списке версий .NET Framework.  
  
4.  Разверните **Visual Basic** или **Visual C#** узлов, а затем выберите **расширяемости** узла.  
  
    > [!NOTE]  
    >  **Расширяемости** узел доступен только в том случае, если установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе "Предварительные требования" ранее в этом разделе.  
  
5.  В списке шаблонов проектов выберите **проект VSIX**.  
  
6.  В **имя** введите **SiteColumnProjectItem**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **SiteColumnProjectItem** проект **обозревателе решений**.  
  
#### <a name="to-create-the-project-template-project"></a>Создание проекта шаблона проекта  
  
1.  В **обозревателе решений**, откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В верхней части **новый проект** диалоговом окне убедитесь, что **.NET Framework 4.5** выбирается в списке версий .NET Framework.  
  
3.  Разверните **Visual C#** или **Visual Basic** узел, а затем выберите **расширяемости** узла.  
  
4.  В списке шаблонов проектов выберите **шаблон проекта C#** или **шаблон проекта Visual Basic** шаблона.  
  
5.  В **имя** введите **SiteColumnProjectTemplate**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **SiteColumnProjectTemplate** проекта к решению.  
  
6.  Удалите файл Class1 код из проекта.  
  
7.  Если вы создали проект Visual Basic, также удалите следующие файлы из проекта:  
  
    -   *MyApplication.Designer.vb*  
  
    -   MyApplication.myapp  
  
    -   *Местоположении Resources.resx*  
  
    -   *Resources.resx*  
  
    -   *Settings.Designer.vb*  
  
    -   Settings.Settings  
  
#### <a name="to-create-the-extension-project"></a>Создание проекта расширения  
  
1.  В **обозревателе решений**, откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В верхней части **новый проект** диалоговом окне убедитесь, что **.NET Framework 4.5** выбирается в списке версий .NET Framework.  
  
3.  Разверните **Visual C#** или **Visual Basic** , выберите **Windows** узел, а затем выберите **библиотеки классов** шаблона.  
  
4.  В **имя** введите **ProjectItemTypeDefinition** и выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **ProjectItemTypeDefinition** проекта в решение и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
## <a name="configure-the-extension-project"></a>Настройка проекта расширения
 Добавьте файлы кода и ссылки на сборки, чтобы настроить проект расширения.  
  
#### <a name="to-configure-the-project"></a>Настройка проекта  
  
1.  В проекте ProjectItemTypeDefinition, добавьте файл кода, который называется **SiteColumnProjectItemTypeProvider**.  
  
2.  В строке меню выберите **проекта** > **добавить ссылку**.  
  
3.  В **диспетчер ссылок - ProjectItemTypeDefinition** диалогового окна разверните узел **сборки** узел, выберите **Framework** узел, а затем выберите Флажок System.ComponentModel.Composition.  
  
4.  Выберите **расширения** узел, установите флажок рядом с Microsoft.VisualStudio.SharePoint сборки и выберите **ОК** кнопки.  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>Определение нового типа элементов проектов SharePoint
 Создайте класс, реализующий <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейса позволяет определить поведение нового типа элемента проекта. Реализуйте этот интерфейс, каждый раз, когда требуется определить новый тип элемента проекта.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Для определения нового типа элемента проекта SharePoint  
  
1.  В **SiteColumnProjectItemTypeProvider** файл кода, замените код по умолчанию следующим кодом и затем сохраните файл.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="create-a-visual-studio-project-template"></a>Создать шаблон проекта Visual Studio
 Создание шаблона проекта, как разрешить другим разработчикам для создания проектов SharePoint, которые содержат элементы проекта столбца сайта. Шаблон проекта SharePoint включает в себя файлы, которые необходимы для всех проектов в Visual Studio, такие как *.csproj* или *.vbproj* и *.vstemplate* файлы, а также файлы, характерные для проектов SharePoint. Дополнительные сведения см. в разделе [создание элементов, шаблоны и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 В этой процедуре создайте пустой проект SharePoint для создания файлов, характерные для проектов SharePoint. Вы затем добавьте эти файлы в проект SiteColumnProjectTemplate таким образом, чтобы они включены в шаблон, который создается из этого проекта. Также настроить для указания расположения шаблона проекта в файле проекта SiteColumnProjectTemplate **новый проект** диалоговое окно.  
  
#### <a name="to-create-the-files-for-the-project-template"></a>Чтобы создать файлы для шаблона проекта  
  
1.  Запустите второй экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] с учетными данными администратора.  
  
2.  Создать проект SharePoint 2010, которая называется **BaseSharePointProject**.  
  
    > [!IMPORTANT]  
    >  В **мастер настройки SharePoint**, не выбирайте **развернуть как решение фермы** переключатель.  
  
3.  Добавьте пустой элемент в проект и назовите элемент **Field1**.  
  
4.  Сохраните проект, а затем закройте второй экземпляр [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5.  В экземпляре [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SiteColumnProjectItem открытия решения, который имеет в **обозревателе решений**, откройте контекстное меню для **SiteColumnProjectTemplate** узел проекта, выберите  **Добавить**, а затем выберите **существующий элемент**.  
  
6.  В **добавить существующий элемент** диалоговое окно, откройте список расширений файлов и выберите **все файлы (\*.\*)** .  
  
7.  В каталоге, в которой содержится проект BaseSharePointProject, выберите файл key.snk и выберите **добавить** кнопки.  
  
    > [!NOTE]  
    >  В этом пошаговом руководстве шаблон проекта, который создается использует один и тот же файл key.snk для подписывания каждого проекта, который создается с помощью шаблона. Чтобы узнать, как расширить этот пример, чтобы создать файл key.snk разных для каждого экземпляра проекта, см. в разделе [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8.  Повторите шаги 5 – 8, чтобы добавить следующие файлы из указанных вложенных папок в каталоге BaseSharePointProject:  
  
    -   *\Field1\Elements.XML*  
  
    -   *\Field1\SharePointProjectItem.SPDATA*  
  
    -   *\Features\Feature1\Feature1.Feature*  
  
    -   *\Features\Feature1\Feature1.Template.XML*  
  
    -   *\Package\Package.Package*  
  
    -   *\Package\Package.Template.XML*  
  
     Добавьте эти файлы непосредственно в проект SiteColumnProjectTemplate; не повторно создать вложенные папки Field1, компонентов или пакет в проекте. Дополнительные сведения об этих файлах см. в разделе [создание элементов, шаблоны и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Чтобы настроить как для разработчиков шаблона проекта в диалоговом окне нового проекта
  
1.  В **обозревателе решений**, откройте контекстное меню для **SiteColumnProjectTemplate** узел проекта, а затем выберите **выгрузить проект**. Если вам будет предложено сохранить изменения во все файлы, выберите **Да** кнопки.  
  
2.  Откройте контекстное меню для **SiteColumnProjectTemplate** опять же, узел и выберите **изменить SiteColumnProjectTemplate.csproj** или **изменить SiteColumnProjectTemplate.vbproj**.  
  
3.  В файле проекта найдите следующие `VSTemplate` элемент.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Замените следующий код XML этого элемента.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` Элемент задает дополнительные папки в пути, в рамках которой создается шаблон проекта при сборке проекта. Папки, указанные здесь убедитесь, что шаблон проекта будет доступен только в том случае, когда клиенты открыть **новый проект** диалогового окна разверните узел **SharePoint** узел и нажмите кнопку **2010**  узла.  
  
5.  Сохраните и закройте файл.  
  
6.  В **обозревателе решений**, откройте контекстное меню для **SiteColumnProjectTemplate** проекта, а затем выберите **перезагрузить проект**.  
  
## <a name="edit-the-project-template-files"></a>Измените файлы шаблона проекта
 В проекте SiteColumnProjectTemplate измените следующие файлы для определения поведения шаблона проекта:  
  
-   *AssemblyInfo.cs* или *AssemblyInfo.vb*  
  
-   *Elements.XML*  
  
-   *SharePointProjectItem.spdata*  
  
-   *Feature1.Feature*  
  
-   *Package.Package*  
  
-   *SiteColumnProjectTemplate.vstemplate*  
  
-   *ProjectTemplate.csproj* или *ProjectTemplate.vbproj*  
  
 В следующих процедурах вы добавите подстановочных параметров некоторые из этих файлов. Заменяемый параметр — это маркер, который начинается и заканчивается символом доллара ($). Когда пользователь использует этот шаблон проекта для создания проекта, Visual Studio автоматически заменяет эти параметры в новом проекте с определенными значениями. Дополнительные сведения см. в разделе [подстановочных параметров](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Чтобы изменить в файле AssemblyInfo.cs или AssemblyInfo.vb
  
1.  В проекте SiteColumnProjectTemplate, откройте *AssemblyInfo.cs* или *AssemblyInfo.vb* файл, а затем добавьте следующую инструкцию в верхнюю часть его:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Когда **изолированное решение** проекта SharePoint свойству **True**, Visual Studio добавляет <xref:System.Security.AllowPartiallyTrustedCallersAttribute> в файл кода AssemblyInfo. Тем не менее, не импортирует файл кода AssemblyInfo в шаблоне проекта <xref:System.Security> пространство имен по умолчанию. Его необходимо добавить **с помощью** или **Imports** инструкцию, чтобы предотвратить ошибки компиляции.  
  
2.  Сохраните и закройте файл.  
  
#### <a name="to-edit-the-elementsxml-file"></a>Чтобы изменить файл Elements.xml
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла *Elements.xml* файл следующий XML-код.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Добавляет нового XML `Field` элемент, который определяет имя столбца сайта, его базовый тип и группы, в которой будет указан столбец сайта в коллекции. Дополнительные сведения о содержимом этого файла см. в разделе [схема определения полей](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Сохраните и закройте файл.  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Чтобы изменить файл SharePointProjectItem.spdata
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла *SharePointProjectItem.spdata* файл следующий XML-код.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     Новый XML-код вносит следующие изменения в файл:  
  
    -   Изменения `Type` атрибут `ProjectItem` элемент ту же строку, которая передается <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> в определении элемента проекта ( `SiteColumnProjectItemTypeProvider` класс, созданный ранее в этом пошаговом руководстве).  
  
    -   Удаляет `SupportedTrustLevels` и `SupportedDeploymentScopes` атрибуты из `ProjectItem` элемент. Значения этих атрибутов являются необязательными, поскольку уровни доверия и области развертывания указываются в `SiteColumnProjectItemTypeProvider` класс в проекте ProjectItemTypeDefinition.  
  
     Дополнительные сведения о содержимом *.spdata* файлы, см. в разделе [Справочник по схеме для элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2.  Сохраните и закройте файл.  
  
#### <a name="to-edit-the-feature1feature-file"></a>Чтобы изменить файл Feature1.feature
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла *Feature1.feature* файл следующий XML-код.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     Новый XML-код вносит следующие изменения в файл:  
  
    -   Изменяет значения `Id` и `featureId` атрибуты `feature` элемент `$guid4$`.  
  
    -   Изменяет значения `itemId` атрибут `projectItemReference` элемент `$guid2$`.  
  
     Дополнительные сведения о *.feature* файлы, см. в разделе [создание элементов, шаблоны и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Сохраните и закройте файл.  
  
#### <a name="to-edit-the-packagepackage-file"></a>Чтобы изменить файл Package.package
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла *Package.package* файл следующий XML-код.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     Новый XML-код вносит следующие изменения в файл:  
  
    -   Изменяет значения `Id` и `solutionId` атрибуты `package` элемент `$guid3$`.  
  
    -   Изменяет значения `itemId` атрибут `featureReference` элемент `$guid4$`.  
  
     Дополнительные сведения о *пакета* файлы, см. в разделе [создание элементов, шаблоны и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Сохраните и закройте файл.  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Чтобы изменить файл sitecolumnprojecttemplate.vstemplate
  
1.  В проекте SiteColumnProjectTemplate Замените содержимое файла SiteColumnProjectTemplate.vstemplate с одним из следующих разделов XML.  
  
    -   Если вы создаете шаблон проекта Visual C#, используйте следующий код XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
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
  
    -   Если вы создаете шаблон проекта Visual Basic, используйте следующий код XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
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
  
     Новый XML-код вносит следующие изменения в файл:  
  
    -   Наборы `Name` равным значению **столбец сайта**. (Это имя отображается в **новый проект** диалоговое окно).  
  
    -   Добавляет `ProjectItem` элементы для каждого filethat включенных в каждый экземпляр проекта.  
  
    -   Использует пространство имен "http://schemas.microsoft.com/developer/vstemplate/2005«. Другие файлы проекта в этом решении используется "http://schemas.microsoft.com/developer/msbuild/2003" пространства имен. Таким образом создается предупреждение схемы XML-сообщения, но их можно игнорировать в этом пошаговом руководстве.  
  
     Дополнительные сведения о содержимом *.vstemplate* файлы, см. в разделе [Справочник по схеме для Visual Studio шаблон](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
2.  Сохраните и закройте файл.  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Чтобы изменить файл projecttemplate.csproj или projecttemplate.vbproj
  
1.  В проекте SiteColumnProjectTemplate, замените содержимое файла *ProjectTemplate.csproj* файл или *ProjectTemplate.vbproj* файл с одним из следующих разделов XML.  
  
    -   Если вы создаете шаблон проекта Visual C#, используйте следующий код XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
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
  
    1.  Если вы создаете шаблон проекта Visual Basic, используйте следующий код XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
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
  
     Новый XML-код вносит следующие изменения в файл:  
  
    -   Использует `TargetFrameworkVersion` элемента, чтобы указать на .NET Framework 3.5, не 4.5.  
  
    -   Добавляет `SignAssembly` и `AssemblyOriginatorKeyFile` элементы для подписания выходных файлов проекта.  
  
    -   Добавляет `Reference` элементы для сборки ссылается на, использующих проектов SharePoint.  
  
    -   Добавляет элементы для каждого файла по умолчанию в проекте, такие как *Elements.xml* и *SharePointProjectItem.spdata*.  
  
2.  Сохраните и закройте файл.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Создание пакета VSIX для развертывания шаблона проекта
 Чтобы развернуть расширение, используйте проект VSIX в **SiteColumnProjectItem** решение, чтобы создать пакет VSIX. Во-первых настройте пакет VSIX, изменив файл source.extension.vsixmanifest, включенный в проект VSIX. Затем создайте пакет VSIX, построения решения.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Настройка и создание пакета VSIX  
  
1.  В **обозревателе решений**в **SiteColumnProjectItem** проекта, откройте файл source.extension.vsixmanifest в редакторе манифестов.  
  
     Файл source.extension.vsixmanifest является основой для файл extension.vsixmanifest, требующий всех пакетов VSIX. Дополнительные сведения об этом файле см. в разделе [Справочник по схеме 1.0 VSIX расширения](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В **название продукта** введите **столбец сайта**.  
  
3.  В **автор** введите **Contoso**.  
  
4.  В **описание** введите **проект SharePoint для создания столбцов сайта**.  
  
5.  Выберите **активы** вкладке, а затем выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
6.  В **тип** выберите **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Это значение соответствует `ProjectTemplate` элемент в файл extension.vsixmanifest. Этот элемент определяет вложенную папку в пакете VSIX, содержащий шаблон проекта. Дополнительные сведения см. в разделе [ProjectTemplate элемент (Схема VSX)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1).  
  
7.  В **источника** выберите **проект в текущем решении**.  
  
8.  В **проекта** , а нажмите **SiteColumnProjectTemplate**, а затем выберите **ОК** кнопку.  
  
9. Выберите **New** еще раз.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
10. В **тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Это значение соответствует `MefComponent` элемент в файл extension.vsixmanifest. Этот элемент задает имя сборки расширения в пакете VSIX. Дополнительные сведения см. в разделе [MEFComponent элемент (Схема VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. В **источника** выберите **проект в текущем решении**.  
  
12. В **проекта** выберите **ProjectItemTypeDefinition**, а затем выберите **ОК** кнопки.  
  
13. В строке меню выберите **построения** > **построить решение**и убедитесь, что проект компилируется без ошибок.  
  
## <a name="test-the-project-template"></a>Проверка шаблона проекта
 Теперь вы готовы для тестирования шаблона проекта. Начните отладку решения SiteColumnProjectItem в экспериментальном экземпляре Visual Studio. Затем протестируйте **столбец сайта** проект в экспериментальном экземпляре Visual Studio. Наконец создайте и запустите проект SharePoint, чтобы убедиться, что столбец сайта работает должным образом.  
  
#### <a name="to-start-debugging-the-solution"></a>Чтобы начать отладку решения  
  
1.  Перезапустите Visual Studio от имени администратора и откройте решение SiteColumnProjectItem.  
  
2.  
  
3.  В файле кода SiteColumnProjectItemTypeProvider добавьте точку останова в первой строке кода в `InitializeType` метод, а затем выберите **F5** клавишу, чтобы начать отладку.  
  
     Visual Studio устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 и запускает экспериментальный экземпляр Visual Studio. Элемент проекта будут тестироваться в этот экземпляр Visual Studio.  
  
#### <a name="to-test-the-project-in-visual-studio"></a>Тестирование проекта в Visual Studio  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **файл** > **New** > **проекта**.  
  
2.  Разверните **Visual C#** или **Visual Basic** (в зависимости от языка, который поддерживает шаблон проекта), раскройте **SharePoint** узел, а затем выберите **2010** узла.  
  
3.  В списке шаблонов проектов выберите **столбец сайта** шаблона.  
  
4.  В **имя** введите **SiteColumnTest** и выберите **ОК** кнопки.  
  
     В **обозревателе решений**, новый проект появляется с элементом проекта, который называется **Field1**.  
  
5.  Убедитесь, что выполнение кода в другом экземпляре Visual Studio будет приостановлено в точке останова, заданной ранее в `InitializeType` метод, а затем выберите **F5** клавишу, чтобы продолжить отладку проекта.  
  
6.  В **обозревателе решений**, выберите **Field1** узел, а затем выберите **F4** ключ.  
  
     **Свойства** откроется окно.  
  
7.  Убедитесь, что в списке свойств свойство **примером свойства** отображается.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Проверяемый столбец сайта в SharePoint  
  
1.  В **обозревателе решений**, выберите **SiteColumnTest** узла.  
  
2.  В **свойства** окно, в текстовом поле рядом с **URL-адрес сайта** свойство, введите **http://localhost**.  
  
     Этот шаг определяет локальный сайт SharePoint на компьютере разработчика, который вы хотите использовать для отладки.  
  
    > [!NOTE]  
    >  **URL-адрес сайта** свойство является пустым по умолчанию, так как шаблон проекта столбца сайта не содержат мастер для получения этого значения при создании проекта. Чтобы узнать, как добавить мастер, который запрашивает разработчика это значение, а затем настраивает это свойство в новом проекте, см. в разделе [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Нажмите клавишу **F5**.  
  
     Столбец сайта упаковывается и развертывается на сайте SharePoint, который указан в **URL-адрес сайта** свойство проекта. Веб-браузер открывает страницу по умолчанию для этого сайта.  
  
    > [!NOTE]  
    >  Если **отладка скриптов отключена** открывшемся диалоговом окне выберите **Да** кнопку, чтобы продолжить отладку проекта.  
  
4.  На **действия сайта** меню, выберите **параметры сайта**.  
  
5.  На **параметры сайта** раздела **галереи** выберите **столбцы сайта** ссылку.  
  
6.  В списке столбцов сайта, убедитесь, что **настраиваемые столбцы** группа содержит столбец с именем **SiteColumnTest**.  
  
7.  Закройте веб-браузер.  
  
## <a name="clean-up-the-development-computer"></a>Очистка компьютера разработчика
 После завершения тестирования проекта, удалите шаблон проекта в экспериментальном экземпляре Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Для очистки компьютера разработчика  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **средства** > **расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В список расширений, выберите **столбец сайта** расширения, а затем выберите **удаления** кнопку.  
  
3.  В появившемся диалоговом окне, выберите **Да** кнопку, чтобы убедиться, что вы хотите удалить расширение.  
  
4.  Выберите **закрыть** кнопку, чтобы завершить удаление.  
  
5.  Закройте оба экземпляра Visual Studio (экспериментальный экземпляр и экземпляр Visual Studio, в котором открыто решение SiteColumnProjectItem).  
  
## <a name="next-steps"></a>Следующие шаги
 После выполнения этого пошагового руководства, мастер можно добавить к шаблону проекта. Когда пользователь создает проект столбца сайта, мастер запрашивает у пользователя для сайта URL-адрес, используемый для отладки и ли новое решение хранятся в изолированной среде, и мастер настроит новый проект с помощью этой информации. Мастер также собирает сведения о столбце (например, базовый тип и группы, в которой будет указан столбец в коллекции столбцов сайта) и добавляет эту информацию, чтобы *Elements.xml* файл в новом проекте. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>См. также
 [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Определение пользовательских типов элементов проектов SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Создание шаблонов элементов и шаблоны проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Сохранение данных в расширениях системы проектов SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Связывать пользовательские данные с расширениями средств SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
