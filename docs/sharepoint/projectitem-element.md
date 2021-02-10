---
title: Элемент ProjectItem | Документация Майкрософт
description: Получите справочные сведения об элементе ProjectItem, который представляет элемент проекта SharePoint в справочнике по XML-схеме элемента проекта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2b94b44bfa442805c4c785a48c9f60f56eb8e002
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950592"
---
# <a name="projectitem-element"></a>ProjectItem - элемент
  Представляет элемент проекта SharePoint. Этот элемент является обязательным корневым элементом для файла *данных..*

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
|**DefaultFile**|Необязательный атрибут **xs: String** .<br /><br /> Относительный путь, включая имя файла, который открывается в редакторе Visual Studio при открытии элемента проекта SharePoint в **Обозреватель решений**. Путь определяется относительно папки, содержащей файл *данных с расширением.*|
|**феатуререцеиверкласс**|Необязательный атрибут **xs: String** .<br /><br /> Полное имя класса приемника компонента для этого элемента проекта SharePoint. Дополнительные сведения о приемниках компонентов см. [в разделе Предоставление сведений о упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**феатуререцеиверассембли**|Необязательный атрибут **xs: String** .<br /><br /> Указывает полное имя сборки, определяющей приемник компонента для этого элемента проекта SharePoint. Дополнительные сведения о приемниках компонентов см. [в разделе Предоставление сведений о упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Дополнительные сведения о полных именах сборок см. в разделе [имена сборок](/dotnet/framework/app-domains/assembly-names).|
|**суппортедтрустлевелс**|Необязательный атрибут **xs: String** .<br /><br /> Указывает уровни доверия, которые поддерживает этот элемент проекта SharePoint. Это значение может быть одной из следующих строк: "песочница", "FullTrust" или "все". Значение ALL указывает как "песочницу", так и "FullTrust".<br /><br /> В пользовательском типе элемента проекта SharePoint значение этого атрибута соответствует значению, присвоенному <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> свойству в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метода. Если указать другое значение для этого атрибута, Visual Studio перезапишет это значение, чтобы указать тот же уровень доверия, который вы указали в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> свойстве.|
|**суппортеддеплойментскопес**|Необязательный атрибут **xs: String** .<br /><br /> Указывает области развертывания, поддерживаемые этим элементом проекта SharePoint. Это значение представляет собой строку с разделителями-запятыми, которая состоит из одной или нескольких следующих строк: ферма, сайт, веб-приложение или пакет. Пример: `Web, Site`<br /><br /> В пользовательском типе элемента проекта SharePoint значение этого атрибута соответствует значению, присвоенному <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> свойству в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> метода. Если указать другое значение для этого атрибута, Visual Studio перезапишет это значение, чтобы указать тот же уровень доверия, который вы указали в <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> свойстве.|
|**Тип**|Обязательный атрибут **xs: String** .<br /><br /> Идентификатор элемента проекта SharePoint. В пользовательском типе элемента проекта SharePoint идентификатором является строка, передаваемая в <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Дополнительные сведения см. [в разделе инструкции. определение типа элемента проекта SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Список идентификаторов встроенных элементов проектов SharePoint, входящих в состав Visual Studio, см. в разделе [расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию пользовательских элементов данных, связанных с элементом проекта SharePoint.<br /><br /> Можно включить только один элемент **ExtensionData** .|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию значений свойств, включенных в компонент при развертывании в SharePoint.<br /><br /> Можно включить только один элемент **FeatureProperties** .|
|[Файлы](../sharepoint/files-element.md)|Необязательный элемент **филеколлектионтипе** .<br /><br /> Указывает файлы для развертывания с помощью элемента проекта SharePoint, такие как файлы элементов компонента и выходные данные зависимых проектов, не связанных с SharePoint.<br /><br /> Включайте либо **файлы** , либо элемент **ProjectItemFolder** , но не оба.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Необязательный элемент **прожектитемфолдертипе** .<br /><br /> Представляет сопоставленную папку.<br /><br /> Включайте либо **файлы** , либо элемент **ProjectItemFolder** , но не оба.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Необязательный элемент.<br /><br /> Представляет коллекцию элементов управления ASPX и веб-части, которые обозначены как безопасные для доступа любого пользователя к любой странице ASPX на сайте SharePoint.<br /><br /> Можно включить только один элемент **SafeControls** .|

### <a name="parent-elements"></a>Родительские элементы
 Нет.

## <a name="element-information"></a>Сведения об элементе

|Свойство|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
[Рсеференце схемы элемента проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
