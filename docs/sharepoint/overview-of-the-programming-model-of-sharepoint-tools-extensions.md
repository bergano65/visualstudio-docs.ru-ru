---
title: Общие сведения о модели программирования расширений инструментов SharePoint
titleSuffix: ''
description: Ознакомьтесь с обзорной моделью программирования расширений инструментов SharePoint. Реализуйте интерфейсы расширяемости. Изучите объектные модели.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b823aecff4f05208094bd98b559a661c7f23fc5b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970534"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Обзор модели программирования расширений инструментов SharePoint
  При создании расширения для инструментов SharePoint в Visual Studio сначала необходимо реализовать один или несколько интерфейсов расширения, предоставляемых инструментами SharePoint. Как правило, для реализации возможностей в расширении вы также будете использовать другие типы, предоставляемые инструментами SharePoint. В некоторых случаях можно также использовать типы в других объектных моделях, предоставляемых Visual Studio и SharePoint. Необходимо понимать назначение каждой из этих объектных моделей и уметь использовать их друг с другом для создания расширений для инструментов SharePoint.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Расширение средств SharePoint путем реализации интерфейсов расширяемости
 Visual Studio использует платформу Managed Extensibility Framework (MEF) в .NET Framework 4 для предоставления модели расширения для инструментов SharePoint. MEF — это API-интерфейс (реализованный в сборке System.ComponentModel.Composition), позволяющий приложениям предоставлять точки расширения, а также обнаруживать и загружать расширения во время выполнения. Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index).

 Для расширения инструментов SharePoint реализуйте один или несколько интерфейсов расширения, предоставляемых Visual Studio. К реализации интерфейса необходимо также применить <xref:System.ComponentModel.Composition.ExportAttribute> и, по мере необходимости, дополнительные атрибуты, определяемые инструментами SharePoint. В таблице ниже перечислены интерфейсы, которые можно реализовать для расширения инструментов SharePoint.

