---
title: "CA1823: избегайте наличия неиспользованных закрытых полей | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
helpviewer_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1823: избегайте наличия неиспользованных закрытых полей
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Это правило сообщает об ошибке, если в коде существует закрытое поле, которое не используется.  
  
## Описание правила  
 Обнаружены закрытые поля, доступ к которым, судя по всему, не предоставляется в сборке.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, удалите поле или добавьте код, который будет его использовать.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении этого правила является безопасным.  
  
## Связанные правила  
 [CA1812: не создавайте внутренние классы без экземпляров](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801: проверьте неиспользуемые параметры](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)