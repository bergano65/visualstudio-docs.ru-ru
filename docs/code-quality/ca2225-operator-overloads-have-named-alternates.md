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
ms.workload:
- multiple
ms.openlocfilehash: 2f427bcdf4ec4e88dcc2842699d738dae7e8e09d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546902"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225. Для перегрузок операторов существуют варианты с именами

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Обнаружена перегрузка оператора, и не найден ожидаемый именованный альтернативный метод.

По умолчанию это правило рассматривает только видимые извне типы, но это можно [настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Перегрузка операторов позволяет использовать символы для представления вычислений для типа. Например, тип, который перегружает символ "плюс" (+) для сложения, обычно имеет альтернативный элемент с именем "Add". Именованный альтернативный элемент предоставляет доступ к тем же функциональным возможностям, что и оператор, и предоставляется разработчикам, которые запрограммированы на языках, не поддерживающих перегруженные операторы.

Это правило проверяет операторы, перечисленные в следующей таблице.

|C#|Visual Basic|C++|Альтернативное имя|
|---------|------------------|-----------|--------------------|
|+ (двоичный)|+|+ (двоичный)|Add|
|+=|+=|+=|Add|
|&|и|&|BitwiseAnd|
|&=|И =|&=|BitwiseAnd|
|&#124;|Или|&#124;|BitwiseOr|
||=|Или =||=|BitwiseOr|
|--|Н/Д|--|Decrement|
|/|/|/|Divide|
|/=|/=|/=|Divide|
|==|=|==|Равно|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Сравнение|
|>=|>=|>=|Сравнение|
|++|Н/Д|++|Приращение|
|<>|!=|Равно|
|<<|<<|<<|лефтшифт|
|<<=|<<=|<<=|лефтшифт|
|<|<|<|Сравнение|
|<=|<=|\<=|Сравнение|
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

N/A = = не может быть перегружен на выбранном языке.

Правило также проверяет явные и неявные операторы приведения в типе`SomeType`(), проверяя методы `ToSomeType` с `FromSomeType`именами и.

В C#при перегрузке бинарного оператора соответствующий оператор присваивания, если таковой имеется, также неявно перегружается.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте альтернативный метод для оператора. присвойте ему имя с рекомендуемым альтернативным именем.

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