---
title: "Атрибут &quot;&lt;имя_атрибута&gt;&quot; не может использоваться для метода с необязательными параметрами | Microsoft Docs"
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
  - "vbc30645"
  - "bc30645"
helpviewer_keywords: 
  - "BC30645"
ms.assetid: 4de3d2c9-5588-47c2-a6b2-e165d16106b8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Атрибут &quot;&lt;имя_атрибута&gt;&quot; не может использоваться для метода с необязательными параметрами
Атрибут может использоваться только с методами, которые имеют обязательные аргументы или не имеют аргументов вообще.  
  
 **Идентификатор ошибки**: BC30645  
  
### Исправление ошибки  
  
1.  Определите метод без необязательных параметров.  
  
2.  Используйте атрибут, который может использоваться с методами, имеющими необязательные параметры.  
  
3.  Определите специальный атрибут, который может использоваться в этом контексте.  
  
## См. также  
 <xref:System.AttributeUsageAttribute>   
 [НЕ В СБОРКЕ. Атрибуты в Visual Basic](http://msdn.microsoft.com/ru-ru/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)