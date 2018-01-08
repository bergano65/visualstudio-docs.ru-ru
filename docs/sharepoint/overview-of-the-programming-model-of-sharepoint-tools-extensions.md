---
title: "Обзор SharePoint модели программирования расширений средств | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
ms.assetid: aec8165b-dff9-47be-82a5-3fa38e579297
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3b8d869dab81273262d23b7aa905370f530b24c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Обзор модели программирования расширений средств SharePoint
  При создании расширения для инструментов SharePoint в Visual Studio сначала необходимо реализовать один или несколько интерфейсов расширения, предоставляемых инструментами SharePoint. Как правило, для реализации возможностей в расширении вы также будете использовать другие типы, предоставляемые инструментами SharePoint. В некоторых случаях можно также использовать типы в других объектных моделях, предоставляемых Visual Studio и SharePoint. Необходимо понимать назначение каждой из этих объектных моделей и уметь использовать их друг с другом для создания расширений для средств SharePoint.  
  
## <a name="extending-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Расширение инструментов SharePoint путем реализации интерфейсов расширения  
 Visual Studio использует платформу Managed Extensibility Framework (MEF) в .NET Framework 4 для предоставления модели расширения для инструментов SharePoint. MEF — это API-интерфейс (реализованный в сборке System.ComponentModel.Composition), позволяющий приложениям предоставлять точки расширения, а также обнаруживать и загружать расширения во время выполнения. Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework &#40; MEF &#41; ](/dotnet/framework/mef/index).  
  
 Для расширения инструментов SharePoint реализуйте один или несколько интерфейсов расширения, предоставляемых Visual Studio. К реализации интерфейса необходимо также применить <xref:System.ComponentModel.Composition.ExportAttribute> и, по мере необходимости, дополнительные атрибуты, определяемые инструментами SharePoint. В таблице ниже перечислены интерфейсы, которые можно реализовать для расширения инструментов SharePoint.  
  
