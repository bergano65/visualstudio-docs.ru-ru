---
title: "CA2146: типы должны быть по крайней мере настолько же критичны, как их базовые типы и интерфейсы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2146"
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2146: типы должны быть по крайней мере настолько же критичны, как их базовые типы и интерфейсы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Прозрачный тип производится от типа, помеченного атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> или <xref:System.Security.SecurityCriticalAttribute>, или тип, помеченный атрибутом <xref:System.Security.SecuritySafeCriticalAttribute>, производится от типа, помеченного атрибутом <xref:System.Security.SecurityCriticalAttribute>.  
  
## Описание правила  
 Это правило срабатывает, если у производного типа есть атрибут прозрачности безопасности, не такой критический, как базовый тип или реализованный интерфейс.  От критических базовых типов или реализованных критических интерфейсов могут производиться только критические типы, и от критических в плане безопасности базовых типов или реализованных интерфейсов могут производиться только критические в плане безопасности типы.  Нарушения этого правила на 2 уровне прозрачности приведут к возникновению исключения <xref:System.TypeLoadException> для производного типа.  
  
## Устранение нарушений  
 Чтобы устранить это нарушение, отметьте производный тип или тип реализации атрибутом прозрачности, критичность которого по крайней мере равна критичности базового типа или интерфейса.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 [!CODE [FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes#1)]