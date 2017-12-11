---
title: "Attribute (динамическое свойство XElement) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0fd01945c2a33f3929f59e66a02a1d08a39c3cc7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [XElement Class Dynamic Properties](../designers/xelement-class-dynamic-properties.md)  (Динамические свойства класса XElement)  
 [Значение](../designers/value-xattribute-dynamic-property.md)