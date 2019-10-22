---
title: Descendants (динамическое свойство XElement) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b0496a04219c88573b3b555ef879a046d90faa3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664785"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Возвращает индексатор, который используется для получения всех элементов-потомков текущего элемента, соответствующих заданному развернутому имени.

## <a name="syntax"></a>Синтаксис

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение
 Индексатор типа `IEnumerable<XElement> Item(String expandedName)`. Этот индексатор принимает развернутое имя указанных элементов-потомков и возвращает соответствующие дочерние элементы в коллекции <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Заметки
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> класса <xref:System.Xml.Linq.XContainer>.

 Элементы в возвращаемой коллекции располагаются в порядке исходного XML-документа.

 В данном свойстве используется отложенное выполнение.

## <a name="see-also"></a>См. также раздел
 [Элементы](../designers/elements-xelement-dynamic-property.md) [динамических свойств класса XElement](../designers/xelement-class-dynamic-properties.md)
