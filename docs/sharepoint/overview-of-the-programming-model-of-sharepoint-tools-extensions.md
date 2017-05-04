---
title: "Overview of the Programming Model of SharePoint Tools Extensions | Microsoft Docs"
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
  - "Visual Studio, extending tools"
  - "SharePoint development in Visual Studio, extensibility object models"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: aec8165b-dff9-47be-82a5-3fa38e579297
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Overview of the Programming Model of SharePoint Tools Extensions
  При создании расширения для инструментов SharePoint в Visual Studio сначала необходимо реализовать один или несколько интерфейсов расширения, предоставляемых инструментами SharePoint.  Как правило, для реализации возможностей в расширении вы также будете использовать другие типы, предоставляемые инструментами SharePoint.  В некоторых случаях можно также использовать типы в других объектных моделях, предоставляемых Visual Studio и SharePoint.  Необходимо понимать назначение каждой из этих объектных моделей и уметь использовать их друг с другом для создания расширений для инструментов SharePoint.  
  
## Расширение инструментов SharePoint путем реализации интерфейсов расширения  
 Visual Studio использует платформу Managed Extensibility Framework \(MEF\) в .NET Framework 4 для предоставления модели расширения для инструментов SharePoint.  MEF — это API\-интерфейс \(реализованный в сборке System.ComponentModel.Composition\), позволяющий приложениям предоставлять точки расширения, а также обнаруживать и загружать расширения во время выполнения.  Дополнительные сведения о MEF см. в разделе [Managed Extensibility Framework &#40;MEF&#41;](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
 Для расширения инструментов SharePoint реализуйте один или несколько интерфейсов расширения, предоставляемых Visual Studio.  К реализации интерфейса необходимо также применить <xref:System.ComponentModel.Composition.ExportAttribute> и, по мере необходимости, дополнительные атрибуты, определяемые инструментами SharePoint.  В таблице ниже перечислены интерфейсы, которые можно реализовать для расширения инструментов SharePoint.  
  
|Интерфейс|Описание|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Реализация этого интерфейса позволяет определить новый тип элемента проекта SharePoint.  Пример см. в разделе [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Реализация этого интерфейса позволяет расширить тип элемента проекта SharePoint, который уже установлен в Visual Studio.  Пример см. в разделе [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Реализация этого интерфейса позволяет расширить проекты SharePoint.  Пример см. в разделе [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Реализация этого интерфейса позволяет определить новый шаг развертывания, выполняемый при развертывании или отзыве элемента проекта SharePoint.  Пример см. в разделе [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Реализация этого интерфейса позволяет расширить существующий узел в узле **Подключения SharePoint** окна **обозревателя серверов**.  Пример см. в разделе [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Реализация этого интерфейса позволяет определить новый тип узла в узле **Подключения SharePoint** окна **обозревателя серверов**.  Пример см. в разделе [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Реализация этого интерфейса позволяет определить настраиваемое правило проверки компонента.  Пример см. в разделе [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Реализация этого интерфейса позволяет определить настраиваемое правило проверки пакета.  Пример см. в разделе [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
  
 После реализации расширения инструментов SharePoint необходимо развернуть сборку расширения в пакете расширения Visual Studio \(VSIX\-файл\), чтобы позволить Visual Studio находить и загружать расширения.  Дополнительные сведения см. в разделе [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Основные сведения об объектных моделях, которые используются в расширениях инструментов SharePoint  
 Существует несколько объектных моделей, которые можно использовать при создании расширений для инструментов SharePoint.  
  
-   *Объектная модель инструментов SharePoint*.  Эта объектная модель предоставляет интерфейсы расширения, реализуемые для создания расширений инструментов SharePoint и других связанных типов.  
  
-   *Объектные модели автоматизации и интеграции Visual Studio*.  Эти объектные модели используются для доступа к возможностям Visual Studio, которые выходят за рамки объектной модели инструментов SharePoint.  
  
    > [!NOTE]  
    >  Некоторые объекты в объектной модели инструментов SharePoint можно преобразовать в объекты в объектных моделях автоматизации и интеграции Visual Studio \(и наоборот\) с помощью службы проектов SharePoint.  Дополнительные сведения см. в разделе [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
-   *Объектные модели сервера и клиента SharePoint*.  Эти объектные модели используются для изменения сайта SharePoint или получения данных с сайта SharePoint из контекста расширения инструментов SharePoint.  
  
### Объектная модель инструментов SharePoint  
 Расширения инструментов SharePoint используют типы в объектной модели инструментов SharePoint для определения основного поведения и функциональных возможностей расширения.  В следующей таблице описаны пространства имен, которые включены в эту объектную модель.  
  
|Сборка|Пространство имен|Описание|  
|------------|-----------------------|--------------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|Содержит типы, используемые для расширения и автоматизации системы проектов SharePoint.  Например, можно расширить встроенные проекты и элементы проектов SharePoint или создать собственные элементы проектов.  Дополнительные сведения см. в разделе [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Содержит типы, используемые для расширения процесса развертывания для проектов SharePoint, например создание шагов и конфигураций развертывания.  Дополнительные сведения см. в разделе [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Содержит типы, используемые для расширения узлов в узле **Подключения SharePoint** окна **обозревателя серверов** или для определения новых типов узлов.  Дополнительные сведения см. в разделе [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|Содержит типы, используемые для доступа к определениям компонентов в проекте SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|Содержит типы, используемые для доступа к определениям пакетов в решении SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|Содержит типы, используемые для настройки поведения проверки компонентов и пакетов для проектов SharePoint.  Дополнительные сведения см. в разделе [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Содержит типы, используемые для создания настраиваемых *команд SharePoint*.  Команда SharePoint — это метод, который вызывает объектную модель сервера SharePoint из расширения инструментов SharePoint.  Дополнительные сведения см. в разделе [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Содержит типы, используемые для получения сведений о встроенных узлах **обозревателя серверов**, которые представляют отдельные компоненты на сайте SharePoint \(например, узел, представляющий список, поле или тип содержимого\).  Дополнительные сведения см. в разделе [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
  
### Объектная модель автоматизации Visual Studio  
 Объектная модель автоматизации Visual Studio предоставляет API\-интерфейсы, которые можно использовать для автоматизации проектов Visual Studio и интегрированной среды разработки.  Объектная модель Visual Studio используется для выполнения задач, связанных с проектами, которые не относятся к конкретному проекту SharePoint, или для выполнения других общих задач автоматизации в Visual Studio.  Традиционно эта объектная модель часто используется в надстройках и макросах Visual Studio, однако ее также можно использовать в расширениях инструментов SharePoint.  
  
 Основная часть объектной модели автоматизации Visual Studio определена в сборке EnvDTE.dll.  Сборки EnvDTE80.dll, EnvDTE90.dll, EnvDTE100.dll и EnvDTE110.dll обеспечивают дополнительные функциональные возможности, которые были представлены в Visual Studio 2005, Visual Studio 2008, Visual Studio 2010 и [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] соответственно.  Эти сборки входят в состав Visual Studio.  
  
 Дополнительные сведения об объектной модели автоматизации см. в разделах [Расширение среды Visual Studio](http://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792) и [Справочник по автоматизации и возможностям расширения среды](http://msdn.microsoft.com/library/93112562-db21-4188-9383-ed19ad79bddf).  
  
### Объектная модель интеграции Visual Studio  
 Объектная модель интеграции предоставляет API\-интерфейсы, которые можно использовать для добавления возможностей в Visual Studio путем создания модуля *VSPackage*.  VSPackage — это модуль, который расширяет возможности интегрированной среды разработки Visual Studio, предоставляя настраиваемые компоненты, такие как окна инструментов, редакторы, конструкторы, службы и проекты.  
  
 Объектную модель интеграции можно использовать при необходимости добавить новый компонент Visual Studio, который будет использоваться вместе со встроенными инструментами SharePoint.  Например, при создании настраиваемого элемента проекта SharePoint, который представляет настраиваемое действие для сайта SharePoint, можно также создать модуль VSPackage, реализующий конструктор для настраиваемого действия.  Конструктор можно связать с настраиваемым действием, добавив пункт контекстного меню в элемент проекта, который представляет настраиваемое действие в **обозревателе решений**.  Открыть конструктор можно, вызвав его контекстное меню \( для этого щелкните элемент проекта настраиваемого действия правой кнопкой мыши или выберите его и нажмите клавиши Shift\+F10\) и выбрав в нем пункт **Открыть**.  
  
 Эта объектная модель определяется в наборе сборок, которые входят в состав пакета SDK Visual Studio.  Некоторые из основных сборок в этой объектной модели включают Microsoft.VisualStudio.Shell.11.0.dll, Microsoft.VisualStudio.Shell.Interop.dll и Microsoft.VisualStudio.OLE.Interop.dll.  
  
 Дополнительные сведения об объектной модели интеграции см. в разделе [Архитектура расширения Visual Studio](/visual-cpp/misc/visual-studio-extensibility-architecture) и [Справочник по Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
### Объектные модели SharePoint  
 Расширения инструментов SharePoint могут использовать API\-интерфейсы SharePoint для изменения сайта SharePoint или получения данных с сайта SharePoint.  [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] предоставляют две разные объектные модели: объектную модель сервера и объектную модель клиента.  
  
 В любой из объектных моделей в расширении инструментов SharePoint можно использовать API\-интерфейсы, однако каждая объектная модель имеет свои преимущества и недостатки в контексте расширений инструментов SharePoint.  Дополнительные сведения см. в разделе [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
|Объектная модель|Описание|  
|----------------------|--------------|  
|Объектная модель сервера|Объектная модель сервера предоставляет доступ ко всем возможностям, предоставляемым [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] программно.  Эта объектная модель предназначена для использования решениями SharePoint, которые выполняются на сервере SharePoint.  Большая часть этой объектной модели определяется в сборке Microsoft.SharePoint.dll.  Дополнительные сведения об объектной модели сервера см. в статье [Использование серверной объектной модели в SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Объектная модель клиента|Объектная модель клиента — это подмножество объектной модели сервера, которое можно использовать для взаимодействия с данными SharePoint с удаленного клиента или сервера.  Она предназначена для сведения к минимуму числа циклов для выполнения типичных задач.  Большая часть объектной модели клиента определяется в сборках Microsoft.SharePoint.Client.dll и Microsoft.SharePoint.Client.Runtime.dll.  Дополнительные сведения об объектной модели клиента см. в статье [Управляемая клиентская объектная модель](http://go.microsoft.com/fwlink/?LinkId=177797).|  
  
## См. также  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)  
  
  