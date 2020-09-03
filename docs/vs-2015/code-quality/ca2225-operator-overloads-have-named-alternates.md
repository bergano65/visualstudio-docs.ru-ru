---
title: 'CA2225: перегрузки оператора имеют именованные варианты | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2dc43e92b92b6f963900057a76dfe88e38a3638f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545227"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225. Для перегрузок операторов существуют варианты с именами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Обнаружена перегрузка оператора, однако не найден ожидаемый именованный альтернативный метод.

## <a name="rule-description"></a>Описание правила
 Перегрузка операторов позволяет использовать символы для представления вычислений для типа. Например, тип, который перегружает символ "плюс" (+) для сложения, обычно имеет альтернативный элемент с именем "Add". Именованный альтернативный элемент предоставляет доступ к тем же функциональным возможностям, что и оператор, и предоставляется разработчикам, которые запрограммированы на языках, не поддерживающих перегруженные операторы.

 Это правило проверяет операторы, перечисленные в следующей таблице.

|C#|Visual Basic|C++|Альтернативное имя|
|---------|------------------|-----------|--------------------|
|+ (двоичный)|+|+ (двоичный)|Добавить|
|+=|+=|+=|Добавить|
|&|And|&|BitwiseAnd|
|&=|И =|&=|BitwiseAnd|
|&#124;|либо|&#124;|BitwiseOr|
|&#124;=|Или =|&#124;=|BitwiseOr|
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
|~|Not|~|онескомплемент|
|>>|>>|>>|Правая клавиша SHIFT|
=|Н/Д|>>=|Правая клавиша SHIFT|
|-(двоичный)|-(двоичный)|-(двоичный)|Subtract|
|-=|Н/Д|-=|Subtract|
|Да|IsTrue|Н/Д|IsTrue (свойство)|
|— (унарные)|Н/Д|-|Negate|
|+ (унарный)|Н/Д|+|Плюс|
|false|IsFalse|Неверно|IsTrue (свойство)|

 N/A = = не может быть перегружен на выбранном языке.

 Правило также проверяет явные и неявные операторы приведения в типе ( `SomeType` ), проверяя методы с именами `ToSomeType` и `FromSomeType` .

 В C# при перегрузке бинарного оператора соответствующий оператор присваивания, если таковой имеется, также неявно перегружается.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, реализуйте альтернативный метод для оператора. присвойте ему имя с рекомендуемым альтернативным именем.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, если реализуется общая библиотека. Приложения могут игнорировать предупреждение от этого правила.

## <a name="example"></a>Пример
 В следующем примере определяется структура, нарушающая это правило. Чтобы исправить пример, добавьте в структуру открытый `Add(int x, int y)` метод.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1046. Не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226. Перегрузки операторов должны быть симметричными](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224. Переопределяйте Equals при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218. Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231. Перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
