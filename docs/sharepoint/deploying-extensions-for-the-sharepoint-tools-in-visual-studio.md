---
title: Развертывание расширений для средств SharePoint в Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dba88bde834ddf8e5eba938325b21434560827a1
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767264"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Развертывание расширений для средств SharePoint в Visual Studio
  Чтобы развернуть расширение инструментов SharePoint, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX), который содержит сборку расширения и другие файлы, которые требуется распространить с расширением. Пакет VSIX представляет сжатый файл, который соответствует стандарту Open Packaging Conventions (OPC). Пакетов VSIX *.vsix* расширения.  
  
 После создания пакета VSIX, другие пользователи могут запускать VSIX-файл, чтобы установить расширение. Когда пользователь устанавливает расширения, все файлы устанавливаются в папку %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Чтобы развернуть расширение, можно отправить пакет VSIX для [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) веб-сайт, или можно распространить пакет для ваших клиентов с помощью других средств, таких как размещение пакета в общей сетевой папке или другом веб-сайте.  
  
 Дополнительные сведения о создании пакетов VSIX и развертывании их [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), в разделе [доставки расширений Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
 Пакет VSIX можно создать с помощью **проект VSIX** шаблон в Visual Studio, или можно создать пакет VSIX вручную.  
  
## <a name="use-vsix-projects-to-create-vsix-packages"></a>Используйте проекты VSIX для создания пакетов VSIX
 Можно использовать **проект VSIX** шаблонов, предоставляемых Visual Studio SDK, чтобы создать пакеты VSIX для расширений инструментов SharePoint. Использование проекта VSIX предоставляет несколько преимуществ над созданием пакета VSIX вручную.  
  
-   При построении проекта, Visual Studio автоматически создает пакет VSIX. Задачи, такие как добавление файлов развертывания в пакет и создать файл [Content_Types] .xml для пакета, уже выполнены.  
  
-   Можно настроить для включения в пакет VSIX выходные данные построения проекта расширения и другие файлы, такие как шаблоны проектов и шаблоны элементов проекта VSIX.  
  
 Дополнительные сведения об использовании проекта VSIX см. в разделе [шаблон проекта VSIX](/visualstudio/extensibility/vsix-project-template).  
  
### <a name="organize-your-projects"></a>Организовать проекты
 По умолчанию проекты VSIX создают только пакеты VSIX, но не сборки. Таким образом обычно не реализовать расширения инструментов SharePoint в проект VSIX. Обычно работает с по крайней мере двух проектов:  
  
-   Проект VSIX.  
  
-   Проект библиотеки классов, реализующий расширение.  
  
 Также можно использовать дополнительные проекты для некоторых типов расширений:  
  
-   Проект библиотеки классов, реализующий команды SharePoint, используемые в расширении. Пример, демонстрирующий этот сценарий, в разделе [Пошаговое руководство: расширение обозревателя серверов для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Проект шаблона проекта или шаблона элемента, который создает шаблон элемента или проекта, если в расширении определен новый тип элемента проекта SharePoint. Пример, демонстрирующий этот сценарий, в разделе [Пошаговое руководство: создание элемент проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Проект библиотеки классов, реализующий шаблон элемента или проекта, если расширение содержит шаблон. Пример, демонстрирующий этот сценарий, в разделе [Пошаговое руководство: создание элемент проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 При включении всех проектов в одном решении Visual Studio, можно изменить файл source.extension.vsixmanifest в проект VSIX, включаемых в выходные данные построения в проектах библиотек классов.  
  
### <a name="edit-the-vsix-manifest"></a>Изменить манифест VSIX
 Необходимо изменить файл source.extension.vsixmanifest в проект VSIX, чтобы включить записи для всех элементов, которые требуется включить в расширение. При открытии файл source.extension.vsixmanifest в контекстном меню файл появится в конструктор, который предоставляет пользовательский Интерфейс для редактирования XML-файла. Дополнительные сведения см. в разделе [конструктор манифеста VSIX](/visualstudio/extensibility/vsix-manifest-designer).  
  
 Необходимо добавить записи в файл source.extension.vsixmanifest для следующих элементов:  
  
-   Сборка расширения.  
  
-   Сборка, реализующая команды SharePoint, используемые в расширении.  
  
-   Шаблоны проектов и шаблоны элементов, которые связаны с расширением.  
  
-   Специальный мастер для шаблона, который связан с расширением.  
  
 Следующие процедуры описывают Добавление записи для файла VSIXMANIFEST для каждого из этих элементов.  
  
##### <a name="to-include-the-extension-assembly"></a>Чтобы включить сборку расширения  
  
1.  В проект VSIX, откройте файл source.extension.vsixmanifest контекстное меню и выберите **откройте**.  
  
     Файл откроется в конструкторе  
  
2.  На **активы** вкладка редактора выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
3.  В **тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
4.  В **источника** выполните одно из следующих действий:  
  
    -   Если сборка расширения создана из проекта, который находится в том же решении, что и проект VSIX, выберите **проект в текущем решении**. В **проекта** выберите имя проекта.  
  
    -   Если сборка расширения включена в проект как файл, выберите **файл в файловой системе**. В **путь** списка, введите полный путь к файлу сборки расширения или использовать **Обзор** кнопку, чтобы найти и выбрать файл сборки.  
  
5.  Нажмите кнопку **ОК** .  
  
##### <a name="to-include-a-sharepoint-command-assembly"></a>Чтобы включить сборку команды SharePoint  
  
1.  В проект VSIX, откройте файл source.extension.vsixmanifest контекстное меню и выберите **откройте** кнопки.  
  
     Файл откроется в конструкторе.  
  
2.  В **активы** раздел в редакторе, выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
3.  В **тип** введите **SharePoint.Commands.v4**.  
  
4.  В **источника** выполните одно из следующих действий:  
  
    -   Если сборка команды создана из проекта, который находится в том же решении, что и проект VSIX, выберите **проект в текущем решении**. В **проекта** выберите имя проекта.  
  
    -   Если сборка команды включена как файл в проекте, выберите **файл в файловой системе**. В **путь** списка, введите полный путь к файлу сборки расширения или использовать **Обзор** кнопку, чтобы найти и выбрать файл сборки.  
  
5.  Нажмите кнопку **ОК** .  
  
##### <a name="to-include-a-template-that-you-create"></a>Добавление шаблона, создаваемого  
  
1.  В проект VSIX, откройте файл source.extension.vsixmanifest контекстное меню и выберите **откройте** кнопки.  
  
     Файл откроется в конструкторе.  
  
2.  В **активы** раздел в редакторе, выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
3.  В **тип** выберите **Microsoft.VisualStudio.ProjectTemplate** или **Microsoft.VisualStudio.ItemTemplate**.  
  
4.  В **источника** выберите **проект в текущем решении**.  
  
5.  В **проекта** , выберите имя проекта, а затем выберите **ОК** кнопки.  
  
6.  В **обозревателе решений**, откройте контекстное меню для шаблона проекта или элемента проекта и нажмите кнопку **выгрузить проект**.  
  
7.  Снова откройте контекстное меню узла проекта и выберите **изменить***Имя_проекта_шаблона***.csproj** или **изменить***Имя_проекта_шаблона***. VBPROJ**.  
  
8.  Выберите следующее `VSTemplate` элемента в файле проекта.  
  
    ```xml  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Замените следующий XML-код этого элемента.  
  
    ```xml  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     `OutputSubPath` Элемент указывает дополнительные папки в пути, в котором создан шаблон проекта при построении проекта. Заданные здесь папки убедитесь, что шаблон элемента будут доступны только в том случае, если открыть клиентов **Добавление нового проекта** диалогового окна разверните **SharePoint** узел и выберите **2010**  узла.  
  
10. Сохраните и закройте файл.  
  
11. В **обозревателе решений**, откройте контекстное меню для шаблона проекта или элемента проекта и нажмите кнопку **перезагрузить проект**.  
  
##### <a name="to-include-a-template-that-you-create-manually"></a>Добавление шаблона, создаваемого вручную  
  
1.  В проекте VSIX добавьте новую папку для проекта для шаблона.  
  
2.  В новой папке, создайте следующие вложенные папки, а затем добавьте файл шаблона (ZIP-файл), который *Локали* папки.  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *КОД языка*  
  
     *YourTemplateName*.zip  
  
     Например, если шаблон элемента с именем ContosoCustomAction.zip, который поддерживает этот языковой стандарт английский (США), полный путь может быть *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.  
  
3.  В **обозревателе решений**, выберите файл шаблона (*YourTemplateName*.zip).  
  
4.  В **свойства** задайте **действие при построении** свойства **содержимого**.  
  
5.  Откройте файл source.extension.vsixmanifest контекстное меню и выберите **откройте**.  
  
     Файл откроется в конструкторе.  
  
6.  В **активы** раздел в редакторе, выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
7.  В **тип** выберите **Microsoft.VisualStudio.ItemTemplate** или **Microsoft.VisualStudio.ProjectTemplate**.  
  
8.  В **источника** выберите **файл в файловой системе**.  
  
9. В **путь** введите полный путь к сборке (например, *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, или используйте **Обзор**кнопку, чтобы найти и выбрать сборку, а затем выберите **ОК** кнопки.  
  
##### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Чтобы включить мастер для шаблона проекта или шаблона элемента  
  
1.  В проект VSIX, откройте файл source.extension.vsixmanifest контекстное меню и выберите **откройте**.  
  
     Файл откроется в конструкторе.  
  
2.  В **активы** раздел в редакторе, выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
3.  В **тип** выберите **Microsoft.VisualStudio.Assembly**.  
  
4.  В **источника** выполните одно из следующих действий:  
  
    -   Если сборка мастера создана из проекта, который находится в том же решении, что и проект VSIX, выберите **проект в текущем решении**. В **проекта** выберите имя проекта.  
  
    -   Если сборка мастера включена как файл в проект, выберите **файл в файловой системе**. В **путь** поле, введите полный путь к файлу сборки или использовать **Обзор** кнопку, чтобы найти и выбрать сборку.  
  
5.  Нажмите кнопку **ОК** .  
  
### <a name="related-walkthroughs"></a>Связанные пошаговые руководства
 В следующей таблице перечислены примеры, демонстрирующие использование проекта VSIX для развертывания различных типов расширений инструментов SharePoint.  
  
|Тип расширения|Связанные пошаговые руководства|  
|--------------------|--------------------------|  
|Расширение, содержащее только сборку расширения|[Пошаговое руководство. Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Пошаговое руководство. Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Пошаговое руководство. Вызов клиентской объектной модели SharePoint в расширении обозревателя серверов](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Расширение, которое включает в себя команды SharePoint|[Пошаговое руководство. Создание пользовательского этапа развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Пошаговое руководство. Расширение обозревателя сервера, так чтобы в нем отображались веб-части](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Расширение, содержащее шаблон Visual Studio|[Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Расширение, содержащее мастер шаблонов|[Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## <a name="create-vsix-packages-manually"></a>Создать пакеты VSIX вручную
 Если вы хотите создать пакет VSIX для расширения средств SharePoint вручную, выполните следующие действия:  
  
1.  Создайте файл extension.vsixmanifest и файл [Content_Types] .xml в новую папку. Дополнительные сведения см. в разделе [составляющие пакета VSIX](/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
2.  В проводнике Windows щелкните правой кнопкой мыши папку, содержащую два XML-файла и нажмите кнопку Отправить щелкните Сжатая ZIP-папка. Переименуйте полученный ZIP-файл в Filename.vsix, где имя файла — это имя распространяемого файла, устанавливающего пакет.  
  
3.  Добавьте сборку расширения в пакет VSIX. Если расширение содержит команду SharePoint, необходимо также добавьте сборки, реализующей пакет VSIX.  
  
4.  Измените файл extension.vsixmanifest.  
  
    -   Добавить `Microsoft.VisualStudio.MefComponent` элемента под `Assets` элемент, а затем задайте значение нового элемента относительный путь сборки, реализующей расширение в пакет VSIX. Дополнительные сведения см. в разделе [MEFComponent элемент (Схема VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Если расширение содержит команду SharePoint, которая вызывает объектную модель сервера для SharePoint, добавьте `Microsoft.VisualStudio.Assembly` элемента под `Assets` элемента. Значение нового элемента относительный путь сборки, реализующей в пакет VSIX. Дополнительные сведения см. в разделе [активов элемент (Схема VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Если расширение содержит шаблон проекта или элемента, добавьте `ProjectTemplate` или `ItemTemplate` элемента под `Assets` элемента. Значение нового элемента в относительный путь к папке, содержащей шаблон в пакет VSIX. Дополнительные сведения см. в разделе [элемент ProjectTemplate (Схема VSX)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1) и [элемента ItemTemplate (Схема VSX)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Если расширение содержит настраиваемый мастер для шаблона проекта или шаблона элемента, добавьте `Assembly` элемента под `Assets` элемента. Задайте значение нового элемента относительный путь к сборке в пакете VSIX, а затем установите `AssemblyName` атрибут полного имени сборки (включая версии, языка и региональных параметров и токена открытого ключа). Дополнительные сведения см. в разделе [элемент зависимость (Схема VSX)](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### <a name="example"></a>Пример  
 Следующий пример показывает содержимое файл extension.vsixmanifest для расширения инструментов SharePoint. Расширение реализуется в сборке, которая называется Contoso.ProjectExtension.dll. Модуль содержит сборку команды SharePoint, которая называется Contoso.ExtensionCommands.dll и шаблон элемента в папке, которая называется **элементов** в пакете VSIX. В этом примере предполагается, что обе сборки в той же папке, что и файл extension.vsixmanifest в пакет VSIX.  
  
```xml 
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">  
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
  
## <a name="see-also"></a>См. также
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Обращение к объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Отладка расширений для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
