---
title: "Первый оператор Sub New должен быть явным вызовом MyBase.New или MyClass.New, так как конструктор &quot;&lt;имя_конструктора&gt;&quot; в базовом классе &quot;&lt;имя_базового_класса&gt;&quot; в &quot;&lt;имя_производного_класса&gt;&quot; отмечен как устаревший. | Microsoft Docs"
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
  - "vbc30919"
  - "bc30919"
helpviewer_keywords: 
  - "BC30919"
ms.assetid: 437e3204-8ddc-45d3-b9b4-c66d53a61a6d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Первый оператор Sub New должен быть явным вызовом MyBase.New или MyClass.New, так как конструктор &quot;&lt;имя_конструктора&gt;&quot; в базовом классе &quot;&lt;имя_базового_класса&gt;&quot; в &quot;&lt;имя_производного_класса&gt;&quot; отмечен как устаревший.
Конструктор класса не вызывает явно конструктор базового класса, а вызванный неявно конструктор базового класса помечается атрибутом <xref:System.ObsoleteAttribute>, что является причиной возникновения ошибки.  
  
 Если конструктор производного класса не вызывает конструктор базового класса, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] пытается создать неявный вызов конструктора базового класса без параметров. Если в базовом классе нет доступного конструктора, который можно вызывать без аргументов, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не удается создать неявный вызов. В этом случае необходимый конструктор помечается атрибутом <xref:System.ObsoleteAttribute>, и поэтому [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может вызвать его.  
  
 Вы можете пометить любой программный элемент как неиспользуемый, применив к нему атрибут <xref:System.ObsoleteAttribute>. Если вы это сделаете, вы можете задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`. Если задать значение `True`, компилятор будет рассматривать попытку использовать элемент как ошибку. Если задать значение `False` или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.  
  
 **Идентификатор ошибки:** BC30919  
  
### Исправление ошибки  
  
-   Включите вызов `MyBase.New()` или `MyClass.New()` в качестве первого оператора `Sub New` в производном классе.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)