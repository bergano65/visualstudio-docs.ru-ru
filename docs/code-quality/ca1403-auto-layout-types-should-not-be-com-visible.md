---
title: CA1403. Типы с автомакетом не должны быть видимыми для COM
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fa965caf63dad6e81e2aeabbc93e97c7aa4b7a80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546203"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403. Типы с автомакетом не должны быть видимыми для COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Тип значений, видимых объектов модели компонентов (COM) помечен с помощью <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> атрибут <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила

<xref:System.Runtime.InteropServices.LayoutKind> Типы макета управляет среда CLR. Макеты этих типов можно изменить в разных версиях .NET Framework, которая разбивает клиентов COM, которые ожидают определенного макета. Если <xref:System.Runtime.InteropServices.StructLayoutAttribute> укажите атрибут не указан, компиляторы C#, Visual Basic и C++ [LayoutKind.Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) для типов значений.

Если не указано иное, все общедоступный, не являющегося универсальным типы являются видимыми для COM, и все не являющиеся открытыми и универсальные типы невидимы для модели COM. Тем не менее чтобы сократить число ложных срабатываний, это правило требует видимость COM типа, чтобы задавать явно. Включающая сборка должны быть отмечены <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> присвоено `false` и тип должен быть помечен атрибутом <xref:System.Runtime.InteropServices.ComVisibleAttribute> присвоено `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените значение <xref:System.Runtime.InteropServices.StructLayoutAttribute> атрибут [LayoutKind.Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) или [LayoutKind.Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), или сделайте тип невидимым для COM.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В примере показан тип, который нарушает правило и тип, соответствующий этому правилу.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Связанные правила

[CA1408: Не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>См. также

- [Определения типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)