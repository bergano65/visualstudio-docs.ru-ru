---
title: Value (динамическое свойство XAttribute) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664052"
---
# <a name="value-xattribute-dynamic-property"></a>Value (динамическое свойство XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Получает или устанавливает значение атрибута XML.

## <a name="syntax"></a>Синтаксис

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение
 Объект типа <xref:System.String>, содержащий значение этого атрибута.

## <a name="exceptions"></a>Исключения

|Тип исключения|Условие|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|При настройке значение параметра `value` - `null`.|

## <a name="remarks"></a>Remarks
 Это свойство эквивалентно свойству <xref:System.Xml.Linq.XAttribute.Value%2A> класса <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, однако это динамическое свойство также поддерживает уведомление об изменениях.

## <a name="see-also"></a>См. также:
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>[Атрибут](../designers/attribute-xelement-dynamic-property.md) [динамических свойств класса XAttribute](../designers/xattribute-class-dynamic-properties.md)
