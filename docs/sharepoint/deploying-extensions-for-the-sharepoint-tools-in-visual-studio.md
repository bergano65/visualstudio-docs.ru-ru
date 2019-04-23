---
title: Развертывание расширений для инструментов SharePoint в Visual Studio | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53e36d993e72da759c87e7d2d2f908818b3d9024
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068552"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Развертывание расширений для инструментов SharePoint в Visual Studio

Чтобы развернуть расширение инструментов SharePoint, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX), который содержит сборку расширения и другие файлы, которые требуется распространить с расширением. Пакет VSIX является сжатый файл, который соответствует стандарту Open Packaging Conventions (OPC). Пакетов VSIX *.vsix* расширения.

После создания пакета VSIX, другие пользователи могут запускать VSIX-файл, чтобы установить расширение. Когда пользователь устанавливает расширение, все файлы устанавливаются в папку %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Чтобы развернуть расширение, можно отправить пакет VSIX для [Visual Studio Marketplace](https://marketplace.visualstudio.com/) веб-сайт, или можно распространить пакет с заказчиками каким-либо образом, как размещение пакета в общую сетевую папку или других веб- веб-узел.

Дополнительные сведения о создании пакетов VSIX и их развертывания в [Visual Studio Marketplace](https://marketplace.visualstudio.com/), см. в разделе [доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Пакет VSIX можно создать с помощью **проект VSIX** шаблона в Visual Studio, или можно создать пакет VSIX вручную.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Использовать проекты VSIX для создания пакетов VSIX

Можно использовать **проект VSIX** шаблоном, который предоставляется пакетом SDK для Visual Studio для создания пакетов VSIX для расширений инструментов SharePoint. С помощью проекта VSIX предоставляет несколько преимуществ над созданием пакета VSIX вручную.

- Visual Studio автоматически создает пакет VSIX, при построении проекта. Задачи, например добавление файлов развертывания в пакет и создать файл [Content_Types] .xml для пакета, уже выполнены.

- Можно настроить для включения в пакет VSIX выходные данные построения проекта расширения и другие файлы, такие как шаблоны проектов и шаблоны элементов проекта VSIX.

Дополнительные сведения об использовании проекта VSIX см. в разделе [шаблоном проекта VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Упорядочить проекты

По умолчанию проекты VSIX создают только пакеты VSIX, но не сборок. Таким образом вы обычно не реализуют расширения инструментов SharePoint в проект VSIX. Обычно вы работаете по крайней мере два проекта:

- Проект VSIX.

- Проект библиотеки классов, реализующий расширение.

Также можно использовать дополнительные проекты для некоторых типов расширений:

- Проект библиотеки классов, реализующий команды SharePoint, которые используются в расширении. Пошаговое руководство, демонстрирующий этот сценарий, см. в разделе [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Проекте шаблона проекта или шаблона элемента, который создает шаблон элемента или проекта, если расширение определяет новый тип элемента проекта SharePoint. Пошаговое руководство, демонстрирующий этот сценарий, см. в разделе [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Проект библиотеки классов, реализующий шаблон элемента или проекта, если расширение содержит шаблон. Пошаговое руководство, демонстрирующий этот сценарий, см. в разделе [Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Если включить все проекты в одном решении Visual Studio, можно изменить файл source.extension.vsixmanifest проекта VSIX для включения вывода построения проектов библиотеки классов.

### <a name="edit-the-vsix-manifest"></a>Изменить манифест VSIX

Необходимо изменить файл source.extension.vsixmanifest в проект VSIX, чтобы включить записи для всех элементов, которые вы хотите включить в расширение. При открытии файл source.extension.vsixmanifest в контекстном меню, файл появится в конструктор, который предоставляет пользовательский Интерфейс для редактирования XML-файла. Дополнительные сведения см. в разделе [конструктор манифеста VSIX](../extensibility/vsix-manifest-designer.md).

Необходимо добавить записи в файл source.extension.vsixmanifest для следующих элементов:

- Сборка модуля.

- Сборка, реализующая команды SharePoint, которые используются в расширении.

- Шаблоны проектов и шаблоны элементов, связанных с расширением.

- Настраиваемый мастер для шаблона, который связан с расширением.

Следующие процедуры описывают способы добавления записей файла VSIXMANIFEST для каждого из этих элементов.

#### <a name="to-include-the-extension-assembly"></a>Включение расширения сборки

1. В проект VSIX, откройте контекстное меню для файла source.extension.vsixmanifest и выберите **откройте**.

     Файл откроется в конструкторе

2. На **активы** вкладка редактора выберите **New** кнопки.

     **Добавить новый актив** откроется диалоговое окно.

3. В **тип** выберите **Microsoft.VisualStudio.MefComponent**.

4. В **источника** списке, выполните одно из следующих действий:

    - Если сборка расширения создана из проекта, который находится в том же решении, что и проект VSIX, выберите **проект в текущем решении**. В **проекта** выберите имя проекта.

    - Если сборка расширения включен в виде файла в проекте, нажмите кнопку **файл в файловой системе**. В **путь** списке, введите полный путь к файлу сборки расширения или использовать **Обзор** кнопку, чтобы найти и выбрать файл сборки.

5. Нажмите кнопку **ОК** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Чтобы включить сборку команды SharePoint

1. В проект VSIX, откройте контекстное меню для файла source.extension.vsixmanifest и выберите **откройте** кнопки.

     Файл откроется в конструкторе.

2. В **активы** раздел в редакторе выберите **New** кнопки.

     **Добавить новый актив** откроется диалоговое окно.

3. В **тип** введите **SharePoint.Commands.v4**.

4. В **источника** списке, выполните одно из следующих действий:

    - Если сборка команды создается из проекта, который находится в том же решении, что и проект VSIX, выберите **проект в текущем решении**. В **проекта** выберите имя проекта.

    - Если сборка команды включен в виде файла в проекте, нажмите кнопку **файл в файловой системе**. В **путь** списке, введите полный путь к файлу сборки расширения или использовать **Обзор** кнопку, чтобы найти и выбрать файл сборки.

5. Нажмите кнопку **ОК** .

#### <a name="to-include-a-template-that-you-create"></a>Добавление шаблона, созданный

1. В проект VSIX, откройте контекстное меню для файла source.extension.vsixmanifest и выберите **откройте** кнопки.

     Файл откроется в конструкторе.

2. В **активы** раздел в редакторе выберите **New** кнопки.

     **Добавить новый актив** откроется диалоговое окно.

3. В **тип** выберите **Microsoft.VisualStudio.ProjectTemplate** или **Microsoft.VisualStudio.ItemTemplate**.

4. В **источника** выберите **проект в текущем решении**.

5. В **проекта** , выберите имя проекта, а затем выберите **ОК** кнопки.

6. В **обозревателе решений**, откройте контекстное меню для шаблона проекта или элемента проекта и затем выберите **выгрузить проект**.

7. Снова откройте контекстное меню для узла проекта и выберите **изменить**_Имя_проекта_шаблона_**.csproj** или **изменить**  _Имя_проекта_шаблона_**.vbproj**.

8. Найдите следующие `VSTemplate` элемент в файле проекта.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Замените следующий код XML этого элемента.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` Элемент задает дополнительные папки в пути, в рамках которой создается шаблон проекта при сборке проекта. Папки, указанные здесь убедитесь, что шаблон элемента будет доступен только в том случае, когда клиенты открыть **Добавление нового проекта** диалогового окна разверните узел **SharePoint** узел и нажмите кнопку **2010**  узла.

10. Сохраните и закройте файл.

11. В **обозревателе решений**, откройте контекстное меню для шаблона проекта или элемента проекта и затем выберите **перезагрузить проект**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Добавление шаблона, создаваемые вручную

1. В проекте VSIX добавьте новую папку для проекта для шаблона.

2. В этой новой папке создайте следующие вложенные папки и затем добавьте файл шаблона (ZIP-файл), который *Локали* папки.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *КОД языка*

     *YourTemplateName*ZIP-файл

     Например, если у вас есть шаблон элемента с именем ContosoCustomAction.zip, который поддерживает этот языковой стандарт английский (США), полный путь может быть *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. В **обозревателе решений**, выберите файл шаблона (*YourTemplateName*ZIP-файл).

4. В **свойства** окне **действие при построении** свойства **содержимого**.

5. Откройте контекстное меню для файла source.extension.vsixmanifest, а затем выберите **откройте**.

     Файл откроется в конструкторе.

6. В **активы** раздел в редакторе выберите **New** кнопки.

     **Добавить новый актив** откроется диалоговое окно.

7. В **тип** выберите **Microsoft.VisualStudio.ItemTemplate** или **Microsoft.VisualStudio.ProjectTemplate**.

8. В **источника** выберите **файл в файловой системе**.

9. В **путь** введите полный путь к сборке (например, *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, или использовать **Обзор**кнопку для поиска и выберите сборку, а затем выберите **ОК** кнопки.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Чтобы включить мастер для шаблона проекта или шаблона элемента

1. В проект VSIX, откройте контекстное меню для файла source.extension.vsixmanifest и выберите **откройте**.

     Файл откроется в конструкторе.

2. В **активы** раздел в редакторе выберите **New** кнопки.

     **Добавить новый актив** откроется диалоговое окно.

3. В **тип** выберите **Microsoft.VisualStudio.Assembly**.

4. В **источника** списке, выполните одно из следующих действий:

    - Если сборка мастера создается из проекта, который находится в том же решении, что и проект VSIX, выберите **проект в текущем решении**. В **проекта** выберите имя проекта.

    - Если включен в виде файла в проекте сборки мастера, нажмите кнопку **файл в файловой системе**. В **путь** введите полный путь к файлу сборки или использовать **Обзор** кнопку, чтобы найти и выбрать сборку.

5. Нажмите кнопку **ОК** .

### <a name="related-walkthroughs"></a>Пошаговые руководства

В следующей таблице перечислены примеры, демонстрирующие способы использования проекта VSIX для развертывания различных типов расширений средств SharePoint.

|Тип расширения|Пошаговые руководства|
|--------------------|--------------------------|
|Расширение, содержащее только сборку расширения|[Пошаговое руководство: Расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Пошаговое руководство: Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Пошаговое руководство: Вызов клиентской объектной модели SharePoint в расширении обозревателя серверов](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Расширение, которое включает в себя команды SharePoint|[Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Пошаговое руководство: Расширения обозревателя сервера для отображения веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Расширение, которое предоставляет шаблон Visual Studio|[Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Расширение, которое включает в себя мастер шаблона|[Пошаговое руководство: Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Пошаговое руководство: Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Создание пакетов VSIX вручную

Если вы хотите создать пакет VSIX для расширения средств SharePoint вручную, выполните следующие действия:

1. Создайте файл extension.vsixmanifest и файл [Content_Types] .xml в новую папку. Дополнительные сведения см. в разделе [составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2. В обозревателе Windows щелкните правой кнопкой мыши папку, содержащую два XML-файлы, нажмите кнопку Отправить и затем ZIP-папку. Переименуйте полученный ZIP-файл в Filename.vsix, где Filename — имя распространяемого файла, устанавливающего пакет.

3. Добавьте сборку расширения в пакет VSIX. Если расширение содержит команды SharePoint, необходимо также добавьте сборки, реализующей команду SharePoint в пакет VSIX.

4. Измените файл extension.vsixmanifest.

    - Добавить `Microsoft.VisualStudio.MefComponent` элемента под `Assets` элемент, а затем задайте значение нового элемента в относительный путь к сборке, реализующей расширение в пакет VSIX. Дополнительные сведения см. в разделе [MEFComponent элемент (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Если расширение содержит команду SharePoint, которая вызывает серверную объектную модель для SharePoint, добавьте `Microsoft.VisualStudio.Assembly` элемента под `Assets` элемент. Значение нового элемента в относительный путь к сборке, реализующей команду SharePoint в пакете VSIX. Дополнительные сведения см. в разделе [активов элемент (Схема VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

    - Если расширение содержит шаблон проекта или шаблона элемента, добавьте `ProjectTemplate` или `ItemTemplate` элемента под `Assets` элемент. Значение нового элемента в относительный путь к папке, содержащей шаблона в пакете VSIX. Дополнительные сведения см. в разделе [ProjectTemplate элемент (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) и [ItemTemplate элемента (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Если расширение содержит настраиваемый мастер для шаблона проекта или шаблона элемента, добавьте `Assembly` элемента под `Assets` элемент. Задайте значение нового элемента к относительному пути сборки в пакете VSIX, а затем установите `AssemblyName` атрибут полное имя сборки (включая версии, язык и региональные параметры и маркер открытого ключа). Дополнительные сведения см. в разделе [Dependency-элемент (Схема VSX)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37).

### <a name="example"></a>Пример

Следующий пример показывает содержание файл extension.vsixmanifest для расширения инструментов SharePoint. Расширение реализуется в сборке, которая называется Contoso.ProjectExtension.dll. Расширение включает сборку команду SharePoint с именем Contoso.ExtensionCommands.dll и шаблона элемента в папке с именем **ItemTemplates** в пакете VSIX. В этом примере предполагается, что обе сборки в той же папке, что и файл extension.vsixmanifest в пакете VSIX.

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

- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Отладка расширений для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
