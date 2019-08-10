---
title: CA2111. Указатели не должны быть видимыми
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 416e45337dafd11a00e98b9adda9f16b02139f9c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921656"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111. Указатели не должны быть видимыми

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Открытый или защищенный <xref:System.IntPtr?displayProperty=fullName> объект <xref:System.UIntPtr?displayProperty=fullName> или поле не предназначено только для чтения.

## <a name="rule-description"></a>Описание правила
 <xref:System.IntPtr>и <xref:System.UIntPtr> являются типами указателей, которые используются для доступа к неуправляемой памяти. Если указатель не является частным, внутренним или предназначенным только для чтения, вредоносный код может изменить значение указателя, потенциально допуская доступ к произвольным расположениям в памяти или вызвать сбои приложения или системы.

Если вы планируете защитить доступ к типу, содержащему поле указателя, см. [раздел CA2112: Защищенные типы не должны предоставлять](../code-quality/ca2112-secured-types-should-not-expose-fields.md)поля.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Защитите указатель, сделав его предназначенным только для чтения, внутренним или частным.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Подавлять предупреждение из этого правила, если не полагаться на значение указателя.

## <a name="example"></a>Пример
В следующем коде показаны указатели, которые нарушают и удовлетворяют правилу. Обратите внимание, что нечастные указатели также нарушают [правило CA1051: Не объявляйте видимые поля](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)экземпляров.

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Связанные правила
[CA2112: Защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051 Не объявляйте видимые поля экземпляров](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>См. также

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>