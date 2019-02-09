---
title: CA2104. Не объявляйте изменяющиеся ссылочные типы только для чтения
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
ms.openlocfilehash: a033ed83d6d349ac3876a6f11a24570f3ff8f60c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945018"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104. Не объявляйте изменяющиеся ссылочные типы только для чтения

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

> [!NOTE]
> CA2104 правило является устаревшим и будет удален в будущих версиях Visual Studio.

## <a name="cause"></a>Причина

Видимый извне тип содержит видимое извне и доступное только для чтение поле, являющееся изменяемым ссылочным типом.

## <a name="rule-description"></a>Описание правила

Изменяемый тип — это тип, экземпляр которого может быть изменен. <xref:System.Text.StringBuilder?displayProperty=fullName> Класс является примером изменяемый ссылочный тип. Он содержит члены, которые можно изменить значение экземпляра класса. Примером неизменяемого ссылочного типа является <xref:System.String?displayProperty=fullName> класса. После его создания экземпляра, его значение изменить нельзя.

Модификатор доступа только для чтения ([только для чтения](/dotnet/csharp/language-reference/keywords/readonly) в C#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) в Visual Basic и [const](/cpp/cpp/const-cpp) в C++) на ссылочный тип поля (или указатель в C++) не позволяет поля заменены другой экземпляр ссылочного типа. Однако модификатор не препятствует данных экземпляра поля изменению посредством ссылочного типа.

Это правило может случайно Показать нарушения для типа, является, по сути, неизменяемым. В этом случае можно отключить предупреждение.

Поля только для чтения массивов будут исключены из этого правила, но вместо этого приведет к нарушению [CA2105: Поля массивов не должны считываться только](../code-quality/ca2105-array-fields-should-not-be-read-only.md) правило.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите модификатор только для чтения, или, если допустима критическое изменение, замените поле неизменяемый тип.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если тип поля является неизменяемым.

## <a name="example"></a>Пример

В следующем примере объявление поля, которое вызывает нарушение этого правила:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]