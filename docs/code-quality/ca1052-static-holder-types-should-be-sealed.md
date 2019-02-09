---
title: CA1052. Типы со статическими заполнителями должны быть запечатаны
ms.date: 11/09/2018
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 36bd459f2a9f7300328aadd3509530f4802e71cd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922456"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052. Типы со статическими заполнителями должны быть запечатаны

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Открытый или защищенный, неабстрактный тип содержит только статические члены и не объявлен с [запечатанный](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) модификатор.

## <a name="rule-description"></a>Описание правила

CA1052 правило предполагает, что тип, который содержит только статические члены не предназначен для наследоваться, так как тип не поддерживает любые функции, которые могут переопределяться в производном типе. Тип, который предназначен не обязан иметь производные классы должны быть помечены `sealed` или `NotInheritable` модификатор, чтобы запретить его использование в качестве базового типа. Это правило не срабатывает для абстрактных классов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, пометьте тип как `sealed` или `NotInheritable`. Если целевой платформой является .NET Framework 2.0 или более поздней версии, лучшим подходом является пометить тип как `static` или `Shared`. Таким образом не нужно объявить закрытый конструктор для предотвращения создания класса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Отключайте предупреждение из этого правила, только в том случае, если тип должен наследоваться. Отсутствие `sealed` или `NotInheritable` модификатор предполагает, что тип является полезным в качестве базового типа.

## <a name="example-of-a-violation"></a>Пример нарушения

В примере показан тип, который нарушает правило.

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Исправление с модификатором static

В следующем примере показано, как устранить нарушение этого правила, пометив тип с `static` модификатор в C#.

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Связанные правила

[CA1053: Типы со статическими заполнителями не должны иметь конструкторы](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)