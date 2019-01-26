---
title: CA1412. Пометьте интерфейсы ComSource как IDispatch
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 61a7042c4eae547a9da64503301351e96681f328
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013968"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412. Пометьте интерфейсы ComSource как IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Тип помечен атрибутом <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> атрибут и по крайней мере один указанного интерфейса не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибут `InterfaceIsDispatch` значение.

## <a name="rule-description"></a>Описание правила

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> используется для определения интерфейсов событий, класс предоставляет клиентам компонента объекта модели (COM). Эти интерфейсы должны предоставляться как `InterfaceIsIDispatch` позволяет клиентам COM Visual Basic 6 получать уведомления о событиях. По умолчанию, если интерфейс не помечен атрибутом <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> атрибут, оно будет представлено как сдвоенный интерфейс.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, добавление или изменение <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> таким образом, чтобы его значение установлено для InterfaceIsIDispatch для всех интерфейсов, которые указываются с помощью <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В следующем примере показан класс, где один из интерфейсов нарушает правило.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Связанные правила

[CA1408: Не используйте AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>См. также

- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)