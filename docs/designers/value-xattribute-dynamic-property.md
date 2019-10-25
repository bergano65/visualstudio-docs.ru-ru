---
title: Value (динамическое свойство XAttribute)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fefa3d13f1a38b5d1c329fa9df9220e13e769b1c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634520"
---
# <a name="value-xattribute-dynamic-property"></a>Value (динамическое свойство XAttribute)

Получает или устанавливает значение атрибута XML.

## <a name="syntax"></a>Синтаксис

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Объект типа <xref:System.String>, содержащий значение этого атрибута.

## <a name="exceptions"></a>Исключения

|Тип исключения|Условие|
| - |---------------|
|<xref:System.ArgumentNullException>|При настройке значение параметра `value` - `null`.|

## <a name="remarks"></a>Примечания

Это свойство эквивалентно свойству <xref:System.Xml.Linq.XAttribute.Value%2A> класса <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, однако это динамическое свойство также поддерживает уведомление об изменениях.

## <a name="see-also"></a>См. также

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Динамические свойства класса XAttribute](../designers/value-xattribute-dynamic-property.md)
- [Attribute (XElement Dynamic Property)](../designers/attribute-xelement-dynamic-property.md) (Attribute (динамическое свойство XElement))