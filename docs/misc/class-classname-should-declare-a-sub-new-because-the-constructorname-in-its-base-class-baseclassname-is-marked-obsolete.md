---
title: "Класс &quot;&lt;имя_класса&gt;&quot; должен объявлять Sub New, поскольку конструктор &quot;&lt;имя_конструктора&gt;&quot; в его базовом классе &quot;&lt;имя_базового_класса&gt;&quot; помечен как устаревший. | Microsoft Docs"
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
  - "bc41001"
  - "vbc41001"
helpviewer_keywords: 
  - "BC41001"
ms.assetid: b2c6b996-6d52-4963-9fee-8b6f78fc028c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Класс &quot;&lt;имя_класса&gt;&quot; должен объявлять Sub New, поскольку конструктор &quot;&lt;имя_конструктора&gt;&quot; в его базовом классе &quot;&lt;имя_базового_класса&gt;&quot; помечен как устаревший.
Объявление класса не включает конструктор, а конструктор базового класса помечен атрибутом <xref:System.ObsoleteAttribute> и содержит директиву, предписывающую расценивать это как предупреждение.  
  
 Когда производный класс не объявляет конструктор, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] пытается создать неявный конструктор без параметров, который вызывает `MyBase.New()`. Если в базовом классе нет доступного конструктора, который можно вызывать без аргументов, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не удается создать неявный конструктор. В этом случае необходимый конструктор помечается атрибутом <xref:System.ObsoleteAttribute>, и поэтому [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может вызвать его.  
  
 Вы можете пометить любой программный элемент как неиспользуемый, применив к нему <xref:System.ObsoleteAttribute>. Если вы это сделаете, вы можете задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`. Если задать значение `True`, компилятор будет рассматривать попытку использовать элемент как ошибку. Если задать значение `False` или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.  
  
 По умолчанию это сообщение считается предупреждением, так как свойство <xref:System.ObsoleteAttribute.IsError%2A><xref:System.ObsoleteAttribute> имеет значение `False`. Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC41001  
  
### Исправление ошибки  
  
1.  Используйте `Sub New` для объявления конструктора в производном классе.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)