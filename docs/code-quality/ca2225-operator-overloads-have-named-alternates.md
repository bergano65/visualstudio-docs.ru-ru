---
title: "CA2225: Перегрузки операторов с именами | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f8c7b71fc964f898aefc5e243c787be71a8a063a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: для перезагрузок оператора существуют дополнения с именами
|||  
|-|-|  
|TypeName|OperatorOverloadsHaveNamedAlternates|  
|CheckId|CA2225|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Обнаружена перегрузка оператора, однако не найден ожидаемый именованный альтернативный метод.  
  
## <a name="rule-description"></a>Описание правила  
 Перегрузка операторов позволяет использовать символы, представляющие вычисления для типа. Например тип, который перегружает знак плюса (+) для добавления обычно есть другой член с именем «Add». Именованный альтернативный член предоставляет доступ к те же функциональные возможности, что и оператор и предоставляется для разработчиков, которые программируют на языках, не поддерживает перегруженные операторы.  
  
 Данное правило отслеживает операторы, перечисленные в следующей таблице.  
  
|C#|Visual Basic|C++|Альтернативное имя|  
|---------|------------------|-----------|--------------------|  
|+ (двоичный)|+|+ (двоичный)|Add|  
|+=|+=|+=|Add|  
|&|И|&|BitwiseAnd|  
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
|++|Н/Д|++|Increment|  
|<>|!=|Равно|  
|<<|<<|<<|Чтения|  
|<<=|<<=|<<=|Чтения|  
|<|<|<|Сравнение|  
|<=|<=|\<=|Сравнение|  
|&&|Н/Д|&&|LogicalAnd|  
|&#124;&#124;|Н/Д|&#124;&#124;|LogicalOr|  
|!|Н/Д|!|LogicalNot|  
|%|Mod|%|Остаток от деления или остатка|  
|%=|Н/Д|%=|Mod|  
|* (двоичный)|*|*|Multiply|  
|*=|Н/Д|*=|Multiply|  
|~|не|~|OnesComplement|  
|>>|>>|>>|Правая|  
=|Н/Д|>>=|Правая|  
|-(двоичный)|-(двоичный)|-(двоичный)|Subtract|  
|-=|Н/Д|-=|Subtract|  
|true|IsTrue|Н/Д|IsTrue (свойство)|  
|— (унарные)|Н/Д|-|Инверсия|  
|+ (унарный)|Н/Д|+|Плюс|  
|False|IsFalse|False|IsTrue (свойство)|  
  
 Н/д == не могут быть перегружены на выбранном языке.  
  
 Данное правило также проверяет неявные и явные операторы приведения в типе (`SomeType`) посредством проверки методов с именем `ToSomeType` и `FromSomeType`.  
  
 В C# при перегрузке двоичного оператора соответствующий оператор присваивания, при его наличии, также неявно перегружается.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте альтернативный метод для оператора; использовать рекомендуемые альтернативное имя имен.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила, если вы реализуете общей библиотеки. Приложения можно игнорировать предупреждение из этого правила.  
  
## <a name="example"></a>Пример  
 В следующем примере определяется структура, которая нарушает это правило. Чтобы исправить пример, добавьте открытый `Add(int x, int y)` метод в структуре.  
  
 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)