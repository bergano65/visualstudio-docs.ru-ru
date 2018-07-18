---
title: Attribute (динамическое свойство XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ac173785804ce2ed2874b9628c68d3ab78be6e1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923269"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (динамическое свойство XElement)

Возвращает индексатор, используемый для получения экземпляра атрибута, соответствующего указанному развернутому имени.

## <a name="syntax"></a>Синтаксис

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение

Индексатор типа `XAttribute Item(String expandedName)`. Данный индексатор принимает развернутое имя указанного атрибута и возвращает соответствующий <xref:System.Xml.Linq.XAttribute> или значение `null`, если не существует атрибута с указанным именем.

## <a name="remarks"></a>Примечания

Это свойство эквивалентно методу <xref:System.Xml.Linq.XElement.Attribute%2A> класса <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>См. также

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Динамические свойства класса XElement](../designers/xelement-class-dynamic-properties.md)
- [Значение](../designers/value-xattribute-dynamic-property.md)