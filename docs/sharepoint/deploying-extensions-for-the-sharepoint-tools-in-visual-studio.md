---
title: "Deploying Extensions for the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, deploying extensions"
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Deploying Extensions for the SharePoint Tools in Visual Studio
  Чтобы развернуть расширение инструментов SharePoint, создайте пакет расширения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\), который содержит сборку расширения и любые другие файлы, которые предполагается распространять с расширением.  Пакет VSIX — это сжатый файл, удовлетворяющий стандарту Open Packaging Conventions \(OPC\).  Для пакетов VSIX используется расширение VSIX.  
  
 После создания пакета VSIX другие пользователи могут запустить VSIX\-файл для установки расширения.  Когда пользователь установит расширение, все файлы перед установлены %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11,0 \\ extensions.  Чтобы развернуть расширение, можно загрузить пакет VSIX на веб\-сайт [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) или распределить пакет среди клиентов другим способом, таким как размещение пакета в сетевой папке или на другом веб\-сайте.  
  
 Дополнительные сведения о создании пакетов VSIX и их развертывании в [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) см. в разделе [Расширения Visual Studio доставки](../extensibility/shipping-visual-studio-extensions.md).  
  
 Создать пакет VSIX можно, используя шаблон **Проект VSIX** в Visual Studio или вручную.  
  
## Использование проектов VSIX для создания пакетов VSIX  
 Можно использовать шаблон **Проект VSIX** предоставленные, что пакет Visual Studio SDK создан пакеты VSIX для расширений инструментов SharePoint.  Использование проекта VSIX предоставляет несколько преимуществ перед созданием пакета VSIX вручную.  
  
-   Visual Studio автоматически генерирует пакет VSIX при выполнении построения проекта.  Такие задания, как добавление файлов развертывания в пакет и создание XML\-файлов по типам содержимого для пакета, уже выполнены.  
  
-   Проект VSIX можно настроить так, чтобы в пакет VSIX включались выходные данные построения проекта расширения и другие файлы, такие как шаблоны проектов и элементов.  
  
 Дополнительные сведения об использовании проекта VSIX см. в разделе [Шаблон проекта VSIX](../extensibility/vsix-project-template.md).  
  
### Организация проектов  
 По умолчанию проекты VSIX создают только пакеты VSIX, но не сборки.  Поэтому в проектах VSIX обычно не реализовывают расширение средств SharePoint.  Как правило, в работе используется как минимум два проекта:  
  
-   Проект VSIX.  
  
-   Проект библиотеки классов, реализующий расширение.  
  
 Также можно использовать дополнительные проекты для некоторых типов расширений:  
  
