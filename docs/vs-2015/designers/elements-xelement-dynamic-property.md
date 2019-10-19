---
title: Elements (динамическое свойство XElement) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 383101679827f19b9a85d36f0f5a39eb772c68ec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664692"
---
# <a name="elements-xelement-dynamic-property"></a>Elements (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Получает индексатор, который используется для извлечения дочернего элемента текущего элемента с заданным развернутым именем.

## <a name="syntax"></a>Синтаксис

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение
 Индексатор типа `IEnumerable<XElement> Item(String expandedName)`. Индексатор принимает развернутое имя нужных дочерних элементов и возвращает соответствующие дочерние элементы в коллекцию <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Заметки
 Это свойство эквивалентно методу <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> класса <xref:System.Xml.Linq.XContainer>.

 Элементы в возвращаемой коллекции располагаются в порядке исходного XML-документа.

 В данном свойстве используется отложенное выполнение.

## <a name="see-also"></a>См. также раздел
 [Потомки](../designers/descendants-xelement-dynamic-property.md) [элементов](../designers/element-xelement-dynamic-property.md) [динамических свойств класса XElement](../designers/xelement-class-dynamic-properties.md)
