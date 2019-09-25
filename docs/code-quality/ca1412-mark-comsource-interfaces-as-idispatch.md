---
title: CA1412. Пометьте интерфейсы ComSource как IDispatch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: caaae787d5e4801f3fc3b8d881b386595fb2eca4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234689"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412. Пометьте интерфейсы ComSource как IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Тип помечен <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> атрибутом, и по крайней мере один указанный интерфейс не помечен <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибутом, для `InterfaceIsDispatch` которого задано значение.

## <a name="rule-description"></a>Описание правила

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>используется для обнаружения интерфейсов событий, предоставляемых классом клиентам модели COM. Эти интерфейсы должны быть предоставлены `InterfaceIsIDispatch` как, чтобы разрешить Visual Basic 6 клиентов COM получать уведомления о событиях. По умолчанию, если интерфейс не помечен <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибутом, он предоставляется как сдвоенный интерфейс.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, добавьте или измените <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибут таким образом, чтобы его значение было равно InterfaceIsIDispatch для всех интерфейсов, указанных <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> с помощью атрибута.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В следующем примере показан класс, в котором один из интерфейсов нарушает правило.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Связанные правила

[CA1408 Не использовать двойное ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>См. также

- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)