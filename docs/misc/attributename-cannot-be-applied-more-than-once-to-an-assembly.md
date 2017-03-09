---
title: "&quot;&lt;имя_атрибута&gt;&quot; не может использоваться для сборки несколько раз | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31521"
  - "vbc31521"
helpviewer_keywords: 
  - "BC31521"
ms.assetid: 7312570f-8afb-4afe-992f-b6f7796f5f26
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_атрибута&gt;&quot; не может использоваться для сборки несколько раз
Указанный атрибут может применяться к атрибуту только один раз.  
  
 **Идентификатор ошибки:** BC31521  
  
### Исправление ошибки  
  
1.  Удалите лишние случаи применения этого атрибута.  
  
2.  Если вы используете самостоятельно разработанный атрибут, измените `AttributeUsageAttribute` и присвойте свойству `AllowMultiple` значение `True`.  
  
## См. также  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=fullName>