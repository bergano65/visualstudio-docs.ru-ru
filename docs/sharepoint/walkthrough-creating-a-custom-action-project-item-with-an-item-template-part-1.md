---
title: 'Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1 | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e690d18bae72b59234f2f90cbcf903b9941df7d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1"></a>Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1
  Системы проектов SharePoint в Visual Studio можно расширить путем создания собственного проекта типов элементов. В этом пошаговом руководстве вы создадите элемент проекта, который может быть добавлен в проект SharePoint для создания настраиваемого действия на сайте SharePoint. Это настраиваемое действие добавляет пункт меню, чтобы **действия сайта** на сайте SharePoint.  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание расширения Visual Studio, который определяет новый тип элемента проекта SharePoint для пользовательского действия. Новый тип элемента проекта реализовано несколько настраиваемых возможностей:  
  
    -   Контекстное меню, которое служит в качестве отправной точки для дополнительных задач, связанных с элементом проекта, например отображение конструктора для пользовательского действия в Visual Studio.  
  
    -   Код, выполняемый при изменении разработчиком определенных свойств элемента проекта, содержащего его элемента проекта.  
  
    -   Пользовательский значок, отображаемый рядом с элементом проекта в **обозревателе решений**.  
  
-   Создание шаблона элемента Visual Studio для элемента проекта.  
  
-   Построение пакета расширения Visual Studio (VSIX) для развертывания шаблона элемента проекта и сборки расширения.  
  
