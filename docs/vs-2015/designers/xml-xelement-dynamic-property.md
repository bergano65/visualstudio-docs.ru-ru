---
title: Xml (динамическое свойство XElement) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663848"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Возвращает неформатированное XML-содержимое элемента.

## <a name="syntax"></a>Синтаксис

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение
 Значение <xref:System.String>, представляющее неформатированное XML-содержимое элемента.

## <a name="remarks"></a>Примечания
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> класса <xref:System.Xml.Linq.XNode?displayProperty=fullName> с параметром `SaveOptions`, установленным равным <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>См. также
 [Значение](../designers/value-xelement-dynamic-property.md) [динамических свойств класса XElement](../designers/xelement-class-dynamic-properties.md)
