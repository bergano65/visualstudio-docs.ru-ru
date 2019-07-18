---
title: CA2146. Типы должны быть по крайней мере настолько критичными, как их базовые типы и интерфейсы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d1a0120caf16fbed34fa87ab71fe50abc4467d51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142661"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146. Типы должны быть по крайней мере настолько же критическими, как их базовые типы и интерфейсы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный тип является производным от типа, который помечен атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> или <xref:System.Security.SecurityCriticalAttribute>, или тип, отмеченный атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> атрибут является производным от типа, который помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> атрибута.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает, если у производного типа есть атрибут прозрачности безопасности, не такой критический, как базовый тип или реализованный интерфейс. От критических базовых типов или реализованных критических интерфейсов могут производиться только критические типы, и от критических в плане безопасности базовых типов или реализованных интерфейсов могут производиться только критические в плане безопасности типы. Нарушение этого правила в прозрачность уровня 2 привести <xref:System.TypeLoadException> для производного типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, пометьте тип производного или реализации атрибутом транспарентности, по крайней мере настолько критичными, как базовый тип или интерфейс.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]
