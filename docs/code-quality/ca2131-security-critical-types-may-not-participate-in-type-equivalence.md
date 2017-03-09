---
title: "CA2131: типы критической безопасности могут не участвовать в эквивалентности типа | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2131"
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2131: типы критической безопасности могут не участвовать в эквивалентности типа
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Тип участвует в эквивалентности типов и либо сам тип, либо его элемент или поле помечается атрибутом <xref:System.Security.SecurityCriticalAttribute>.  
  
## Описание правила  
 Это правило применяется ко всем критическим типам или к типам, содержащим критические методы или поля, участвующие в эквивалентности типов.  Когда среда CLR обнаруживает такой тип, происходит сбой загрузки с <xref:System.TypeLoadException> во время выполнения.  Обычно это правило срабатывает, только если пользователи реализуют эквивалентность типов вручную вместо того, чтобы позволить tlbimp и компиляторам обработать эквивалентность типов.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите атрибут SecurityCritical.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующих примерах демонстрируются интерфейс, метод и поле, вызывающие срабатывание этого правила.  
  
 [!code-cs[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## См. также  
 [Security\-Transparent Code, Level 2](../Topic/Security-Transparent%20Code,%20Level%202.md)