|Интерфейс|Описание:|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Реализация этого интерфейса позволяет определить новый тип элемента проекта SharePoint. Пример см. в разделе [как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Реализация этого интерфейса позволяет расширить тип элемента проекта SharePoint, который уже установлен в Visual Studio. Пример см. в разделе [как: создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Реализация этого интерфейса позволяет расширить проекты SharePoint. Пример см. в разделе [как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Реализация этого интерфейса позволяет определить новый шаг развертывания, выполняемый при развертывании или отзыве элемента проекта SharePoint. Пример см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Реализация этого интерфейса позволяет расширить существующий узел в разделе **подключения SharePoint** узел в **обозревателя серверов** окна. Пример см. в разделе [как: расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Реализация этого интерфейса позволяет определить новый тип узла в группе **подключения SharePoint** узел в **обозревателя серверов** окна. Пример см. в разделе [как: расширение узла SharePoint в обозревателе серверов](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Реализация этого интерфейса позволяет определить настраиваемое правило проверки компонента. Пример см. в разделе [как: Создание пользовательских компонентов и правила проверки пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Реализация этого интерфейса позволяет определить настраиваемое правило проверки пакета. Пример см. в разделе [как: Создание пользовательских компонентов и правила проверки пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
  
 После реализации расширения инструментов SharePoint необходимо развернуть сборку расширения в пакете расширения Visual Studio (VSIX-файл), чтобы позволить Visual Studio находить и загружать расширения. Дополнительные сведения см. в разделе [развертывание расширений для средств SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="understanding-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Основные сведения об объектных моделях, которые используются в расширениях инструментов SharePoint  
 Существует несколько объектных моделей, которые можно использовать при создании расширений для инструментов SharePoint.  
  
-   *Объектная модель инструментов SharePoint*. Эта объектная модель предоставляет интерфейсы расширения, реализуемые для создания расширений инструментов SharePoint и других связанных типов.  
  
-   *Visual Studio автоматизации и интеграции объектные модели*. Эти объектные модели используются для доступа к возможностям Visual Studio, которые выходят за рамки объектной модели инструментов SharePoint.  
  
    > [!NOTE]  
    >  Некоторые объекты в объектной модели инструментов SharePoint можно преобразовать в объекты в объектных моделях автоматизации и интеграции Visual Studio (и наоборот) с помощью службы проектов SharePoint. Дополнительные сведения см. в разделе [преобразование между типами системы проектов SharePoint и другими типами проектов Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
-   *Объектные модели SharePoint server и клиента*. Эти объектные модели используются для изменения сайта SharePoint или получения данных с сайта SharePoint из контекста расширения инструментов SharePoint.  
  
### <a name="sharepoint-tools-object-model"></a>Объектная модель инструментов SharePoint  
 Расширения инструментов SharePoint используют типы в объектной модели инструментов SharePoint для определения основного поведения и функциональных возможностей расширения. В следующей таблице описаны пространства имен, которые включены в эту объектную модель.  
  
|Сборка|Пространство имен|Описание:|  
|--------------|---------------|-----------------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|Содержит типы, используемые для расширения и автоматизации системы проектов SharePoint. Например, можно расширить встроенные проекты и элементы проектов SharePoint или создать собственные элементы проектов. Дополнительные сведения см. в разделе [расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Содержит типы, используемые для расширения процесса развертывания для проектов SharePoint, например создание шагов и конфигураций развертывания. Дополнительные сведения см. в разделе [расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Содержит типы, используемые для расширения узлов в **подключения SharePoint** узел в **обозревателя серверов** окна, или для определения новых типов узлов. Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|Содержит типы, используемые для доступа к определениям компонентов в проекте SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|Содержит типы, используемые для доступа к определениям пакетов в решении SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|Содержит типы, используемые для настройки поведения проверки компонентов и пакетов для проектов SharePoint. Дополнительные сведения см. в разделе [как: Создание пользовательских компонентов и правила проверки пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Содержит типы, которые можно использовать для создания пользовательских *команды SharePoint*. Команда SharePoint — это метод, который вызывает объектную модель сервера SharePoint из расширения инструментов SharePoint. Дополнительные сведения см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Содержит типы, которые можно использовать для получения сведений о встроенных **обозревателя серверов** узлы, которые представляют отдельные компоненты на сайте SharePoint, например узел, представляющий список, поле или тип содержимого. Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
  
### <a name="visual-studio-automation-object-model"></a>Объектная модель автоматизации Visual Studio  
 Объектная модель автоматизации Visual Studio предоставляет API-интерфейсы, которые можно использовать для автоматизации проектов Visual Studio и интегрированной среды разработки. Объектная модель Visual Studio используется для выполнения задач, связанных с проектами, которые не относятся к конкретному проекту SharePoint, или для выполнения других общих задач автоматизации в Visual Studio. Традиционно эта объектная модель часто используется в надстройках и макросах Visual Studio, однако ее также можно использовать в расширениях инструментов SharePoint.  
  
 Основная часть объектной модели автоматизации Visual Studio определена в сборке EnvDTE.dll. EnvDTE*версии*.dll обеспечивают дополнительные функциональные возможности, которая была представлена в определенных версиях Visual Studio. Эти сборки входят в состав Visual Studio.  
  
 Дополнительные сведения об объектной модели автоматизации см. в разделе [Справочник по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
### <a name="visual-studio-integration-object-model"></a>Объектная модель интеграции Visual Studio  
 Объектная модель интеграции предоставляет API, которые можно использовать для добавления возможностей в Visual Studio путем создания *VSPackage*. VSPackage — это модуль, который расширяет возможности интегрированной среды разработки Visual Studio, предоставляя настраиваемые компоненты, такие как окна инструментов, редакторы, конструкторы, службы и проекты.  
  
 Объектную модель интеграции можно использовать при необходимости добавить новый компонент Visual Studio, который будет использоваться вместе со встроенными инструментами SharePoint. Например, при создании настраиваемого элемента проекта SharePoint, который представляет настраиваемое действие для сайта SharePoint, можно также создать модуль VSPackage, реализующий конструктор для настраиваемого действия. Конструктор можно связать с настраиваемым действием, Добавление пункта контекстного меню в элемент проекта, который представляет настраиваемое действие в **обозревателе решений**. Открыть конструктор можно, открыв его контекстное меню (щелкнуть правой кнопкой мыши проект настраиваемого действия элемента или выбрав его, затем нажав клавиши Shift + F10 ключи) и выбрав **откройте**.  
  
 Эта объектная модель определяется в наборе сборок, которые входят в состав пакета SDK Visual Studio. Некоторые из основных сборок в этой объектной модели включают Microsoft.VisualStudio.Shell.11.0.dll, Microsoft.VisualStudio.Shell.Interop.dll и Microsoft.VisualStudio.OLE.Interop.dll.  
  
 Дополнительные сведения об объектной модели интеграции см. в разделе [Общие сведения о модели автоматизации](/visualstudio/extensibility/internals/automation-model-overview) и [Справочник по Visual Studio SDK](/visualstudio/extensibility/visual-studio-sdk-reference).  
  
### <a name="sharepoint-object-models"></a>Объектные модели SharePoint  
 Расширения инструментов SharePoint могут использовать API-интерфейсы SharePoint для изменения сайта SharePoint или получения данных с сайта SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] предоставляют две разные объектные модели: объектную модель сервера и объектную модель клиента.  
  
 В любой из объектных моделей в расширении инструментов SharePoint можно использовать API-интерфейсы, однако каждая объектная модель имеет свои преимущества и недостатки в контексте расширений инструментов SharePoint. Дополнительные сведения см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
|Объектная модель|Описание:|  
|------------------|-----------------|  
|Объектная модель сервера|Объектная модель сервера предоставляет доступ ко всем возможностям, предоставляемым [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] программно. Эта объектная модель предназначена для использования решениями SharePoint, которые выполняются на сервере SharePoint. Большая часть этой объектной модели определяется в сборке Microsoft.SharePoint.dll. Дополнительные сведения об объектной модели сервера см. в разделе [с помощью объектной модели SharePoint Foundation серверные](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Объектная модель клиента|Объектная модель клиента — это подмножество объектной модели сервера, которое можно использовать для взаимодействия с данными SharePoint с удаленного клиента или сервера. Она предназначена для сведения к минимуму числа циклов для выполнения типичных задач. Большая часть объектной модели клиента определяется в сборках Microsoft.SharePoint.Client.dll и Microsoft.SharePoint.Client.Runtime.dll. Дополнительные сведения об объектной модели клиента см. в разделе [управляемая клиентская объектная модель](http://go.microsoft.com/fwlink/?LinkId=177797).|  
  
## <a name="see-also"></a>См. также  
 [Расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Обращение к объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Использование службы проектов SharePoint](../sharepoint/using-the-sharepoint-project-service.md)  
  
  