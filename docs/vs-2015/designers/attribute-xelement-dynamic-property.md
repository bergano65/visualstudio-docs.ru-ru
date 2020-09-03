---
title: Attribute (динамическое свойство XElement) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 551e072b05e7a88ff9624c5d16e4aa199a6afd66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657978"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Возвращает индексатор, используемый для получения экземпляра атрибута, соответствующего указанному развернутому имени.

## <a name="syntax"></a>Синтаксис

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение
 Индексатор типа `XAttribute Item(String expandedName)`. Данный индексатор принимает развернутое имя указанного атрибута и возвращает соответствующий <xref:System.Xml.Linq.XAttribute> или значение `null`, если не существует атрибута с указанным именем.

## <a name="remarks"></a>Remarks
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XElement.Attribute%2A> класса <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>См. также:
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>[Значение](../designers/value-xattribute-dynamic-property.md) [динамических свойств класса XElement](../designers/xelement-class-dynamic-properties.md)
