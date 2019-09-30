---
title: CA2104. Не объявляйте изменяемые ссылочные типы только для чтения
ms.date: 11/01/2018
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8f4f165b4b00f46b478907c9affca672b4c7f113
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232957"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104. Не объявляйте изменяющиеся ссылочные типы только для чтения

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

> [!NOTE]
> Правило CA2104 устарело и будет удалено в следующей версии Visual Studio. Он не будет реализован в качестве [анализатора](roslyn-analyzers-overview.md) из-за сложного анализа, необходимого для определения фактической неизменности типа.

## <a name="cause"></a>Причина:

Видимый извне тип содержит видимое извне и доступное только для чтение поле, являющееся изменяемым ссылочным типом.

## <a name="rule-description"></a>Описание правила

Изменяемый тип — это тип, экземпляр которого может быть изменен. <xref:System.Text.StringBuilder?displayProperty=fullName> Класс является примером изменяемого ссылочного типа. Он содержит члены, которые могут изменять значение экземпляра класса. Примером неизменяемого ссылочного типа является <xref:System.String?displayProperty=fullName> класс. После создания экземпляра его значение не может изменяться.

Модификатор только[для](/dotnet/csharp/language-reference/keywords/readonly) чтения (ReadOnly C# [в, только](/dotnet/visual-basic/language-reference/modifiers/readonly) в Visual Basic и [const](/cpp/cpp/const-cpp) в C++) для поля ссылочного типа (или указателя в C++) предотвращает замену поля другим экземпляром ссылочного типа. Однако модификатор не предотвращает изменение данных экземпляра поля с помощью ссылочного типа.

Это правило может непреднамеренно показывать нарушение для типа, который фактически является неизменяемым. В этом случае можно спокойно отключить предупреждение.

Поля массива, доступные только для чтения, исключены из этого правила, но вызывают нарушение [CA2105: Поля массивов не должны быть правилом только](../code-quality/ca2105-array-fields-should-not-be-read-only.md) для чтения.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите модификатор "только для чтения" или, если критическое изменение допустимо, замените поле неизменяемым типом.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно отключить вывод предупреждений из этого правила, если тип поля является неизменяемым.

## <a name="example"></a>Пример

В следующем примере показано объявление поля, которое вызывает нарушение этого правила:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]