---
title: CA1406. Не используйте аргументы Int64 для клиентов Visual Basic 6
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6d39c98aae5ae577ad82f0ff99f1069fb34e5146
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920943"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406. Не используйте аргументы Int64 для клиентов Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип, который специально помечен как видимый для модели объектов компонента (COM) объявляет член, принимающую <xref:System.Int64?displayProperty=fullName> аргумент.

## <a name="rule-description"></a>Описание правила
 Клиенты COM Visual Basic 6 не может получить доступ к 64-разрядных целых чисел.

 По умолчанию следующие являются видимыми для COM: сборки, открытые типы, члены открытых экземпляров в открытых типов и все члены открытых типов значения. Тем не менее чтобы сократить число ложных срабатываний, это правило требует видимость COM типа, чтобы задавать явно; включающая сборка должны быть отмечены <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> присвоено `false` и тип должен быть помечен атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> присвоено `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила для параметра, значение которого всегда может быть выражен как 32-разрядного целого числа, измените тип параметра для <xref:System.Int32?displayProperty=fullName>. Если значение параметра может быть больше, чем может быть выражен как 32-разрядного целого числа, измените тип параметра для <xref:System.Decimal?displayProperty=fullName>. Обратите внимание, что оба <xref:System.Single?displayProperty=fullName> и <xref:System.Double?displayProperty=fullName> потеря точности в верхнем диапазоны <xref:System.Int64> тип данных. Если элемент не должен быть видим для COM, пометьте его с <xref:System.Runtime.InteropServices.ComVisibleAttribute> присвоено `false`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если известно, что клиенты COM Visual Basic 6 не затронет тип.

## <a name="example"></a>Пример
 В примере показан тип, который нарушает правило.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1413: Избегайте не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Пометьте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также

- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
- [Тип данных Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)