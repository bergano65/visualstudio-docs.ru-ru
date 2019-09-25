---
title: CA1009. Правильно объявляйте обработчики событий
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e923730213ca31a4429d8547fdaaf980692f9a96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236478"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009. Правильно объявляйте обработчики событий

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Делегат, обрабатывающий открытое или защищенное событие, не имеет правильной сигнатуры, возвращаемого типа или имен параметров.

## <a name="rule-description"></a>Описание правила
Методы обработчиков событий принимают два параметра. Первый имеет тип <xref:System.Object?displayProperty=fullName> и имеет имя sender. Это объект, вызвавший событие. Второй параметр имеет тип <xref:System.EventArgs?displayProperty=fullName> и имеет имя "e". Это данные, связанные с событием. Например, если событие возникает при открытии файла, то данные события обычно содержат имя файла.

Методы обработчиков событий не должны возвращать значение. На языке C# программирования это определяется типом `void`возвращаемого значения. Обработчик событий может вызывать несколько методов в нескольких объектах. Если методам было разрешено возвращать значение, для каждого события будет происходить несколько возвращаемых значений, и будет доступно только значение последнего вызванного метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, исправьте сигнатуру, возвращаемый тип или имена параметров делегата. Дополнительные сведения см. в следующем примере.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показан делегат, подходящий для обработки событий. Методы, которые могут вызываться этим обработчиком событий, соответствуют сигнатуре, указанной в руководствах по проектированию. `AlarmEventHandler`имя типа делегата. `AlarmEventArgs`является производным от базового класса для данных события, <xref:System.EventArgs>и содержит данные события будильника.

[!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
[!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
[!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA2109: Просмотр видимых обработчиков событий](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>См. также

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [Обработка и вызов событий](/dotnet/standard/events/index)