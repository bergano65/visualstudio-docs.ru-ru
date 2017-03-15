---
title: "В классе &quot;&lt;имя_класса&gt;&quot; должен объявляться метод Sub New, поскольку &quot;&lt;имя_конструктора&gt;&quot; в базовом классе &quot;&lt;имя_базового_класса&gt;&quot; помечен как устаревший: &quot;&lt;сообщение_об_ошибке&gt;&quot; | Microsoft Docs"
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
  - "vbc41002"
  - "bc41002"
helpviewer_keywords: 
  - "BC41002"
ms.assetid: 6d034bbe-ab6a-433a-ae31-8c4a42faf7f8
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# В классе &quot;&lt;имя_класса&gt;&quot; должен объявляться метод Sub New, поскольку &quot;&lt;имя_конструктора&gt;&quot; в базовом классе &quot;&lt;имя_базового_класса&gt;&quot; помечен как устаревший: &quot;&lt;сообщение_об_ошибке&gt;&quot;
Объявление класса не включает конструктор, а конструктор базового класса помечен атрибутом <xref:System.ObsoleteAttribute> и содержит директиву, предписывающую расценивать это как предупреждение.  
  
 Когда производный класс не объявляет конструктор, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] пытается создать неявный конструктор без параметров, который вызывает `MyBase.New()`. Если в базовом классе нет доступного конструктора, который можно вызывать без аргументов, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не удается создать неявный конструктор. В этом случае необходимый конструктор помечается атрибутом <xref:System.ObsoleteAttribute>, и поэтому [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может вызвать его.  
  
 Вы можете пометить любой программный элемент как неиспользуемый, применив к нему <xref:System.ObsoleteAttribute>. В этом случае можно задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`. При задании значения `True` компилятор будет рассматривать попытку использовать элемент как ошибку. Если задать значение `False` или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.  
  
 По умолчанию это сообщение считается предупреждением, так как свойство <xref:System.ObsoleteAttribute.IsError%2A><xref:System.ObsoleteAttribute> имеет значение `False`. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC41002  
  
### Исправление ошибки  
  
1.  Проверьте указанное сообщение об ошибке и предпримите соответствующее действие.  
  
2.  Используйте `Sub New` для объявления конструктора в производном классе.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)