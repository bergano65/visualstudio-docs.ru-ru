---
title: CA2146. Типы должны быть по крайней мере настолько же критическими, как их базовые типы и интерфейсы
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a70e999505bd900a7b3d89693ef4f6a1cef9de7d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920422"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146. Типы должны быть по крайней мере настолько же критическими, как их базовые типы и интерфейсы

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Прозрачный тип является производным от типа, <xref:System.Security.SecuritySafeCriticalAttribute> помеченного как <xref:System.Security.SecurityCriticalAttribute>или, или тип, помеченный <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом, является производным <xref:System.Security.SecurityCriticalAttribute> от типа, помеченного атрибутом.

## <a name="rule-description"></a>Описание правила
Это правило срабатывает, если у производного типа есть атрибут прозрачности безопасности, не такой критический, как базовый тип или реализованный интерфейс. От критических базовых типов или реализованных критических интерфейсов могут производиться только критические типы, и от критических в плане безопасности базовых типов или реализованных интерфейсов могут производиться только критические в плане безопасности типы. Нарушения этого правила в прозрачности уровня 2 приводят к <xref:System.TypeLoadException> созданию производного типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить это нарушение, пометьте производный или реализующий тип атрибутом прозрачности, который не менее важен, чем базовый тип или интерфейс.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
[!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]