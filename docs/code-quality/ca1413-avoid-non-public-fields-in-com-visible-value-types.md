---
title: CA1413. Не используйте неоткрытые поля в типах значений, видимых для COM
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0d4fed5b16120ec069eaa4101670c88ad8f3a247
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234651"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413. Не используйте неоткрытые поля в типах значений, видимых для COM

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Тип значения, специально помеченный как видимый для модели COM, объявляет Неоткрытое поле экземпляра.

## <a name="rule-description"></a>Описание правила
Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM-клиентов. Проверьте содержимое поля на предмет сведений, которые не должны быть предоставлены или которые будут иметь непреднамеренное Оформление или последствия безопасности.

По умолчанию все открытые типы значений видимы для модели COM. Однако для сокращения числа ложных срабатываний это правило требует явного определения видимости типа COM. Включающая сборка должна быть помечена <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> `false` значением, а тип <xref:System.Runtime.InteropServices.ComVisibleAttribute> должен быть `true`помечен значением.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила и сделать поле скрытым, измените тип значения на ссылочный тип или удалите <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут из типа.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Можно отключить вывод предупреждения из этого правила, если доступность поля является общедоступной.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий правило.

[!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
[!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA1407 Избегайте статических членов в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017 Пометка сборок с помощью ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также

- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
- [Oпределение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)