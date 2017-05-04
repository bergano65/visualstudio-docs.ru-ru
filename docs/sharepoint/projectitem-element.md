---
title: "ProjectItem Element | Microsoft Docs"
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
  - "ProjectItem element"
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# ProjectItem Element
  Представляет элемент проекта SharePoint.  Это обязательный корневой элемент SPDATA\-файла.  
  
## Синтаксис  
  
```  
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"  
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"  
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"  
    SupportedTrustLevels = "Trust levels that the project item supports"  
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"  
    Type="Identifier for the project item">  
  <Files>...</Files>  
  <ProjectItemFolder>...</ProjectItemFolder>  
  <SafeControls>...</SafeControls>  
  <FeatureProperties>...</FeatureProperties>  
  <ExtensionData>...</ExtensionData>  
</ProjectItem>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние элементы и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|**DefaultFile**|Необязательный атрибут элемента **xs:string**.<br /><br /> Относительный путь, включая имя файла, который открывается в редакторе Visual Studio при открытии элемента проекта SharePoint в **обозревателе решений**.  Этот путь задается относительно папки, содержащей SPDATA\-файл.|  
|**FeatureReceiverClass**|Необязательный атрибут элемента **xs:string**.<br /><br /> Полное имя класса получателя компонента для данного элемента проекта SharePoint.  Дополнительные сведения о приемниках компонента см. в разделе [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Необязательный атрибут элемента **xs:string**.<br /><br /> Задает полное имя сборки, определяющей приемника компонента для этого элемента проекта SharePoint.  Дополнительные сведения о приемниках компонента см. в разделе [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  Дополнительные сведения о полных именах сборок см. в разделе [Имена сборок](../Topic/Assembly%20Names.md).|  
|**SupportedTrustLevels**|Необязательный атрибут элемента **xs:string**.<br /><br /> Задает уровни доверия, которые поддерживает данный элемент проекта SharePoint.  Возможны следующие значения: Sandboxed, FullTrust или All.  Значение "All" указывает оба параметра \(Sandboxed и FullTrust\).<br /><br /> В настраиваемом типе проектов SharePoint значение этого атрибута соответствует значению, заданному для свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> в пользовательской реализации метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Если указать для этого атрибута другое значение, Visual Studio перезаписывает значение таким образом, что оно задает тот же уровень доверия, что и свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>.|  
|**SupportedDeploymentScopes**|Необязательный атрибут элемента **xs:string**.<br /><br /> Задает области развертывания, которые поддерживает данный элемент проекта SharePoint.  Это значение представляет строку с разделением запятой, которая состоит из одной или нескольких следующих строк: Farm, Site, Web, WebApplication или Package.  Например, "Интернет, сайт".<br /><br /> В настраиваемом типе проектов SharePoint значение этого атрибута соответствует значению, заданному для свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> в пользовательской реализации метода <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Если указать для этого атрибута другое значение, Visual Studio перезаписывает значение таким образом, что оно задает тот же уровень доверия, что и свойство <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>.|  
|**Type**|Обязательный атрибут элемента **xs:string**.<br /><br /> Идентификатор для элемента проекта SharePoint.  В пользовательском типе элемента проекта SharePoint идентификатор представляет собой строку, передаваемую в <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Дополнительные сведения см. в разделе [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Список идентификаторов для встроенных элементов проекта SharePoint, включенных в Visual Studio, см. в разделе [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.<br /><br /> Можно включить только один элемент **ExtensionData**.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию значений свойства, включенных в "Компонент" при развертывании в SharePoint.<br /><br /> Можно включить только один элемент **FeatureProperties**.|  
|[Файлы](../sharepoint/files-element.md)|Необязательный элемент **FileCollectionType**.<br /><br /> Указывает файлы для развертывания с элементом проекта SharePoint, такие как файлы элемента Feature и выходные файлы зависимых проектов, отличных от проектов SharePoint.<br /><br /> Необходимо включить элемент **Files** или **ProjectItemFolder**, но не оба сразу.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Необязательный элемент **ProjectItemFolderType**.<br /><br /> Представляет сопоставляемую папку.<br /><br /> Необходимо включить элемент **Files** или **ProjectItemFolder**, но не оба сразу.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию элементов управления ASPX или веб\-частей, отмеченных как безопасные, с доступом для любых пользователей на любой странице ASPX сайта SharePoint.<br /><br /> Можно включить только один элемент **SafeControls**.|  
  
### Родительские элементы  
 Отсутствует.  
  
## Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым**|Нет|  
  
## См. также  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  