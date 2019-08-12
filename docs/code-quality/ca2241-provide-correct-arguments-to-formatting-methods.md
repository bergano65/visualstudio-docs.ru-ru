---
title: CA2241. Задайте правильные аргументы для методов форматирования
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3bdb8ef315c9702cc10352368aba7202a8f29f7f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920006"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241. Задайте правильные аргументы для методов форматирования

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Строковый аргумент, передаваемый методу <xref:System.Console.WriteLine%2A>, например <xref:System.Console.Write%2A>, или <xref:System.String.Format%2A?displayProperty=fullName> , не содержит элемент форматирования, соответствующий аргументу объекта, или наоборот. `format`

## <a name="rule-description"></a>Описание правила
Аргументы для таких методов, как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, и <xref:System.String.Format%2A> состоят из строки форматирования, за которой следуют <xref:System.Object?displayProperty=fullName> несколько экземпляров. Строка формата состоит из текста и внедренных элементов форматирования в форме: {index [, Alignment] [: formatString]}. 'index' — это отсчитываемое от нуля целое число, которое указывает форматируемый объект. Если у объекта нет соответствующего индекса в строке формата, объект игнорируется. Если объект, указанный параметром "index", не существует, <xref:System.FormatException?displayProperty=fullName> во время выполнения создается исключение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, укажите элемент форматирования для каждого аргумента объекта и укажите аргумент объекта для каждого элемента форматирования.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показаны два нарушения правила.

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]