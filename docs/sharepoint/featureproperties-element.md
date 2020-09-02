---
title: Элемент FeatureProperties | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6860a91067daa6da1d4223ae5060385087ad3433
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967335"
---
# <a name="featureproperties-element"></a>FeatureProperties - элемент
  Коллекция значений свойств, включенных в компонент при развертывании в SharePoint. После развертывания компонента можно получить доступ к значениям свойств в коде.

## <a name="syntax"></a>Синтаксис

```xml
<FeatureProperties>
  <FeatureProperty.../>
</FeatureProperties>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[феатурепроперти](../sharepoint/featureproperty-element.md)|Необязательный элемент.<br /><br /> Представляет пользовательское свойство в формате "ключ — значение".|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Представляет элемент проекта SharePoint. Этот элемент является обязательным корневым элементом `.spdata` файла.|

## <a name="remarks"></a>Remarks
 Дополнительные сведения о свойствах компонентов см. [в разделе Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Сведения об элементе

|Элемент|Описание|
|-------------|-----------------|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