-   Проект библиотеки классов, реализующий команды SharePoint, используемые в расширении.  Пошаговое руководство, в котором рассматривается такой сценарий, см. в разделе [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Проект шаблона элемента или проекта, создающий шаблон элемента или проекта, если в расширении определен новый тип элемента проекта SharePoint.  Пошаговое руководство, в котором рассматривается такой сценарий, см. в разделе [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Проект библиотеки классов, реализующий шаблон элемента или проекта, если в расширении содержится шаблон.  Пошаговое руководство, в котором рассматривается такой сценарий, см. в разделе [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 Если все проекты включаются в одно решение Visual Studio, можно изменить SOURCE.EXTENSION.VSIXMANIFEST\-файл в проекте VSIX, чтобы он включал в себя выходные данные построения проектов библиотеки классов.  
  
### Редактирование манифеста VSIX  
 Необходимо изменить файл source.extension.vsixmanifest в проекте VSIX, указав в нем все элементы, которые должны содержаться в расширении.  При открытии файла source.extension.vsixmanifest в контекстном меню выберите файл появится в конструкторе, который предоставляет пользовательский интерфейс для редактирования XML в файле.  Дополнительные сведения см. в разделе [Конструктор манифеста VSIX](../extensibility/media/vsix-manifest-designer.png).  
  
 В файл source.extension.vsixmanifest необходимо добавить записи о следующих элементах:  
  
-   Сборка расширения.  
  
-   Сборка, реализующая команды SharePoint, используемые в расширении.  
  
-   Шаблоны проектов и элементов, связанные с расширением.  
  
-   Настраиваемый мастер для шаблона, связанный с расширением.  
  
 В следующих процедурах описывается, как добавить записи о каждом из этих элементов в файл .vsixmanifest.  
  
##### Чтобы включить в файл сборку расширения, выполните следующие действия.  
  
1.  В проекте VSIX, открыть контекстное меню для файла source.extension.vsixmanifest, а затем выберите **Открыть**.  
  
     Открытие файла в конструкторе  
  
2.  На вкладке **Активы** редактор выберите кнопку **Создать**.  
  
     Будет открыто диалоговое окно **Добавить новый актив**.  
  
3.  В списке **Тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
4.  В списке **Источник**, выполните одно из следующих действий:  
  
    -   Если сборка расширения создана из проекта, являющегося тем же решением, что и проект VSIX выберите **Проект в текущем решении**.  В списке **Проект** выберите имя проекта.  
  
    -   Если сборка расширения включена, как файл в проекте выберите **Файл в файловой системе**.  В списке **Путь** введите полный путь к файлу сборки модуля или воспользуйтесь кнопкой **Обзор**, чтобы найти и выбрать файл сборки.  
  
5.  Нажмите кнопку **ОК**.  
  
##### Чтобы включить в файл сборку команды SharePoint, выполните следующие действия  
  
1.  В проекте VSIX, открыть контекстное меню для файла source.extension.vsixmanifest, а затем нажмите кнопку **Открыть**.  
  
     Открытие файла в конструкторе.  
  
2.  В разделе **Активы** редактор выберите кнопку **Создать**.  
  
     Будет открыто диалоговое окно **Добавить новый актив**.  
  
3.  В окне **Тип** введите **SharePoint.Commands.v4**.  
  
4.  В списке **Источник**, выполните одно из следующих действий:  
  
    -   Если сборка команды создана из проекта, являющегося тем же решением, что и проект VSIX выберите **Проект в текущем решении**.  В списке **Проект** выберите имя проекта.  
  
    -   Если сборка команды включена, как файл в проекте выберите **Файл в файловой системе**.  В списке **Путь** введите полный путь к файлу сборки модуля или воспользуйтесь кнопкой **Обзор**, чтобы найти и выбрать файл сборки.  
  
5.  Нажмите кнопку **ОК**.  
  
##### Включить шаблон, который будет создан  
  
1.  В проекте VSIX, открыть контекстное меню для файла source.extension.vsixmanifest, а затем нажмите кнопку **Открыть**.  
  
     Открытие файла в конструкторе.  
  
2.  В разделе **Активы** редактор выберите кнопку **Создать**.  
  
     Будет открыто диалоговое окно **Добавить новый актив**.  
  
3.  В списке **Тип** выберите **Microsoft.VisualStudio.ProjectTemplate** или **Microsoft.VisualStudio.ItemTemplate**.  
  
4.  В списке **Источник** выберите **Проект в текущем решении**.  
  
5.  В списке **Проект** выберите имя проекта, а затем нажмите кнопку **ОК**.  
  
6.  В **Обозреватель решений** открыть контекстное меню для выбранного шаблона проекта или шаблон элемента проекта, а затем выберите **Выгрузить проект**.  
  
7.  Раскрывайте контекстное меню для узла проекта, а затем выберите **Изменить***YourTemplateProjectName***csproj** или **Изменить***YourTemplateProjectName***vbproj**.  
  
8.  Найдите следующий элемент `VSTemplate` в файле проекта.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Замените этот элемент следующим XML\-кодом.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Элемент `OutputSubPath` задает путь к дополнительным папкам, в которых при построении проекта создается шаблон проекта.  Заданные здесь папки обеспечивают что шаблон элемента будет доступен, только если клиенты раскроют диалоговое окно **Добавить новый проект** разверните узел **SharePoint**, а затем выберите узел **2010**.  
  
10. Сохраните и закройте файл.  
  
11. В **Обозреватель решений** открыть контекстное меню для шаблона проекта или шаблон элемента проекта, а затем выберите **Перезагрузить проект**.  
  
##### Добавление шаблона, создаваемого вручную  
  
1.  В проекте VSIX добавьте новую папку к проекту для шаблона.  
  
2.  В новой папке создайте вложенные папки и затем добавьте шаблон \(ZIP\-файл\) в папку *код\_языка*.  
  
     *папка\_шаблона*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *код\_языка*  
  
     *YourTemplateName*.zip  
  
     Например, если есть шаблон элемента с именем ContosoCustomAction.zip, который поддерживает английские \(США\) языковые стандарты, полный путь может иметь следующий вид: ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip.  
  
3.  В **Обозреватель решений** выберите файл шаблона \(ZIP *YourTemplateName*\).  
  
4.  В окне **Свойства** задайте для свойства **Действие построения** значение **Содержание**.  
  
5.  Открыть контекстное меню для файла source.extension.vsixmanifest, а затем выберите **Открыть**.  
  
     Открытие файла в конструкторе.  
  
6.  В разделе **Активы** редактор выберите кнопку **Создать**.  
  
     Будет открыто диалоговое окно **Добавить новый актив**.  
  
7.  В списке **Тип** выберите **Microsoft.VisualStudio.ItemTemplate** или **Microsoft.VisualStudio.ProjectTemplate**.  
  
8.  В списке **Источник** выберите **Файл в файловой системе**.  
  
9. В поле **Путь** введите полный путь к сборке \(например, **ItemTemplates \\ SharePoint \\ SharePoint14 \\ 1033 \\ ContosoCustomAction.zip** или использует кнопку **Обзор**, чтобы найти и выбрать сборки, а затем нажмите кнопку **ОК**.  
  
##### Добавление мастера в шаблон проекта или элемента  
  
1.  В проекте VSIX, открыть контекстное меню для файла source.extension.vsixmanifest, а затем выберите **Открыть**.  
  
     Открытие файла в конструкторе.  
  
2.  В разделе **Активы** редактор выберите кнопку **Создать**.  
  
     Будет открыто диалоговое окно **Добавить новый актив**.  
  
3.  В списке **Тип** выберите **Microsoft.VisualStudio.Assembly**.  
  
4.  В списке **Источник**, выполните одно из следующих действий:  
  
    -   Если сборка мастера создана из проекта, являющегося тем же решением, что и проект VSIX выберите **Проект в текущем решении**.  В списке **Проект** выберите имя проекта.  
  
    -   Если сборка мастера включена, как файл в проекте выберите **Файл в файловой системе**.  В поле **Путь** введите полный путь к файлу сборки или воспользуйтесь кнопкой **Обзор**, чтобы найти и выбрать сборки.  
  
5.  Нажмите кнопку **ОК**.  
  
### Связанные обзоры  
 В следующей таблице приведены пошаговые руководства по использованию проекта VSIX для развертывания различных типов расширений средств SharePoint.  
  
|Тип расширения|Связанные пошаговые руководства|  
|--------------------|-------------------------------------|  
|Расширение, содержащее только сборку расширения|[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Расширение, содержащее команды SharePoint|[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Расширение, содержащее шаблон Visual Studio|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Расширение, содержащее мастер шаблона|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## Создание вручную пакетов VSIX  
 Чтобы создать вручную пакеты VSIX для расширений инструментов SharePoint, выполните следующие действия.  
  
1.  Создайте EXTENSION.VSIXMANIFEST\-файл, \[Типы\_контента\].xml и файл пакета VSIX \(VSIX\-файл\).  Дополнительные сведения см. в разделах [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md) и [Практическое руководство. Упаковка расширения &#40;развертывания VSIX&#41; вручную](~/misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
2.  Добавьте сборку расширения в пакет VSIX.  Если расширение содержит команду SharePoint, также добавьте сборку, которая реализует команду SharePoint в пакете VSIX.  
  
3.  Измените EXTENSION.VSIXMANIFEST\-файл.  
  
    -   Добавьте элемент `Microsoft.VisualStudio.MefComponent` под элементом `Assets`, а затем установите значение нового элемента на относительный путь сборки, реализующей расширение в пакете VSIX.  Дополнительные сведения см. в разделе [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/ru-ru/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Если расширение содержит команду SharePoint, которая вызывает объектную модель сервера SharePoint, добавьте элемент `Microsoft.VisualStudio.Assembly` под элементом `Assets`.  Задайте значение нового элемента на относительный путь сборки, которая реализует команду SharePoint в пакете VSIX.  Дополнительные сведения см. в разделе [элемент актива \(схема VSX\)](http://msdn.microsoft.com/ru-ru/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Если расширение содержит шаблон проекта или шаблон элемента, добавьте элемент `ProjectTemplate` или `ItemTemplate` под элементом `Assets`.  Задайте значение нового элемента на относительный путь к папке, содержащей шаблон в пакете VSIX.  Дополнительные сведения см. в разделах [NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/ru-ru/87add64c-9dcd-495f-8815-209dab182cb1) и [NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/ru-ru/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Если расширение содержит пользовательский мастер шаблона или шаблона элемента проекта, добавьте элемент `Assembly` под элементом `Assets`.  Задайте значение нового элемента на относительный путь сборки в пакете VSIX, а затем установите для атрибута `AssemblyName` до полного имени сборки \(включая версию, язык и региональные параметры и маркер открытого ключа\).  Дополнительные сведения см. в разделе [Элемент dependencies \(схема VSX\)](http://msdn.microsoft.com/ru-ru/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### Пример  
 В следующем примере представлено содержимое файла extension.vsixmanifest расширения средств SharePoint.  Расширение реализуется в сборке с именем Contoso.ProjectExtension.dll.  Расширение включает сборку команды SharePoint с именем Contoso.ExtensionCommands.dll и шаблоном элемента в папке с именем **ItemTemplates** в пакете VSIX.  Данный пример предполагает, что обе сборки находятся в одной папке с EXTENSION.VSIXMANIFEST\-файлом в пакете VSIX.  
  
```  
<PackageManifest Version=”2.0.0” xmlns=”http://schemas.microsoft.com/developer/vsx-schema/2011”>  
  <Metadata>  
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />  
    <DisplayName>CustomActionProjectItem</DisplayName>  
    <Description>Empty VSIX Project.</Description>  
  </Metadata>  
  <Installation>  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />  
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />  
  </Assets>  
</PackageManifest>  
  
```  
  
## См. также  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  