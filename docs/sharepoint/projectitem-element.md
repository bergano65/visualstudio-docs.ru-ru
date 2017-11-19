---
title: "Элемент ProjectItem | Документы Microsoft"
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
helpviewer_keywords: ProjectItem element
ms.assetid: df588235-12a1-4798-bc56-ef81843de17f
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8a9f1ac258f6501aedb2fd89ce21514d785b25f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="projectitem-element"></a>Элемент ProjectItem
  Представляет элемент проекта SharePoint. Это обязательный корневой элемент SPDATA-файла.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|**DefaultFile**|Необязательный **xs: String** атрибута.<br /><br /> Относительный путь, включая имя файла, для файла, который открывается в редакторе Visual Studio при открытии элемента проекта SharePoint в **обозревателе решений**. Путь относительно папки, содержащей SPDATA-файла.|  
|**FeatureReceiverClass**|Необязательный **xs: String** атрибута.<br /><br /> Полное имя класса приемника компонента для этого элемента проекта SharePoint. Дополнительные сведения о приемниках компонента см. в разделе [предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Необязательный **xs: String** атрибута.<br /><br /> Указывает полное имя сборки, определяющей приемника компонента для этого элемента проекта SharePoint. Дополнительные сведения о приемниках компонента см. в разделе [предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Дополнительные сведения об именах полного имени сборки см. в разделе [имена сборок](/dotnet/framework/app-domains/assembly-names).|  
|**SupportedTrustLevels**|Необязательный **xs: String** атрибута.<br /><br /> Задает уровни доверия, которые поддерживает данный элемент проекта SharePoint. Это значение может быть одним из следующих строк: изолированное, полное доверие или All. Значение All указывает Sandboxed и FullTrust.<br /><br /> В поле пользовательского типа элемента проекта SharePoint, значение этого атрибута соответствует значению, которые назначены <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> свойство в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод. Если указать другое значение для этого атрибута, Visual Studio перезаписывает значение, чтобы указать тот же уровень доверия, указываемое в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> свойство.|  
|**SupportedDeploymentScopes**|Необязательный **xs: String** атрибута.<br /><br /> Задает области развертывания, которые поддерживает данный элемент проекта SharePoint. Это значение является строкой с разделителями запятыми, состоящая из одного или нескольких из следующих строк: фермы, сайта, Интернет, веб-приложения или пакета. Например, «Веб-сайта».<br /><br /> В поле пользовательского типа элемента проекта SharePoint, значение этого атрибута соответствует значению, которые назначены <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> свойство в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод. Если указать другое значение для этого атрибута, Visual Studio перезаписывает значение, чтобы указать тот же уровень доверия, указываемое в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> свойство.|  
|**Тип**|Требуется **xs: String** атрибута.<br /><br /> Идентификатор для элемента проекта SharePoint. В пользовательского типа элемента проекта SharePoint, идентификатор представляет собой строку, которая передается в <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Дополнительные сведения см. в разделе [как: определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Список идентификаторов для встроенных элементов проектов SharePoint, входящих в состав Visual Studio см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.<br /><br /> Можно включить только один **ExtensionData** элемента.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию значений свойств, которые входят в состав компонентом при его развертывании в SharePoint.<br /><br /> Можно включить только один **FeatureProperties** элемента.|  
|[Файлы](../sharepoint/files-element.md)|Необязательный **FileCollectionType** элемента.<br /><br /> Указывает файлы для развертывания с элементом проекта SharePoint, например элементов компонента файлов и выходных данных зависимого вне SharePoint проектов.<br /><br /> Необходимо включить **файлы** или **ProjectItemFolder** элемент, но не оба.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Необязательный **ProjectItemFolderType** элемента.<br /><br /> Представляет сопоставленную папку.<br /><br /> Необходимо включить **файлы** или **ProjectItemFolder** элемент, но не оба.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию элементов управления ASPX и веб-частей, отмеченных как безопасные для любому пользователю получить доступ к любой странице ASPX на сайте SharePoint.<br /><br /> Можно включить только один **SafeControls** элемента.|  
  
### <a name="parent-elements"></a>Родительские элементы  
 Отсутствует.  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Namespace**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочные материалы по схеме элементов для проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  