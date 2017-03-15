---
title: "Первый оператор Sub New должен быть явным вызовом в MyBase.New или MyClass.New, так как &quot;&lt;имя_конструктора&gt;&quot; в базовом классе &quot;&lt;имя_базового_класса&gt;&quot; в &quot;&lt;имя_производного_класса&gt;&quot; отмечен как устаревший. | Microsoft Docs"
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
  - "bc41003"
  - "vbc41003"
helpviewer_keywords: 
  - "BC41003"
ms.assetid: 6d7c84db-659f-4388-85cf-38208ad607c3
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Первый оператор Sub New должен быть явным вызовом в MyBase.New или MyClass.New, так как &quot;&lt;имя_конструктора&gt;&quot; в базовом классе &quot;&lt;имя_базового_класса&gt;&quot; в &quot;&lt;имя_производного_класса&gt;&quot; отмечен как устаревший.
Конструктор класса не вызывает явно конструктор базового класса, а вызванный неявно конструктор базового класса помечается атрибутом <xref:System.ObsoleteAttribute>, что является причиной возникновения предупреждения.  
  
 Если конструктор производного класса не вызывает конструктор базового класса, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] пытается создать неявный вызов конструктора базового класса без параметров. Если в базовом классе нет доступного конструктора, который можно вызывать без аргументов, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не удается создать неявный вызов. В этом случае необходимый конструктор помечается атрибутом <xref:System.ObsoleteAttribute>, и поэтому [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не может вызвать его.  
  
 Вы можете пометить любой программный элемент как неиспользуемый, применив к нему <xref:System.ObsoleteAttribute>. В этом случае можно задать для свойства <xref:System.ObsoleteAttribute.IsError%2A> атрибута значение `True` или `False`. При задании значения `True` компилятор будет рассматривать попытку использовать элемент как ошибку. Если задать значение `False` или оставить значение по умолчанию `False`, то при попытке использовать элемент компилятор выдаст предупреждение.  
  
 По умолчанию это сообщение считается предупреждением, так как свойство <xref:System.ObsoleteAttribute.IsError%2A><xref:System.ObsoleteAttribute> имеет значение `False`. Сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Настройка предупреждений в Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Идентификатор ошибки:** BC41003  
  
### Исправление ошибки  
  
-   Сделайте вызов `MyBase.New()` или `MyClass.New()` первым оператором `Sub New` в производном классе.  
  
## См. также  
 [НЕ В СБОРКЕ. Атрибуты, используемые в Visual Basic](http://msdn.microsoft.com/ru-ru/22231318-8a40-49af-9245-e0aab723563b)   
 [НЕ В СБОРКЕ. Применение атрибутов](http://msdn.microsoft.com/ru-ru/2b1703ed-4437-49b3-bc0b-568094324f47)