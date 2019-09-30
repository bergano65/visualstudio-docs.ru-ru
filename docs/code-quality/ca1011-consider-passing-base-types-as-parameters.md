---
title: CA1011. Попробуйте передать базовые типы в качестве параметров
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dcb5937f58088684e7bfc204ab4143434b0684ae
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236398"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011. Попробуйте передать базовые типы в качестве параметров

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Объявление метода включает формальный параметр, который является производным типом, а метод вызывает только члены базового типа параметра.

## <a name="rule-description"></a>Описание правила

Если в объявлении метода в качестве параметра указан базовый тип, любой тип, производный от базового, можно передать методу в качестве соответствующего аргумента. Если аргумент используется внутри тела метода, конкретный метод, который выполняется, зависит от типа аргумента. Если дополнительные функциональные возможности, предоставляемые производным типом, не требуются, использование базового типа позволяет более широко использовать метод.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, измените тип параметра на его базовый тип.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно отключить вывод предупреждения из этого правила.

- Если метод требует конкретной функциональности, предоставляемой производным типом

     \- или -

- чтобы обеспечить передачу в метод только производного типа или более производного типа.

В таких случаях код будет более надежным из-за проверки строгого типа, предоставляемой компилятором и средой выполнения.

## <a name="example"></a>Пример

В следующем примере показан метод, `ManipulateFileStream`, который можно использовать только <xref:System.IO.FileStream> с объектом, который нарушает это правило. Второй метод, `ManipulateAnyStream`, удовлетворяет правилу, <xref:System.IO.FileStream> заменяя параметр с помощью <xref:System.IO.Stream>.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Связанные правила

[CA1059: Члены не должны предоставлять определенные конкретные типы](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)