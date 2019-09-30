---
title: CA2225. Для перегрузок операторов существуют варианты с именами
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: b4db3074d334fe32f95c4d1b8446921c4e4d47ba
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481775"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225. Для перегрузок операторов существуют варианты с именами

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Обнаружена перегрузка оператора, и не найден ожидаемый именованный альтернативный метод.

По умолчанию это правило рассматривает только видимые извне типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Перегрузка операторов позволяет использовать символы для представления вычислений для типа. Например, тип, который перегружает символ "плюс" `+` для сложения, обычно имеет альтернативный элемент с именем `Add`. Именованный альтернативный элемент предоставляет доступ к тем же функциональным возможностям, что и оператор. Он предоставляется разработчикам, которые запрограммированы на языках, не поддерживающих перегруженные операторы.

Это правило проверяет следующее.

- Неявные и явные операторы приведения в типе путем проверки методов с именами `To<typename>` и `From<typename>`.

- Операторы, перечисленные в следующей таблице:

|C#|Visual Basic|C++|Имя альтернативного метода|
|-|-|-|-|
|+ (двоичный)|+|+ (двоичный)|Add|
|+=|+=|+=|Add|
|&|и|&|BitwiseAnd|
|&=|И =|&=|BitwiseAnd|
|&#124;|Или|&#124;|BitwiseOr|
|&#124;=|Или =|&#124;=|BitwiseOr|
|--|Н/Д|--|Decrement|
|/|/|/|Divide|
|/=|/=|/=|Divide|
|==|=|==|Равно|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|CompareTo или Compare|
|>=|>=|>=|CompareTo или Compare|
|++|Н/Д|++|Приращение|
|!=|<>|!=|Равно|
|<<|<<|<<|лефтшифт|
|<<=|<<=|<<=|лефтшифт|
|<|<|<|CompareTo или Compare|
|<=|<=|\<=|CompareTo или Compare|
|&&|Н/Д|&&|LogicalAnd|
|&#124;&#124;|Н/Д|&#124;&#124;|Логический|
|!|Н/Д|!|логикалнот|
|%|Mod|%|Mod или остаток|
|%=|Н/Д|%=|Mod|
|* (двоичный)|*|*|Multiply|
|*=|Н/Д|*=|Multiply|
|~|not|~|онескомплемент|
|>>|>>|>>|Правая клавиша SHIFT|
=|Н/Д|>>=|Правая клавиша SHIFT|
|-(двоичный)|-(двоичный)|-(двоичный)|Subtract|
|-=|Н/Д|-=|Subtract|
|true|IsTrue|Н/Д|IsTrue (свойство)|
|— (унарные)|Н/Д|-|Negate|
|+ (унарный)|Н/Д|+|Плюс|
|false|IsFalse|False|IsTrue (свойство)|

\* N/A означает, что оператор не может быть перегружен на выбранном языке.

> [!NOTE]
> В C#при перегрузке бинарного оператора соответствующий оператор присваивания, если таковой имеется, также неявно перегружается.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте альтернативный метод для оператора. Присвойте ему имя с рекомендуемым альтернативным именем.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Не отключайте предупреждение из этого правила, если реализуется общая библиотека. Приложения могут игнорировать предупреждение от этого правила.

## <a name="configurability"></a>Возможности настройки

Если вы используете это правило из [анализаторов FxCop](install-fxcop-analyzers.md) (а не для анализа прежних версий), можно настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл. editorconfig в проекте:

```ini
dotnet_code_quality.ca2225.api_surface = private, internal
```

Этот параметр можно настроить только для этого правила, для всех правил или для всех правил в этой категории (использование). Дополнительные сведения см. в статье [Настройка средств FxCop Analyzer](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере определяется структура, нарушающая это правило. Чтобы исправить пример, добавьте в структуру открытый `Add(int x, int y)` метод.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1046: Не перегружать оператор Equals в ссылочных типах](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226: Операторы должны иметь симметричные перегрузки](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224: Переопределять Equals при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Переопределять GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)