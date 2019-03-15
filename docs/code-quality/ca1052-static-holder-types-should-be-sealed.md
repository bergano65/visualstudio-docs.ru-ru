---
title: CA1052. Типы со статическими заполнителями должны быть запечатаны
ms.date: 03/11/2019
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
ms.openlocfilehash: 46a8c9a4e22c7a54a4b2b68f95bb2b81f3a0888e
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57870390"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052. Типы со статическими заполнителями должны быть запечатаны

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Неабстрактный тип содержит только статические члены и не объявлен с [запечатанный](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) модификатор.

По умолчанию это правило считывает только типы, видимые извне, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

CA1052 правило предполагает, что тип, который содержит только статические члены не предназначен для наследоваться, так как тип не поддерживает любые функции, которые могут переопределяться в производном типе. Тип, который предназначен не обязан иметь производные классы должны быть помечены `sealed` или `NotInheritable` модификатор, чтобы запретить его использование в качестве базового типа. Это правило не срабатывает для абстрактных классов.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, пометьте тип как `sealed` или `NotInheritable`. Если целевой платформой является .NET Framework 2.0 или более поздней версии, лучшим подходом является пометить тип как `static` или `Shared`. Таким образом не нужно объявить закрытый конструктор для предотвращения создания класса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Отключайте предупреждение из этого правила, только в том случае, если тип должен наследоваться. Отсутствие `sealed` или `NotInheritable` модификатор предполагает, что тип является полезным в качестве базового типа.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca1052.api_surface = private, internal
```

В этой категории (структуры) можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Пример нарушения

В следующем примере показано тип, который нарушает правило:

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Исправление с модификатором static

В следующем примере показано, как устранить нарушение этого правила, пометив тип с `static` модификатор в C#:

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1053: Типы со статическими заполнителями не должны иметь конструкторы](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)