---
title: CA2140. Прозрачный код не должен ссылаться на критические для безопасности элементы
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4f02938aed7456762f1ef51da716b6b96bdf437
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232152"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140. Прозрачный код не должен ссылаться на критические для безопасности элементы

|||
|-|-|
|TypeName|транспарентмесодсмустнотреференцекритикалкоде|
|CheckId|CA2140|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Прозрачный метод:

- обрабатывает критически важный для безопасности тип исключения безопасности

- имеет параметр, помеченный как тип, критический для безопасности

- имеет универсальный параметр с ограниченными критическими ограничениями безопасности

- имеет локальную переменную с критическим типом безопасности

- ссылается на тип, помеченный как критически важный для безопасности

- вызывает метод, помеченный как критически важный для безопасности

- ссылается на поле, помеченное как критическое для безопасности

- Возвращает тип, помеченный как критический с точки зрения безопасности

## <a name="rule-description"></a>Описание правила

Элемент кода, помеченный <xref:System.Security.SecurityCriticalAttribute> атрибутом, является критически важным для безопасности. Прозрачный метод не может использовать элемент, критический с точки зрения безопасности. Если прозрачный тип пытается использовать критически важный для безопасности тип <xref:System.TypeAccessException>, <xref:System.MethodAccessException> вызывается исключение <xref:System.FieldAccessException> , или.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, выполните одно из следующих действий.

- Пометьте элемент кода, использующий критически важный для безопасности <xref:System.Security.SecurityCriticalAttribute> код с помощью атрибута

     \- или -

- Удалите атрибут из элементов кода, помеченных как критически важный для безопасности, а затем пометьте их <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом или <xref:System.Security.SecurityTransparentAttribute>. <xref:System.Security.SecurityCriticalAttribute>

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В следующих примерах прозрачный метод пытается сослаться на общую коллекцию с критической безопасностью, поле критическое для безопасности и метод критической безопасности.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>