---
title: CA2225. Оператор дополнения с именами | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aa90a1e97b563ef549cb3f628fcf9130a364c50a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992233"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225. Для перегрузок операторов существуют варианты с именами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Обнаружена перегрузка оператора, однако не найден ожидаемый именованный альтернативный метод.

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

## <a name="example"></a>Пример
 В следующем примере определяется структура, которая нарушает это правило. Чтобы исправить в примере, добавьте открытое `Add(int x, int y)` метод к структуре.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1046: Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Операторы должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
