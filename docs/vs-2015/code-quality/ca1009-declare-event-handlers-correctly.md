---
title: 'CA1009: правильно объявите обработчики событий | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a4a4e2e6990772b50568043c4d18ff29248571d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547892"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009. Правильно объявляйте обработчики событий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Делегат, обрабатывающий открытое или защищенное событие, не имеет правильной сигнатуры, возвращаемого типа или имен параметров.

## <a name="rule-description"></a>Описание правила
 Методы обработчиков событий принимают два параметра. Первый имеет тип <xref:System.Object?displayProperty=fullName> и имеет имя sender. Это объект, вызвавший событие. Второй параметр имеет тип <xref:System.EventArgs?displayProperty=fullName> и имеет имя "e". Это данные, связанные с событием. Например, если событие возникает при открытии файла, то данные события обычно содержат имя файла.

 Методы обработчиков событий не должны возвращать значение. На языке программирования C# это определяется типом возвращаемого значения `void` . Обработчик событий может вызывать несколько методов в нескольких объектах. Если методам было разрешено возвращать значение, для каждого события будет происходить несколько возвращаемых значений, и будет доступно только значение последнего вызванного метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, исправьте сигнатуру, возвращаемый тип или имена параметров делегата. Дополнительные сведения см. в следующем примере.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан делегат, подходящий для обработки событий. Методы, которые могут вызываться этим обработчиком событий, соответствуют сигнатуре, указанной в руководствах по проектированию. `AlarmEventHandler`имя типа делегата. `AlarmEventArgs`является производным от базового класса для данных события, <xref:System.EventArgs> и содержит данные события будильника.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2109. Проверьте видимые обработчики событий](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>См. также
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: события и делегаты](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
