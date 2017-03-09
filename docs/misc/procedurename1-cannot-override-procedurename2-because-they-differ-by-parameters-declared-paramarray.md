---
title: "&quot;&lt;имя_процедуры1&gt;&quot; не может переопределить &quot;&lt;имя_процедуры2&gt;&quot;, поскольку они отличаются параметрами, объявленными как ParamArray | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30906"
  - "vbc30906"
helpviewer_keywords: 
  - "BC30906"
ms.assetid: 12939030-732e-4c6d-8fe9-707b7532174b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;имя_процедуры1&gt;&quot; не может переопределить &quot;&lt;имя_процедуры2&gt;&quot;, поскольку они отличаются параметрами, объявленными как ParamArray
Процедура в производном классе переопределяет одноименную процедуру \(с другим списком параметров\) в базовом классе.  
  
 Чтобы переопределить процедуру в наследуемом классе, у переопределяющей процедуры и этого класса должны совпадать списки параметров, уровни доступа и типы возвращаемых значений \(если таковые имеются\). В частности, должны соответствовать любые объявления [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) или [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray).  
  
 **Идентификатор ошибки:** BC30906  
  
### Исправление ошибки  
  
-   Если требуется переопределить процедуру, используйте список параметров, в точности соответствующий списку параметров в процедуре базового класса. Если последний параметр в процедуре базового класса объявлен как `ParamArray`, объявите его как `ParamArray` в переопределяющей процедуре.  
  
-   Если необходимо использовать список параметров, отличающийся от версии базового класса, такую процедуру нельзя переопределить. Вместо этого рассмотрите возможность перегрузки. Дополнительные сведения см. в разделе [Перегрузка процедур](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading).  
  
## См. также  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [НЕ В СБОРКЕ. переопределение свойств и методов](http://msdn.microsoft.com/ru-ru/2167e8f5-1225-4b13-9ebd-02591ba90213)