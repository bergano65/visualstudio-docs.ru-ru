---
title: "CA1501: избегайте излишнего наследования | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1501"
  - "AvoidExcessiveInheritance"
helpviewer_keywords: 
  - "AvoidExcessiveInheritance"
  - "CA1501"
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1501: избегайте излишнего наследования
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|Категория|Microsoft.Maintainability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Тип расположен глубже четырех уровней в иерархии наследования.  
  
## Описание правила  
 Глубокие иерархии вложенных типов трудно отслеживать, понимать и поддерживать.  Данное правило ограничивает анализ для иерархий в одном модуле.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте данный тип производным от базового типа, который располагается не так глубоко в иерархии наследования или удалите часть промежуточных базовых типов.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении этого правила является безопасным.  Тем не менее код может быть более сложным в обслуживании.  Обратите внимание, что в зависимости от видимости базовых типов устранение нарушений данного правила может привести к критическим изменениям.  Например, удаление открытых базовых типов является критическим изменением.  
  
## Пример  
 В следующем примере показан тип, который нарушает данное правило.  
  
 [!code-cs[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]