|Интерфейс|Описание|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Реализация этого интерфейса позволяет определить новый тип элемента проекта SharePoint. Пример см. в разделе [руководство. определение типа элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Реализация этого интерфейса позволяет расширить тип элемента проекта SharePoint, который уже установлен в Visual Studio. Пример см. в разделе [как создать расширение элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Реализация этого интерфейса позволяет расширить проекты SharePoint. Пример см. в разделе [руководство. Создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Реализация этого интерфейса позволяет определить новый шаг развертывания, выполняемый при развертывании или отзыве элемента проекта SharePoint. Пример см. в разделе [Пошаговое руководство. Создание настраиваемого шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Реализуйте этот интерфейс, чтобы расширить существующий узел в узле " **подключения SharePoint** " в окне **Обозреватель сервера** . Пример см. в разделе [руководство. расширение узла SharePoint в обозреватель сервера](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Реализуйте этот интерфейс, чтобы определить новый тип узла в узле " **подключения SharePoint** " в окне **Обозреватель сервера** . Пример см. в разделе [руководство. расширение узла SharePoint в обозреватель сервера](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Реализация этого интерфейса позволяет определить настраиваемое правило проверки компонента. Пример см. в разделе [Создание настраиваемых правил проверки компонентов и пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Реализация этого интерфейса позволяет определить настраиваемое правило проверки пакета. Пример см. в разделе [Создание настраиваемых правил проверки компонентов и пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

 После реализации расширения инструментов SharePoint необходимо развернуть сборку расширения в пакете расширения Visual Studio (VSIX-файл), чтобы позволить Visual Studio находить и загружать расширения. Дополнительные сведения см. [в статье Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Общие сведения об объектных моделях, используемых в расширениях инструментов SharePoint
 Существует несколько объектных моделей, которые можно использовать при создании расширений для инструментов SharePoint.

- *Объектная модель инструментов SharePoint*. Эта объектная модель предоставляет интерфейсы расширения, реализуемые для создания расширений инструментов SharePoint и других связанных типов.

- *Модели объектов автоматизации и интеграции Visual Studio*. Эти объектные модели используются для доступа к возможностям Visual Studio, которые выходят за рамки объектной модели инструментов SharePoint.

    > [!NOTE]
    > Некоторые объекты в объектной модели инструментов SharePoint можно преобразовать в объекты в объектных моделях автоматизации и интеграции Visual Studio (и наоборот) с помощью службы проектов SharePoint. Дополнительные сведения см. в разделе [Преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

- *Серверные и клиентские объектные модели SharePoint*. Эти объектные модели используются для изменения сайта SharePoint или получения данных с сайта SharePoint из контекста расширения инструментов SharePoint.

### <a name="sharepoint-tools-object-model"></a>Объектная модель инструментов SharePoint
 Расширения инструментов SharePoint используют типы в объектной модели инструментов SharePoint для определения основного поведения и функциональных возможностей расширения. В следующих таблицах описываются пространства имен, входящие в эту объектную модель, по сборке, содержащей их.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|Пространство имен|Описание|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|Содержит типы, используемые для расширения и автоматизации системы проектов SharePoint. Например, можно расширить встроенные проекты и элементы проектов SharePoint или создать собственные элементы проектов. Дополнительные сведения см. в разделе [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Содержит типы, используемые для расширения процесса развертывания для проектов SharePoint, например создание шагов и конфигураций развертывания. Дополнительные сведения см. в разделе [Расширение упаковки и развертывания SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Содержит типы, используемые для расширения узлов в узле **подключения SharePoint** в окне **Обозреватель сервера** или для определения новых типов узлов. Дополнительные сведения см. в разделе [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|Содержит типы, используемые для доступа к определениям компонентов в проекте SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|Содержит типы, используемые для доступа к определениям пакетов в решении SharePoint.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|Содержит типы, используемые для настройки поведения проверки компонентов и пакетов для проектов SharePoint. Дополнительные сведения см. в разделе [Практическое руководство. Создание пользовательских правил проверки компонентов и пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|Пространство имен|Описание|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Содержит типы, которые можно использовать для создания пользовательских *команд SharePoint*. Команда SharePoint — это метод, который вызывает объектную модель сервера SharePoint из расширения инструментов SharePoint. Дополнительные сведения см. в разделе [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|Пространство имен|Описание|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Содержит типы, которые можно использовать для получения сведений о встроенных **Обозреватель сервера** узлах, представляющих отдельные компоненты на сайте SharePoint, таких как узел, представляющий список, поле или тип содержимого. Дополнительные сведения см. в разделе [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|

### <a name="visual-studio-automation-object-model"></a>Объектная модель автоматизации Visual Studio
 Объектная модель автоматизации Visual Studio предоставляет API-интерфейсы, которые можно использовать для автоматизации проектов Visual Studio и интегрированной среды разработки. Объектная модель Visual Studio используется для выполнения задач, связанных с проектами, которые не относятся к конкретному проекту SharePoint, или для выполнения других общих задач автоматизации в Visual Studio. Традиционно эта объектная модель часто используется в надстройках и макросах Visual Studio, однако ее также можно использовать в расширениях инструментов SharePoint.

 Основная часть объектной модели автоматизации Visual Studio определена в сборке *EnvDTE.dll* . Сборки *EnvDTE \\ \<version> . dll* предоставляют дополнительные функциональные возможности, появившиеся в конкретных версиях Visual Studio. Эти сборки входят в состав Visual Studio.

 Дополнительные сведения об объектной модели автоматизации см. в [справочнике по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

### <a name="visual-studio-integration-object-model"></a>Объектная модель интеграции Visual Studio
 Объектная модель интеграции предоставляет интерфейсы API, которые можно использовать для добавления компонентов в Visual Studio путем создания *VSPackage*. VSPackage — это модуль, который расширяет возможности интегрированной среды разработки Visual Studio, предоставляя настраиваемые компоненты, такие как окна инструментов, редакторы, конструкторы, службы и проекты.

 Объектную модель интеграции можно использовать при необходимости добавить новый компонент Visual Studio, который будет использоваться вместе со встроенными инструментами SharePoint. Например, при создании настраиваемого элемента проекта SharePoint, который представляет настраиваемое действие для сайта SharePoint, можно также создать модуль VSPackage, реализующий конструктор для настраиваемого действия. Конструктор можно связать с настраиваемым действием, добавив пункт контекстного меню к элементу проекта, который представляет настраиваемое действие в **Обозреватель решений**. Открыть конструктор можно, открыв его контекстное меню (щелкнув правой кнопкой мыши элемент проекта настраиваемого действия или выбрав его, а затем нажав клавиши **SHIFT** + **F10** ), а затем выбрав **Открыть**.

 Эта объектная модель определяется в наборе сборок, которые входят в состав пакета SDK Visual Studio. Некоторые из основных сборок в этой модели объектов включают *Microsoft.VisualStudio.Shell.11.0.dll*, *Microsoft.VisualStudio.Shell.Interop.dll* и *Microsoft.VisualStudio.OLE.Interop.dll*.

 Дополнительные сведения об объектной модели интеграции см. в разделе [Общие сведения о модели автоматизации](../extensibility/internals/automation-model-overview.md) и [справочнике по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

### <a name="sharepoint-object-models"></a>Объектные модели SharePoint
 Расширения инструментов SharePoint могут использовать API-интерфейсы SharePoint для изменения сайта SharePoint или получения данных с сайта SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] предоставляют две разные объектные модели: объектную модель сервера и объектную модель клиента.

 В любой из объектных моделей в расширении инструментов SharePoint можно использовать API-интерфейсы, однако каждая объектная модель имеет свои преимущества и недостатки в контексте расширений инструментов SharePoint. Дополнительные сведения см. в разделе [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

|Объектная модель|Описание|
|------------------|-----------------|
|Объектная модель сервера|Объектная модель сервера предоставляет доступ ко всем возможностям, предоставляемым [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] программно. Эта объектная модель предназначена для использования решениями SharePoint, которые выполняются на сервере SharePoint. Большая часть этой объектной модели определена в сборке *Microsoft.SharePoint.dll* . Дополнительные сведения о серверной объектной модели см. [в разделе Использование объектной модели Server-Side SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).|
|Объектная модель клиента|Объектная модель клиента — это подмножество объектной модели сервера, которое можно использовать для взаимодействия с данными SharePoint с удаленного клиента или сервера. Она предназначена для сведения к минимуму числа циклов для выполнения типичных задач. Большая часть клиентской объектной модели определена в сборках *Microsoft.SharePoint.Client.dll* и *Microsoft.SharePoint.Client.Runtime.dll* . Дополнительные сведения о клиентской объектной модели см. в разделе [управляемая клиентская объектная модель](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).|

## <a name="see-also"></a>См. также раздел
- [Расширение средств SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Вызов объектных моделей SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
