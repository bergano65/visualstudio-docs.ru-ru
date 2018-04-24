---
title: Value (динамическое свойство XAttribute)
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b98272fe2c86137eb925a54924e1b0e8411ed0e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="value-xattribute-dynamic-property"></a>Value (динамическое свойство XAttribute)

Получает или устанавливает значение атрибута XML.

## <a name="syntax"></a>Синтаксис

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Объект типа <xref:System.String>, содержащий значение этого атрибута.

## <a name="exceptions"></a>Исключения

|Тип исключения|Условие|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|При настройке значение параметра `value` - `null`.|

## <a name="remarks"></a>Примечания

Это свойство эквивалентно свойству <xref:System.Xml.Linq.XAttribute.Value%2A> класса <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, однако это динамическое свойство также поддерживает уведомление об изменениях.

## <a name="see-also"></a>См. также

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Динамические свойства класса XAttribute](../designers/xattribute-class-dynamic-properties.md)
- [Attribute (XElement Dynamic Property)](../designers/attribute-xelement-dynamic-property.md) (Attribute (динамическое свойство XElement))