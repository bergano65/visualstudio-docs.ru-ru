---
title: Развертывание расширений для инструментов SharePoint в Visual Studio | Документация Майкрософт
description: Развертывание расширений для инструментов SharePoint в Visual Studio. Используйте проекты расширения Visual Studio (VSIX) для создания пакетов VSIX.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6a899bcc132b9229c1046dee5793278f79ea9e5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948899"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Развертывание расширений для инструментов SharePoint в Visual Studio

Чтобы развернуть расширение инструментов SharePoint, создайте [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] пакет расширения (VSIX), содержащий сборку расширения и другие файлы, которые требуется распространить с расширением. Пакет VSIX представляет собой сжатый файл, следующий за стандартом Open Packaging Conventions (OPC). У пакетов VSIX есть расширение *VSIX* .

После создания пакета VSIX другие пользователи могут запустить VSIX-файл для установки расширения. Когда пользователь устанавливает расширение, все файлы устанавливаются в папку%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions Чтобы развернуть расширение, можно передать пакет VSIX на веб-сайт [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или передать его клиентам с помощью других средств, таких как размещение пакета в общей сетевой папке или на другом веб-сайте.

Дополнительные сведения о создании пакетов VSIX и их развертывании в [Visual Studio Marketplace](https://marketplace.visualstudio.com/)см. в разделе [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Вы можете создать пакет VSIX с помощью шаблона **проекта VSIX** в Visual Studio или создать пакет VSIX вручную.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Использование проектов VSIX для создания пакетов VSIX

Вы можете использовать шаблон **проекта VSIX** , ПРЕДОСТАВЛЯЕМый пакетом SDK для Visual Studio, для создания пакетов VSIX для расширений инструментов SharePoint. Использование проекта VSIX предоставляет несколько преимуществ по сравнению с созданием пакета VSIX вручную.

- Visual Studio автоматически создает пакет VSIX при построении проекта. Задачи, такие как добавление файлов развертывания в пакет и создание файла [Content_Types]. XML для пакета, выполняются за вас.

- Вы можете настроить проект VSIX для включения выходных данных сборки проекта расширения и других файлов, таких как шаблоны проектов и шаблонов элементов, в пакет VSIX.

Дополнительные сведения об использовании проекта VSIX см. в разделе [шаблон проекта VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Организация проектов

По умолчанию проекты VSIX создают только пакеты VSIX, а не сборки. Поэтому расширение инструментов SharePoint в проекте VSIX обычно не реализуется. Обычно вы работаете по крайней мере с двумя проектами:

- Проект VSIX.

- Проект библиотеки классов, реализующий расширение.

Вы также можете работать с дополнительными проектами для определенных типов расширений:

- Проект библиотеки классов, реализующий все команды SharePoint, используемые вашим расширением. Пошаговое руководство, демонстрирующее этот сценарий, см. [в разделе Пошаговое руководство. расширение обозреватель сервера для показа веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Шаблон элемента или проект шаблона проекта, который создает шаблон элемента или шаблона проекта, если расширение определяет новый тип элемента проекта SharePoint. Пошаговое руководство, демонстрирующее этот сценарий, см. в разделе [Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Проект библиотеки классов, реализующий настраиваемый мастер для шаблона элемента или шаблона проекта, если расширение содержит шаблон. Пошаговое руководство, демонстрирующее этот сценарий, см. в разделе [Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

При включении всех проектов в одном решении Visual Studio можно изменить файл Source. extension. vsixmanifest в проекте VSIX, чтобы включить выходные данные сборки проектов библиотеки классов.

### <a name="edit-the-vsix-manifest"></a>Изменение манифеста VSIX

Необходимо изменить файл Source. extension. vsixmanifest в проекте VSIX, чтобы включить записи для всех элементов, которые требуется включить в расширение. При открытии файла Source. extension. vsixmanifest из контекстного меню файл появляется в конструкторе, который предоставляет пользовательский интерфейс для редактирования XML-кода в файле. Дополнительные сведения см. в разделе [Конструктор манифестов VSIX](../extensibility/vsix-manifest-designer.md).

Необходимо добавить записи в файл Source. extension. vsixmanifest для следующих элементов:

- Сборка расширения.

- Сборка, реализующая все команды SharePoint, используемые вашим расширением.

- Шаблоны проектов или элементов, связанные с вашим расширением.

- Настраиваемый мастер для шаблона, связанного с расширением.

В следующих процедурах описывается добавление записей в VSIXMANIFEST файл для каждого из этих элементов.

#### <a name="to-include-the-extension-assembly"></a>Включение сборки расширения

1. В проекте VSIX откройте контекстное меню для файла Source. extension. vsixmanifest и выберите **Открыть**.

     Файл откроется в конструкторе

2. На вкладке **ресурсы** редактора нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление нового ресурса** .

3. В списке **тип** выберите **Microsoft. VisualStudio. MefComponent**.

4. В списке **источник** выполните одно из следующих действий.

    - Если сборка расширения строится на основе проекта, который находится в том же решении, что и проект VSIX, выберите **проект в текущем решении**. В списке **проект** выберите имя проекта.

    - Если сборка расширения включается в проект в виде файла, выберите **файл в файловой системе**. В списке **путь** введите полный путь к файлу сборки расширения или нажмите кнопку **Обзор** , чтобы найти и выбрать файл сборки.

5. Нажмите кнопку **ОК** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Включение сборки команд SharePoint

1. В проекте VSIX откройте контекстное меню для файла Source. extension. vsixmanifest, а затем нажмите кнопку **Открыть** .

     Файл откроется в конструкторе.

2. В разделе **ресурсы** редактора нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление нового ресурса** .

3. В поле **тип** введите **SharePoint. Commands. v4**.

4. В списке **источник** выполните одно из следующих действий.

    - Если сборка команды строится из проекта, который находится в том же решении, что и проект VSIX, выберите **проект в текущем решении**. В списке **проект** выберите имя проекта.

    - Если командная сборка включена в проект в виде файла, выберите **файл в файловой системе**. В списке **путь** введите полный путь к файлу сборки расширения или нажмите кнопку **Обзор** , чтобы найти и выбрать файл сборки.

5. Нажмите кнопку **ОК** .

#### <a name="to-include-a-template-that-you-create"></a>Включение создаваемого шаблона

1. В проекте VSIX откройте контекстное меню для файла Source. extension. vsixmanifest, а затем нажмите кнопку **Открыть** .

     Файл откроется в конструкторе.

2. В разделе **ресурсы** редактора нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление нового ресурса** .

3. В списке **тип** выберите **Microsoft. VisualStudio. ProjectTemplate** или **Microsoft. VisualStudio. ItemTemplate**.

4. В списке **источник** выберите **проект в текущем решении**.

5. В списке **проект** выберите имя проекта, а затем нажмите кнопку **ОК** .

6. В **Обозреватель решений** откройте контекстное меню для шаблона проекта или проекта шаблона элемента, а затем выберите команду **Выгрузить проект**.

7. Снова откройте контекстное меню узла проекта и выберите **изменить**_йоуртемплатепрожектнаме_**. csproj** или **изменить**_йоуртемплатепрожектнаме_**. vbproj**.

8. `VSTemplate`В файле проекта нахождение следующего элемента.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Замените этот элемент следующим XML-кодом.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`Элемент задает дополнительные папки в пути, по которому создается шаблон проекта при построении проекта. Указанные здесь папки гарантируют, что шаблон элемента будет доступен только тогда, когда клиенты открывают диалоговое окно **Добавление нового проекта** , разверните узел **SharePoint** , а затем выберите узел **2010** .

10. Сохраните и закройте файл.

11. В **Обозреватель решений** откройте контекстное меню шаблона проекта или шаблона элемента и выберите **Перезагрузить проект**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Включение шаблона, созданного вручную

1. В проекте VSIX добавьте в проект новую папку, в которой будет содержаться шаблон.

2. В этой новой папке создайте следующие вложенные папки, а затем добавьте шаблон ZIP-файл в папку *Locale ID* .

     *йоуртемплатефолдер*

     **SharePoint**

     **SharePoint14**

     *Код языка*

     *Йоуртемплатенаме*. zip

     Например, если имеется шаблон элемента с именем ContosoCustomAction.zip, поддерживающий английский язык (США), полный путь может быть *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. В **Обозреватель решений** выберите файл шаблона (*йоуртемплатенаме*. zip).

4. В окне **Свойства** задайте для свойства **действие сборки** значение **содержимое**.

5. Откройте контекстное меню для файла Source. extension. vsixmanifest и выберите **Открыть**.

     Файл откроется в конструкторе.

6. В разделе **ресурсы** редактора нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление нового ресурса** .

7. В списке **тип** выберите **Microsoft. VisualStudio. ItemTemplate** или **Microsoft. VisualStudio. ProjectTemplate**.

8. В списке **источник** выберите **файл в файловой системе**.

9. В поле **путь** введите полный путь к сборке (например, *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip* или нажмите кнопку **Обзор** , чтобы найти и выбрать сборку, а затем нажмите кнопку **ОК** .

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Включение мастера для шаблона проекта или элемента

1. В проекте VSIX откройте контекстное меню для файла Source. extension. vsixmanifest и выберите **Открыть**.

     Файл откроется в конструкторе.

2. В разделе **ресурсы** редактора нажмите кнопку **создать** .

     Откроется диалоговое окно **Добавление нового ресурса** .

3. В списке **тип** выберите **Microsoft. VisualStudio. Assembly**.

4. В списке **источник** выполните одно из следующих действий.

    - Если сборка мастера построена из проекта, который находится в том же решении, что и проект VSIX, выберите **проект в текущем решении**. В списке **проект** выберите имя проекта.

    - Если сборка мастера включена в проект в виде файла, выберите **файл в файловой системе**. В поле **путь** введите полный путь к файлу сборки или воспользуйтесь кнопкой **Обзор** , чтобы найти и выбрать сборку.

5. Нажмите кнопку **ОК** .

### <a name="related-walkthroughs"></a>Связанные пошаговые руководства

В следующей таблице перечислены пошаговые руководства, демонстрирующие использование проекта VSIX для развертывания различных типов расширений инструментов SharePoint.

|тип расширения;|Связанные пошаговые руководства|
|--------------------|--------------------------|
|Расширение, включающее только сборку расширения|[Пошаговое руководство. расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Пошаговое руководство. Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Пошаговое руководство. вызов клиентской объектной модели SharePoint в расширении обозреватель сервера](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Расширение, включающее команды SharePoint|[Пошаговое руководство. Создание настраиваемого шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Пошаговое руководство. расширение обозреватель сервера для показа веб-частей](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Расширение, включающее шаблон Visual Studio|[Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Расширение, включающее мастер шаблонов|[Пошаговое руководство. Создание элемента проекта настраиваемого действия с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона проекта, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Создание пакетов VSIX вручную

Если вы хотите вручную создать пакет VSIX для расширения инструментов SharePoint, выполните следующие действия.

1. Создайте файл Extension. vsixmanifest и файл [Content_Types]. XML в новой папке. Дополнительные сведения см. в разделе [Анатомия пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2. В проводнике Windows щелкните правой кнопкой мыши папку, содержащую два XML-файла, выберите пункт Отправить, а затем пункт Сжатая ZIP-папка. Переименуйте полученный ZIP-файл в Имя_файла.vsix, где Имя_файла — это имя распространяемого файла, устанавливающего пакет.

3. Добавьте сборку расширения в пакет VSIX. Если расширение содержит команду SharePoint, также добавьте сборку, реализующую команду SharePoint, в пакет VSIX.

4. Измените файл Extension. vsixmanifest:

    - Добавьте `Microsoft.VisualStudio.MefComponent` элемент в `Assets` элемент, а затем задайте в качестве значения нового элемента относительный путь к сборке, реализующей расширение в пакете VSIX. Дополнительные сведения см. в разделе [элемент MEFComponent (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Если расширение включает команду SharePoint, которая вызывает серверную объектную модель для SharePoint, добавьте `Microsoft.VisualStudio.Assembly` элемент в `Assets` элемент. Задайте в качестве значения нового элемента относительный путь к сборке, реализующей команду SharePoint в пакете VSIX. Дополнительные сведения см. в разделе [элемент Asset (Схема VSX)](/previous-versions/dd393737(v=vs.110)).

    - Если расширение содержит шаблон проекта или элемента, добавьте `ProjectTemplate` `ItemTemplate` элемент или в `Assets` элемент. Задайте в качестве значения нового элемента относительный путь к папке, содержащей шаблон, в пакете VSIX. Дополнительные сведения см. в разделе [элемент ProjectTemplate (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) и [элемент ITEMTEMPLATE (Схема VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Если расширение содержит настраиваемый мастер для шаблона проекта или элемента, добавьте `Assembly` элемент в `Assets` элемент. Задайте для нового элемента относительный путь к сборке в пакете VSIX, а затем присвойте `AssemblyName` атрибуту полное имя сборки (включая версию, язык и региональные параметры и токен открытого ключа). Дополнительные сведения см. в разделе [элемент dependency (Схема VSX)](/previous-versions/dd393682(v=vs.110)).

### <a name="example"></a>Пример

В следующем примере показано содержимое файла Extension. vsixmanifest для расширения инструментов SharePoint. Расширение реализуется в сборке с именем Contoso.ProjectExtension.dll. Расширение включает сборку команд SharePoint с именем Contoso.ExtensionCommands.dll и шаблон элемента в папке с именем **ItemTemplate** в пакете VSIX. В этом примере предполагается, что обе сборки находятся в той же папке, что и файл Extension. vsixmanifest в пакете VSIX.

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

## <a name="see-also"></a>См. также раздел

- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Расширение узла подключений SharePoint в обозревателе сервера](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Отладка расширений для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)