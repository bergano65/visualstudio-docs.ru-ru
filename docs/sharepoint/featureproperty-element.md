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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8e6010ac45d0b760325c73c4bd754fbb0b422a77
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672760"
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
|**Key**|Обязательный атрибут **xs: String** .<br /><br /> Ключ, используемый для хранения и извлечения значения свойства. У каждого свойства должен быть ключ, уникальный в пределах функции.|
|**Значение**|Обязательный атрибут **xs: String** .<br /><br /> Значение свойства.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Представляет коллекцию значений свойств, включенных в компонент при развертывании в SharePoint.|

## <a name="remarks"></a>Комментарии
 Дополнительные сведения о свойствах компонентов см. [в разделе Предоставление сведений о пакете и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Сведения об элементе

|Свойство.|Значение|
|-|-|
|**Пространство имен**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/Шарепоинттулс/Шарепоинтпрожектитеммодел|
|**Имя схемы**|Схема элемента проекта SharePoint|
|**Файл проверки**|Прожектитеммоделсчема. xsd|
|**Может быть пустым**|Нет|

## <a name="see-also"></a>См. также раздел
- [Справочник по схеме элементов проекта SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