-   Отладка и тестирование элемента проекта.  
  
 Это изолированный Пошаговое руководство. После выполнения этого пошагового руководства, элемент проекта можно улучшить, добавив мастер в шаблоне элемента. Дополнительные сведения см. в разделе [Пошаговое руководство: создание элемент проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  Вы можете загрузить пример, содержащий завершенные проекты, код и другие файлы для этого пошагового руководства из следующего расположения: [ http://go.microsoft.com/fwlink/?LinkId=191369 ](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимы следующие компоненты на компьютере разработчика для выполнения данного пошагового руководства.  
  
-   Поддерживаемые версии Microsoft Windows, SharePoint и Visual Studio. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. В этом пошаговом руководстве используется **проект VSIX** шаблона в пакете SDK для создания пакета VSIX для развертывания элемента проекта. Дополнительные сведения см. в разделе [расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Изучением приведенных ниже концепций будет полезно, хотя и не требуется для выполнения данного пошагового руководства.  
  
-   Настраиваемые действия в SharePoint. Дополнительные сведения см. в разделе [пользовательское действие](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Шаблоны элементов в Visual Studio. Дополнительные сведения см. в статье [Creating Project and Item Templates](/visualstudio/ide/creating-project-and-item-templates) (Создание шаблонов проектов и элементов).  
  
## <a name="creating-the-projects"></a>Создание проектов  
 Для выполнения данного пошагового руководства, необходимо создать три проекта:  
  
-   Проект VSIX. Этот проект создает пакет VSIX для развертывания элемента проекта SharePoint.  
  
-   Проект шаблона элемента. Этот проект создает шаблон элемента, который можно использовать для добавления элемента проекта SharePoint в проект SharePoint.  
  
-   Проект библиотеки классов. Этот проект реализует расширение Visual Studio, которое определяет поведение элемента проекта SharePoint.  
  
 Пошаговое руководство начинается с создания проектов.  
  
#### <a name="to-create-the-vsix-project"></a>Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
3.  В списке в верхней части **новый проект** диалогового окна поле, убедитесь, что **.NET Framework 4.5** выбран.  
  
4.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic** узлов и нажмите кнопку **расширяемости** узла.  
  
    > [!NOTE]  
    >  **Расширяемости** узел доступен, только если установлен пакет SDK для Visual Studio. Дополнительные сведения см. в разделе предварительных требований этого раздела.  
  
5.  Выберите **проект VSIX** шаблона.  
  
6.  В **имя** введите **CustomActionProjectItem**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **CustomActionProjectItem** проекта **обозревателе решений**.  
  
#### <a name="to-create-the-item-template-project"></a>Создание проекта шаблона элемента  
  
1.  В **обозреватель решений**откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В списке в верхней части **новый проект** диалогового окна поле, убедитесь, что **.NET Framework 4.5** выбран.  
  
3.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic** узлов и нажмите кнопку **расширяемости** узла.  
  
4.  В списке шаблонов проектов выберите **шаблона элемента C#** или **шаблона элемента Visual Basic** шаблона.  
  
5.  В **имя** введите **ItemTemplate**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **ItemTemplate** проекта в решение.  
  
#### <a name="to-create-the-extension-project"></a>Создание проекта расширения  
  
1.  В **обозреватель решений**откройте контекстное меню узла решения, выберите **добавить**, а затем выберите **новый проект**.  
  
2.  В списке в верхней части **новый проект** диалогового окна поле, убедитесь, что **.NET Framework 4.5** выбран.  
  
3.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic** , выберите **Windows** узел, а затем выберите  **Библиотека классов** шаблона проекта.  
  
4.  В **имя** введите **ProjectItemDefinition**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Добавляет **ProjectItemDefinition** в решение проект и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
## <a name="configuring-the-extension-project"></a>Настройка проекта расширения  
 Прежде чем писать код, чтобы определить тип элемента проекта SharePoint, необходимо добавить файлы кода и ссылок на сборки в проект расширения.  
  
#### <a name="to-configure-the-project"></a>Настройка проекта  
  
1.  В **обозревателе решений**, откройте контекстное меню для **ProjectItemDefinition** проекта, выбор **добавить**, затем выберите **новый элемент**.  
  
2.  В списке элементов проекта, выберите **файл кода**.  
  
3.  В **имя** введите имя **настраиваемое действие** соответствующим расширение имени файла, а затем выберите **добавить** кнопки.  
  
4.  В **обозревателе решений**, откройте контекстное меню для **ProjectItemDefinition** проекта, а затем выберите **добавить ссылку**.  
  
5.  В **диспетчер ссылок - ProjectItemDefinition** диалогового окна выберите **сборки** узел и выберите **Framework** узла.  
  
6.  Установите флажок радом с каждым из следующих сборок:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms.  
  
7.  Выберите **расширения** узла, установите флажок рядом с Microsoft.VisualStudio.Sharepoint сборки и выберите **ОК** кнопки.  
  
## <a name="defining-the-new-sharepoint-project-item-type"></a>Определение нового типа элемента проекта SharePoint  
 Создайте класс, реализующий <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> интерфейс, чтобы определить поведение нового типа элемента проекта. Реализуйте этот интерфейс, каждый раз, когда требуется определить новый тип элемента проекта.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Для определения нового типа элемента проекта SharePoint  
  
1.  В проекте ProjectItemDefinition откройте файл кода настраиваемое действие.  
  
2.  Замените код в этот файл следующий код.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]  
  
## <a name="creating-an-icon-for-the-project-item-in-solution-explorer"></a>Создание значка для элемента проекта в обозревателе решений  
 При создании пользовательского элемента проекта SharePoint, изображения (значка или точечного рисунка) можно связать с элементом проекта. Это изображение отображается рядом с элементом проекта в **обозревателе решений**.  
  
 В следующей процедуре создается значок для элемента проекта и внедрения в сборку расширения значок. Этот значок ссылается <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> из `CustomActionProjectItemTypeProvider` класса, которое было создано ранее.  
  
#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Чтобы создать пользовательский значок для элемента проекта  
  
1.  В **обозревателе решений**, откройте контекстное меню для **ProjectItemDefinition** проекта, выбор **добавить**, а затем выберите **новый элемент...** .  
  
2.  В списке элементов проекта, выберите **файл значка** элемента.  
  
    > [!NOTE]  
    >  В проектах Visual Basic необходимо выбрать **Общие** узел, чтобы отобразить **файл значка** элемента.  
  
3.  В **имя** введите **CustomAction_SolutionExplorer.ico**, а затем выберите **добавить** кнопки.  
  
     Значок «Создать» открывается в **редактора изображений**.  
  
4.  Измените версию файла значок 16 x 16, чтобы его структуру может распознать, а затем сохраните файл значка.  
  
5.  В **обозревателе решений**, выберите **CustomAction_SolutionExplorer.ico**.  
  
6.  В **свойства** окно, щелкните стрелку рядом с **действие при построении** свойство.  
  
7.  В появившемся списке выберите **внедренный ресурс**.  
  
## <a name="checkpoint"></a>Контрольная точка  
 На этом этапе в пошаговом руководстве, весь код для элемента проекта теперь находится в проекте. Построение проекта, чтобы убедиться, что оно компилируется без ошибок.  
  
#### <a name="to-build-your-project"></a>Построение проекта  
  
1.  Откройте контекстное меню для **ProjectItemDefinition** проект и выберите **сборки**.  
  
## <a name="creating-a-visual-studio-item-template"></a>Создание шаблона элемента Visual Studio  
 Чтобы включить другие разработчики также могли использовать созданный элемент проекта, необходимо создать шаблон проекта или шаблона элемента. Разработчики используют эти шаблоны в Visual Studio для создания экземпляра элемента проекта путем создания нового проекта или при добавлении элемента в существующий проект. В этом пошаговом руководстве используется проект ItemTemplate для настройки элемента проекта.  
  
#### <a name="to-create-the-item-template"></a>Создание шаблона элемента  
  
1.  Удалите файл Class1 код из проекта ItemTemplate.  
  
2.  В проекте ItemTemplate откройте файл ItemTemplate.vstemplate.  
  
3.  Замените содержимое файла следующим кодом XML, а затем сохраните и закройте файл.  
  
    > [!NOTE]  
    >  Следующий XML-код предназначен для шаблона элемента Visual C#. При создании шаблона элемента Visual Basic, замените значение `ProjectType` элемент с `VisualBasic`.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Этот файл определяет содержимое и поведение шаблона элемента. Дополнительные сведения о содержимом этого файла см. в разделе [Справочник схеме шаблонов Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
4.  В **обозревателе решений**, откройте контекстное меню для **ItemTemplate** проекта, выбор **добавить**, а затем выберите **новый элемент**.  
  
5.  В **Добавление нового элемента** диалогового окна выберите **текстовый файл** шаблона.  
  
6.  В **имя** введите **CustomAction.spdata**, а затем выберите **добавить** кнопки.  
  
7.  Добавьте следующий код XML в файл CustomAction.spdata и затем сохраните и закройте файл.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Этот файл содержит сведения о файлах, содержащихся в элемент проекта. `Type` Атрибут `ProjectItem` необходимо задать элемент ту же строку, которая передается <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> для определения элемента проекта ( `CustomActionProjectItemTypeProvider` класс, созданный ранее в этом пошаговом руководстве). Дополнительные сведения о содержимом SPDATA-файлов см. в разделе [Справочник по схеме элементов проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  В **обозревателе решений**, откройте контекстное меню для **ItemTemplate** проекта, выбор **добавить**, а затем выберите **новый элемент**.  
  
9. В **Добавление нового элемента** диалогового окна выберите **XML-файл** шаблона.  
  
10. В **имя** введите **Elements.xml**, а затем выберите **добавить** кнопки.  
  
11. Замените содержимое файла Elements.xml следующий XML-код, а затем сохраните и закройте файл.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Этот файл определяет настраиваемое действие по умолчанию и создает пункт меню **действия сайта** на сайте SharePoint. Когда пользователь выбирает пункт меню, URL-адрес указан в `UrlAction` элемент откроется в веб-браузере. Дополнительные сведения об XML-элементах, можно использовать для определения настраиваемого действия см. в разделе [определений настраиваемых действий](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. При необходимости откройте файл ItemTemplate.ico и измените его так, чтобы он имеет вид, который может распознать. Значок будет отображаться рядом с элементом проекта в **Добавление нового элемента** диалоговое окно.  
  
13. В **обозревателе решений**, откройте контекстное меню для **ItemTemplate** проекта, а затем выберите **выгрузить проект**.  
  
14. Откройте контекстное меню для **ItemTemplate** проекта еще раз, а затем выберите **изменить ItemTemplate.csproj** или **изменить ItemTemplate.vbproj**.  
  
15. Выберите следующее `VSTemplate` элемента в файле проекта.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Введите здесь `VSTemplate` элемент с следующий XML-код, а затем сохраните и закройте файл.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` Элемент указывает дополнительные папки в пути, что при построении проекта создается шаблон элемента. Заданные здесь папки убедитесь, что шаблон элемента будут доступны только в том случае, если открыть клиентов **Добавление нового элемента** диалогового окна разверните **SharePoint** узел и выберите **2010**  узла.  
  
17. В **обозревателе решений**, откройте контекстное меню для **ItemTemplate** проекта, а затем выберите **перезагрузить проект**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item"></a>Создание пакета VSIX для развертывания элемента проекта  
 Для развертывания расширения, используйте проект VSIX в решении для создания пакета VSIX. Во-первых настройте пакет VSIX, изменив файл source.extension.vsixmanifest, включенный в проект VSIX. Затем создайте пакет VSIX с построением решения.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Для настройки и создания пакета VSIX  
  
1.  В **обозревателе решений**, откройте контекстное меню для **source.extension.vsixmanifest** файлу в проекте CustomActionProjectItem и нажмите кнопку **откройте**.  
  
     Visual Studio открывает файл в редакторе манифестов. Файл source.extension.vsixmanifest является основой для файл extension.vsixmanifest, требующий все пакеты VSIX. Дополнительные сведения об этом файле см. в разделе [ссылки 1.0 схемы расширения VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В **название продукта** введите **элемент проекта настраиваемого действия**.  
  
3.  В **автор** введите **Contoso**.  
  
4.  В **описание** введите **элемент проекта SharePoint, который представляет настраиваемое действие**.  
  
5.  На **активы** выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
6.  В **тип** выберите **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Это значение соответствует `ItemTemplate` элемент в файл extension.vsixmanifest. Этот элемент определяет вложенную папку в пакете VSIX, который содержит шаблон элемента проекта. Дополнительные сведения см. в разделе [элемента ItemTemplate (Схема VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
7.  В **источника** выберите **проект в текущем решении**.  
  
8.  В **проекта** выберите **ItemTemplate**, а затем выберите **ОК** кнопки.  
  
9. В **активы** выберите **New** еще раз.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
10. В **тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Это значение соответствует `MefComponent` элемент в файл extension.vsixmanifest. Этот элемент задает имя сборки расширения в пакете VSIX. Дополнительные сведения см. в разделе [MEFComponent элемент (Схема VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. В **источника** выберите **проект в текущем решении**.  
  
12. В **проекта** выберите **ProjectItemDefinition**.  
  
13. Нажмите кнопку **ОК** .  
  
14. В строке меню выберите **построения**, **построить решение**, а затем убедитесь, что проект компилируется без ошибок.  
  
15. Убедитесь, что выходную папку построения для проекта CustomActionProjectItem содержит файл CustomActionProjectItem.vsix.  
  
     По умолчанию является выходной папке сборки... папку \bin\debug в папке, содержащей CustomActionProjectItem проекта.  
  
## <a name="testing-the-project-item"></a>Тестирование элемента проекта  
 Теперь все готово для проверки элемента проекта. Начните отладку решение CustomActionProjectItem в экспериментальном экземпляре Visual Studio. Затем для проверки **пользовательское действие** элемент проекта в проект SharePoint в экспериментальном экземпляре Visual Studio. Наконец сборку и запуск проекта SharePoint, чтобы убедиться, что настраиваемое действие работает должным образом.  
  
#### <a name="to-start-debugging-the-solution"></a>Чтобы начать отладку решения  
  
1.  Перезапустите Visual Studio с правами администратора и откройте решение CustomActionProjectItem.  
  
2.  Откройте файл кода настраиваемое действие и затем добавьте точку останова в первой строке кода в `InitializeType` метод.  
  
3.  Выберите **F5** клавишу, чтобы начать отладку.  
  
     Visual Studio устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 действия проекта и запускает экспериментальный экземпляр Visual Studio. В этом экземпляре Visual Studio, вы сможете протестировать элемент проекта.  
  
#### <a name="to-test-the-project-item-in-visual-studio"></a>Чтобы протестировать элемент проекта в Visual Studio  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **файл**, **New**, **проекта**.  
  
2.  Разверните **Visual C#** или **Visual Basic** (в зависимости от языка, поддерживаемого шаблоном элемента), разверните **SharePoint**, а затем выберите **2010**  узла.  
  
3.  В списке шаблонов проектов выберите **проект SharePoint 2010**.  
  
4.  В **имя** введите **CustomActionTest**, а затем выберите **ОК** кнопки.  
  
5.  В **мастер настройки SharePoint**, введите URL-адрес сайта, который требуется использовать для отладки и нажмите кнопку **Готово** кнопки.  
  
6.  В **обозреватель решений**, откройте контекстное меню узла проекта и последовательно выберите **добавить**, а затем выберите **новый элемент**.  
  
7.  В **Добавление нового элемента** диалогового окна выберите **2010** узле **SharePoint** узла.  
  
     Убедитесь, что **пользовательское действие** элемент появляется в списке элементов проекта.  
  
8.  Выберите **пользовательское действие** элемента, а затем выберите **добавить** кнопки.  
  
     Visual Studio добавляет элемент с именем **CustomAction1** в проект и открывает файл Elements.xml в редакторе.  
  
9. Убедитесь, что код в другом экземпляре Visual Studio прервано на точке останова, заданной ранее в `InitializeType` метод.  
  
10. Выберите **F5** клавишу, чтобы продолжить отладку проекта.  
  
11. В экспериментальном экземпляре Visual Studio в **обозреватель решений**, откройте контекстное меню для **CustomAction1** узел, а затем выберите **Просмотр конструктора настраиваемых действий**.  
  
12. Убедитесь, что появляется окно сообщения, а затем выберите **ОК** кнопки.  
  
     Это контекстное меню можно использовать для предоставления Дополнительные параметры и команды для разработчиков, например отображение конструктора для настраиваемого действия.  
  
13. В строке меню выберите **представление**, **вывода**.  
  
     **Вывода** открывается окно.  
  
14. В **обозревателе решений**, откройте контекстное меню для **CustomAction1** элемента, а затем измените ее имя на **MyCustomAction**.  
  
     В **вывода** окна, появится окно подтверждения. Это сообщение записывается в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> обработчика событий, определенных в `CustomActionProjectItemTypeProvider` класса. Можно обработать это событие и других событий элемента проекта, чтобы реализовать пользовательское поведение, если разработчик изменяет элемент проекта.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Чтобы протестировать пользовательское действие в SharePoint  
  
1.  В экспериментальном экземпляре Visual Studio, откройте файл Elements.xml, который является дочерним объектом **MyCustomAction** элемент проекта.  
  
2.  В файле Elements.xml внести следующие изменения и затем сохраните файл:  
  
    -   В `CustomAction` , задайте `Id` атрибут GUID или любую другую уникальную строку, как показано в следующем примере:  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   В `CustomAction` , задайте `Title` атрибут, как показано в следующем примере:  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   В `CustomAction` , задайте `Description` атрибут, как показано в следующем примере:  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   В `UrlAction` , задайте `Url` атрибут, как показано в следующем примере:  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  Нажмите клавишу F5.  
  
     Пользовательское действие является упаковываются и развертываются на сайте SharePoint, которая указана в **URL-адрес сайта** свойство проекта. Веб-браузере откроется страница по умолчанию этого сайта.  
  
    > [!NOTE]  
    >  Если **отладка скриптов отключена** диалоговое окно, выберите **Да** кнопку, чтобы продолжить отладку проекта.  
  
4.  На **действия сайта** меню, выберите **центр разработки SharePoint**, убедитесь, что в браузере будет открыта веб-сайт http://msdn.microsoft.com/sharepoint/default.aspxи закройте веб-браузер.  
  
## <a name="cleaning-up-the-development-computer"></a>Очистка компьютера разработчика  
 После завершения тестирования элемента проекта удалите шаблон элемента проекта из экспериментального экземпляра Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Очистка компьютера разработчика  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **средства**, **расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В список расширений, выберите **элемент проекта настраиваемого действия**, а затем выберите **удаления** кнопки.  
  
3.  В появившемся диалоговом окне, выберите **Да** кнопку, чтобы убедиться, что вы хотите удалить расширение.  
  
4.  Выберите **Перезагрузить сейчас** кнопку, чтобы завершить удаление.  
  
5.  Закройте экспериментальный экземпляр Visual Studio и экземпляр, в котором открыт решение CustomActionProjectItem.  
  
## <a name="next-steps"></a>Следующие шаги  
 После выполнения этого пошагового руководства, можно добавить мастер для шаблона элемента. При добавлении пользователем элемента проекта настраиваемого действия в проект SharePoint, мастер собирает сведения о действии (например, его расположение и URL-адрес для перехода при выборе действия) и добавляет их в файл Elements.xml в новый элемент проекта. Дополнительные сведения см. в разделе [Пошаговое руководство: создание элемент проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Определение типов элементов проектов SharePoint, пользовательские](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Создание шаблонов элементов и проектов для элементов проектов SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Справочник по схеме шаблонов Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Редактор изображений для значков](/cpp/windows/image-editor-for-icons)   
 [Создание значка или другого изображения &#40;редактор изображений для значков&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  