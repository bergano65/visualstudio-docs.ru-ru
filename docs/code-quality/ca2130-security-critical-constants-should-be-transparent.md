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
ms.openlocfilehash: 62cf9b6b62dac85251d9fca434b35f0a7c6254c7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232423"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130. Важные константы безопасности должны быть прозрачными

|||
|-|-|
|TypeName|константсшаулдбетранспарент|
|CheckId|CA2130|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Константное поле или член перечисления помечается атрибутом <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Описание правила
Принудительная прозрачность не применяется для постоянных значений, чтобы во время выполнения не требовалась подстановка значений. Константные поля должны быть прозрачными для системы безопасности, чтобы анализаторы кода не предполагали, что прозрачный для системы безопасности код не может получить доступ к константе.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, удалите атрибут SecurityCritical из поля или значения.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующих примерах это предупреждение вызывается `EnumWithCriticalValues.CriticalEnumValue` значением перечисления и `CriticalConstant` константой. Чтобы устранить проблемы, удалите атрибут [`SecurityCritical`], чтобы сделать их прозрачными для безопасности.

[!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]