---
title: Attribute (динамическое свойство XElement) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ced05b8da63f9a7a242b166fe64e9e44f78b8065
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162679"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (динамическое свойство XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)  (Динамические свойства класса XElement)  
 [Значение](../designers/value-xattribute-dynamic-property.md)
