---
title: Элемент Феатурепроперти | Документация Майкрософт
description: Просмотр справочных сведений об элементе Феатурепроперти, который является элементом в схеме элемента проекта SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 070866b9dd14d974eb976b22bf7a79907e2c5d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876671"
---
# <a name="featureproperty-element"></a>FeatureProperty - элемент
  Представляет пользовательское свойство, которое входит в состав компонента при его развертывании в SharePoint. После развертывания компонента можно получить доступ к свойству в коде.

## <a name="syntax"></a>Синтаксис

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|**Ключ**|Обязательный атрибут **xs: String** .<br /><br /> Ключ, используемый для хранения и извлечения значения свойства. У каждого свойства должен быть ключ, уникальный в пределах функции.|
|**Значение**|Обязательный атрибут **xs: String** .<br /><br /> Значение свойства.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Представляет коллекцию значений свойств, включенных в компонент при развертывании в SharePoint.|

## <a name="remarks"></a>Remarks
 Дополнительные сведения о свойствах компонентов см. [в разделе Предоставление сведений о пакете и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Сведения об элементе

|Свойство|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
