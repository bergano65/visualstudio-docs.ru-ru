---
title: 'CA1413: избегайте использования не открытых полей в видимых типах значений COM'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 170f4936258383cf26ed1d22fc78962b8b25e79c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: избегайте использования не открытых полей в видимых типах значений COM
|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип значения, который специально помечен как видимый для модели объектов компонентов (COM) объявляет поле закрытого экземпляра.

## <a name="rule-description"></a>Описание правила
 Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM-клиентов. Проверьте содержимое полей сведения, не следует делать видимыми, или которые могут оказать нежелательное воздействие на разработку или безопасность.

 По умолчанию все открытые типы значений являются видимыми для COM. Однако во избежание ложных положительных результатов, это правило требует видимость COM необходимо явно указать тип. Содержащей сборки должны быть отмечены <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> значение `false` и тип должен быть помечен атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> значение `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила и сохранить скрытые поля, измените тип значения в ссылочный тип или удалите <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут на основе типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если допустима раскрытию поля.

## <a name="example"></a>Пример
 В следующем примере показано тип, нарушающий правило.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1407: не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index) [уточнение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)