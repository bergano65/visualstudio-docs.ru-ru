---
title: "Непредвиденная круглая скобка &quot;(&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32095"
  - "bc32095"
helpviewer_keywords: 
  - "BC32095"
ms.assetid: a47ad15a-2cfc-4d17-9012-27ba85b7d783
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Непредвиденная круглая скобка &quot;(&quot;
Непредвиденная круглая скобка "\(". Массивы абстрактных универсальных типов недопустимы.  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не удается скомпилировать массив, если он не имеет определенный тип данных. Нельзя использовать параметр типа данных универсального типа в качестве типа данных массива.  
  
 **Идентификатор ошибки:** BC32095  
  
### Исправление ошибки  
  
-   Ели требуется использовать массив, его необходимо объявить как имеющий определенный тип данных. Нельзя использовать параметр типа данных.  
  
-   Если необходимо, чтобы группа элементов имела тип данных, соответствующий параметру типа данных, следует использовать коллекцию вместо массива.  
  
## См. также  
 [Универсальные типы в Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NIB Коллекции в Visual Basic](http://msdn.microsoft.com/ru-ru/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)   
 [Управление группами объектов в Visual Basic](http://msdn.microsoft.com/ru-ru/50be4910-4732-4d5f-a18a-055a162e9037)