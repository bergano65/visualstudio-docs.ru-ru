---
title: "CA2123: запросы компоновки переопределения должны быть идентичны базовым | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
helpviewer_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2123: запросы компоновки переопределения должны быть идентичны базовым
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Открытый или защищенный метод в открытом типе переопределяет метод или реализует интерфейс и не имеет в качестве интерфейса или виртуального метода такого же [Link Demands](../Topic/Link%20Demands.md).  
  
## Описание правила  
 Это правило сравнивает метод с его базовым методом \(который является интерфейсом или виртуальным методом другого типа\), а затем сравнивает запросы ссылок для каждого из них.  Правило считается нарушенным, если у одного из двух элементов \(метода или базового метода\) есть запрос ссылок, а у другого нет.  
  
 Если это правило нарушается, то злонамеренный вызывающий объект может обойти запрос ссылок путем вызова небезопасного метода.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, примените то же требование ссылки к переопределению метода или реализации.  Если это невозможно, следует пометить метод полным требованием или полностью удалить атрибут.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показаны различные нарушения этого правила.  
  
 [!code-cs[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## См. также  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)