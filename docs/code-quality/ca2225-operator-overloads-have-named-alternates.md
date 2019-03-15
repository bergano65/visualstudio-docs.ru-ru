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
ms.openlocfilehash: a8a1c7015421b686d47bfea4c3341ec76748f8ad
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873072"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225. Для перегрузок операторов существуют варианты с именами

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Обнаружена перегрузка оператора и не найден ожидаемый именованный альтернативный метод.

По умолчанию это правило считывает только типы, видимые извне, но это [можно настроить](#configurability).

## <a name="rule-description"></a>Описание правила

Перегрузка операторов позволяет использовать символы, представляющие вычисления для типа. Например тип, который перегружает символ "плюс" (+) для добавления обычно есть другой член с именем «Добавить». Именованный альтернативный член предоставляет доступ к ту же функциональность, что оператор и предоставляется для разработчиков, которые программируют на языках, которые не поддерживает перегруженные операторы.

Это правило проверяет, операторы, перечисленные в следующей таблице.

|C#|Visual Basic|C++|Альтернативное имя|
|---------|------------------|-----------|--------------------|
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
|^=|Xor =|^=|Xor|
|>|>|>|Сравнение|
|>=|>=|>=|Сравнение|
|++|Н/Д|++|Приращение|
|<>|!=|Равно|
|<<|<<|<<|Левая|
|<<=|<<=|<<=|Левая|
|<|<|<|Сравнение|
|<=|<=|\<=|Сравнение|
|&&|Н/Д|&&|LogicalAnd|
|&#124;&#124;|Н/Д|&#124;&#124;|LogicalOr|
|!|Н/Д|!|LogicalNot|
|%|Mod|%|Mod или остаток|
|%=|Н/Д|%=|Mod|
|* (двоичный)|*|*|Multiply|
|*=|Н/Д|*=|Multiply|
|~|not|~|OnesComplement|
|>>|>>|>>|Правая клавиша SHIFT|
=|Н/Д|>>=|Правая клавиша SHIFT|
|-(двоичный)|-(двоичный)|-(двоичный)|Subtract|
|-=|Н/Д|-=|Subtract|
|true|IsTrue|Н/Д|IsTrue (свойство)|
|— (унарные)|Н/Д|-|Инверсия|
|+ (унарный)|Н/Д|+|Plus|
|False|IsFalse|False|IsTrue (свойство)|

Н/д == не могут быть перегружены на выбранном языке.

Правило также проверяет неявные и явные операторы приведения типа (`SomeType`), установив для методов с именем `ToSomeType` и `FromSomeType`.

В C# при перегрузке бинарного оператора соответствующий оператор присвоения, если таковые имеются, также неявно перегружается.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, реализуйте альтернативный метод для оператора; имя с помощью рекомендуемое альтернативное имя.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Не отключайте предупреждение из этого правила, если вы реализуете общей библиотеки. Приложения можно игнорировать предупреждение из этого правила.

## <a name="configurability"></a>Возможность настройки

Если у вас это правило из [анализаторы FxCop](install-fxcop-analyzers.md) (а не с помощью функций анализа статического кода), можно настроить, какие части вашей базы кода, чтобы применить это правило, в зависимости от их доступности. Например чтобы указать, что правило должно выполняться только для рабочей области не являющийся открытым API, добавьте следующую пару "ключ значение" файла editorconfig в проект:

```
dotnet_code_quality.ca2225.api_surface = private, internal
```

В этой категории (использование), можно настроить этот параметр для только что это правило, для всех правил или для всех правил. Дополнительные сведения см. в разделе [анализаторы FxCop, Настройка](configure-fxcop-analyzers.md).

## <a name="example"></a>Пример

В следующем примере определяется структура, которая нарушает это правило. Чтобы исправить в примере, добавьте открытое `Add(int x, int y)` метод к структуре.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Связанные правила

- [CA1046: Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226: Операторы должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224: Переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)