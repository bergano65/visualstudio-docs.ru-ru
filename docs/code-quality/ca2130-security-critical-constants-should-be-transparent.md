---
title: CA2130. Важные константы безопасности должны быть прозрачными
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbe1f5c58b957cf3ed226af7c7b879c7a6dcfc0a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970066"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130. Важные константы безопасности должны быть прозрачными

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Константного поля или член перечисления помечается <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Описание правила
 Принудительная прозрачность не применяется для постоянных значений, чтобы во время выполнения не требовалась подстановка значений. Константные поля должны быть прозрачными для системы безопасности, чтобы анализаторы кода не предполагали, что прозрачный для системы безопасности код не может получить доступ к константе.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите атрибут SecurityCritical из поля или значения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующих примерах значение перечисления `EnumWithCriticalValues.CriticalEnumValue` и константы `CriticalConstant` выдавал подобное предупреждение. Чтобы устранить проблемы, удалите [`SecurityCritical`] атрибут, чтобы сделать их безопасности прозрачным.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]