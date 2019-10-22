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
ms.openlocfilehash: 261013ed844b6c5ba37c544c7745a77378c0c722
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668913"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: правильно объявите обработчики событий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Делегат, обрабатывающий открытое или защищенное событие, не имеет правильной сигнатуры, возвращаемого типа или имен параметров.

## <a name="rule-description"></a>Описание правила
 Методы обработчиков событий принимают два параметра. Первый имеет тип <xref:System.Object?displayProperty=fullName> и имеет имя sender. Это объект, вызвавший событие. Второй параметр имеет тип <xref:System.EventArgs?displayProperty=fullName> и имеет имя "e". Это данные, связанные с событием. Например, если событие возникает при открытии файла, то данные события обычно содержат имя файла.

 Методы обработчиков событий не должны возвращать значение. На языке C# программирования это определяется типом возвращаемого значения `void`. Обработчик событий может вызывать несколько методов в нескольких объектах. Если методам было разрешено возвращать значение, для каждого события будет происходить несколько возвращаемых значений, и будет доступно только значение последнего вызванного метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, исправьте сигнатуру, возвращаемый тип или имена параметров делегата. Дополнительные сведения см. в следующем примере.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан делегат, подходящий для обработки событий. Методы, которые могут вызываться этим обработчиком событий, соответствуют сигнатуре, указанной в руководствах по проектированию. `AlarmEventHandler` — имя типа делегата. `AlarmEventArgs` является производным от базового класса для данных события, <xref:System.EventArgs> и содержит данные события будильника.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA2109: проверьте видимые обработчики событий](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>См. также раздел
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: события и делегаты](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
