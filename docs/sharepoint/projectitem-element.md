---
title: Элемент ProjectItem | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2768a2e55b3e38158f2ef6b856a653a1a2c12dfa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562407"
---
# <a name="projectitem-element"></a>ProjectItem - элемент
  Представляет элемент проекта SharePoint. Этот элемент обязательный корневой элемент из *.spdata* файла.

## <a name="syntax"></a>Синтаксис

```xml
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

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|**DefaultFile**|Необязательный **xs: строка** атрибута.<br /><br /> Относительный путь, включая имя файла, файла, который открывается в редакторе Visual Studio при открытии элемента проекта SharePoint в **обозревателе решений**. Путь является относительным из папки, которая содержит *.spdata* файла.|
|**FeatureReceiverClass**|Необязательный **xs: String** атрибута.<br /><br /> Полное имя класса-получателя компонента для этого элемента проекта SharePoint. Дополнительные сведения о приемниках компонентов см. в разделе [сведениями упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**FeatureReceiverAssembly**|Необязательный **xs: String** атрибута.<br /><br /> Указывает полное имя сборки, определяющей приемника компонента для этого элемента проекта SharePoint. Дополнительные сведения о приемниках компонентов см. в разделе [сведениями упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Дополнительные сведения о полные имена сборок, см. в разделе [имена сборок](/dotnet/framework/app-domains/assembly-names).|
|**SupportedTrustLevels**|Необязательный **xs: String** атрибута.<br /><br /> Указывает уровни доверия, которые поддерживает данный элемент проекта SharePoint. Это значение может принимать одно из следующих строк: Изолированной, FullTrust, или все. Значение All указывает Sandboxed и FullTrust.<br /><br /> В поле пользовательского типа элемента проекта SharePoint, значение этого атрибута соответствует значению, назначаемый <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> свойство в текущей реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод. Если указать другое значение для этого атрибута, Visual Studio перезаписывает значение, чтобы она тот же уровень доверия, указываемое в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> свойство.|
|**SupportedDeploymentScopes**|Необязательный **xs: String** атрибута.<br /><br /> Задает области развертывания, которые поддерживает данный элемент проекта SharePoint. Это значение является строка с разделителями запятыми, состоящая из одного или нескольких из следующих строк: Фермы, сайтов, Интернета, веб-приложения или пакета. Пример: `Web, Site`<br /><br /> В поле пользовательского типа элемента проекта SharePoint, значение этого атрибута соответствует значению, назначаемый <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> свойство в текущей реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метод. Если указать другое значение для этого атрибута, Visual Studio перезаписывает значение, чтобы она тот же уровень доверия, указываемое в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> свойство.|
|**Type**|Требуется **xs: String** атрибута.<br /><br /> Идентификатор для элемента проекта SharePoint. В поле пользовательского типа элемента проекта SharePoint, идентификатор является строка, которая передается <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Дополнительные сведения см. в разделе [Как Определить тип элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Список идентификаторов для встроенных элементов проектов SharePoint, включенные в Visual Studio, см. в разделе [элементы проекта SharePoint, расширить](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию пользовательских элементов данных, которые связаны с элементом проекта SharePoint.<br /><br /> Может включать только одну **ExtensionData** элемент.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию значений свойств, которые входят в состав компонентом при его развертывании в SharePoint.<br /><br /> Может включать только одну **FeatureProperties** элемент.|
|[Файлы](../sharepoint/files-element.md)|Необязательный **FileCollectionType** элемент.<br /><br /> Указывает файлы для развертывания с элементом проекта SharePoint, например элементов компонента файлов и выходных данных зависимого вне SharePoint проектов.<br /><br /> Включают в себя **файлы** или **ProjectItemFolder** , но не оба.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Необязательный **ProjectItemFolderType** элемент.<br /><br /> Представляет сопоставленную папку.<br /><br /> Включают в себя **файлы** или **ProjectItemFolder** , но не оба.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию элементов управления ASPX и веб-частей, отмеченных как безопасные для любого доступа пользователя к любой странице ASPX на сайте SharePoint.<br /><br /> Может включать только одну **SafeControls** элемент.|

### <a name="parent-elements"></a>Родительские элементы
 Отсутствует.

## <a name="element-information"></a>Сведения об элементе

|||
|-|-|
|**Пространство имен**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|ProjectItemModelSchema.xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также
[Rseference схемы элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
