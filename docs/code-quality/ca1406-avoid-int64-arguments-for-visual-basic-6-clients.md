---
title: CA1406. Не используйте аргументы Int64 для клиентов Visual Basic 6
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4dfcc612e931756b0e3d817556c9b37844bc3cfd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922037"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406. Не используйте аргументы Int64 для клиентов Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Тип, который специально помечен как видимый для модели COM, объявляет член, принимающий <xref:System.Int64?displayProperty=fullName> аргумент.

## <a name="rule-description"></a>Описание правила
Клиенты COM Visual Basic 6 не может получить доступ к 64-разрядных целых чисел.

По умолчанию следующие элементы видимы для COM: сборки, открытые типы, члены открытых экземпляров в открытых типах и все члены открытых типов значений. Однако для сокращения числа ложных срабатываний это правило требует явного определения видимости типа COM. включающая сборка должна быть помечена <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> `false` значением, а тип <xref:System.Runtime.InteropServices.ComVisibleAttribute> должен быть `true`помечен значением.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила для параметра, значение которого всегда может быть выражено в виде 32-разрядного целого числа, измените тип параметра <xref:System.Int32?displayProperty=fullName>на. Если значение параметра может быть больше, чем может быть выражено в виде 32-разрядного целого числа, измените тип параметра <xref:System.Decimal?displayProperty=fullName>на. Обратите внимание <xref:System.Single?displayProperty=fullName> , <xref:System.Double?displayProperty=fullName> что и, и теряют точность в верхних диапазонах <xref:System.Int64> типа данных. Если элемент не должен быть видимым для com, пометьте его <xref:System.Runtime.InteropServices.ComVisibleAttribute> `false`значением.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Предупреждение из этого правила можно отключить, если известно, что Visual Basic 6 клиентов COM не будет обращаться к типу.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий правило.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA1413 Избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407 Избегайте статических членов в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017 Пометка сборок с помощью ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также

- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
- [Тип данных Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)