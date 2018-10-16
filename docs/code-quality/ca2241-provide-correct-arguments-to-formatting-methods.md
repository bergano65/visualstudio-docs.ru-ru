---
title: 'CA2241: предоставьте правильные аргументы методам форматирования'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6ef5b2f3b7244762e69d87882cbf2caae63cb34b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547884"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: предоставьте правильные аргументы методам форматирования

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 `format` Строку аргумент, переданный методу, такие как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, или <xref:System.String.Format%2A?displayProperty=fullName> не содержит элемент форматирования, соответствующий каждому аргументу объекта, или наоборот.

## <a name="rule-description"></a>Описание правила
 Аргументы для методов, таких как <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, и <xref:System.String.Format%2A> состоят из строк формата, следуют несколько <xref:System.Object?displayProperty=fullName> экземпляров. Строка формата состоит из текста и внедренного форматирование элементов в формате {индекс [, выравнивание] [: formatString]}. 'index' — это отсчитываемое от нуля целое число, которое указывает форматируемый объект. Если объект не имеет соответствующий индекс в строке формата, объект учитывается. Если объект, указанный «index» не существует, <xref:System.FormatException?displayProperty=fullName> возникает исключение во время выполнения.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, предоставляет элемента формата для каждого объекта-аргумента и аргумент объекта для каждого элемента форматирования.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Следующий пример показывает два нарушения данного правила.

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]