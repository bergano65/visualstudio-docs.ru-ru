---
title: 'CA2146: типы должны быть не менее критичны, чем их базовые типы и интерфейсы | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ab621ade120a257508eddbf9527f674b5fda8748
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610187"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: типы должны быть по крайней мере настолько же критичны, как их базовые типы и интерфейсы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|типесмустбеатлеастаскритикаласбасетипес|
|CheckId|CA2146|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный тип является производным от типа, помеченного <xref:System.Security.SecuritySafeCriticalAttribute> или <xref:System.Security.SecurityCriticalAttribute>, либо тип, помеченный атрибутом <xref:System.Security.SecuritySafeCriticalAttribute>, является производным от типа, помеченного атрибутом <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает, если у производного типа есть атрибут прозрачности безопасности, не такой критический, как базовый тип или реализованный интерфейс. От критических базовых типов или реализованных критических интерфейсов могут производиться только критические типы, и от критических в плане безопасности базовых типов или реализованных интерфейсов могут производиться только критические в плане безопасности типы. Нарушения этого правила в прозрачности уровня 2 приводят к <xref:System.TypeLoadException> производного типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, пометьте производный или реализующий тип атрибутом прозрачности, который не менее важен, чем базовый тип или интерфейс.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]
