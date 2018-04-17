---
title: 'CA1046: Не перегружайте оператор равенства для ссылочных типов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e78217e2ce8613ca312a96058b4477d1da82a5e7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: не перегружайте оператор равенства для ссылочных типов
|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или вложенный открытый ссылочный тип перегружает оператор равенства.  
  
## <a name="rule-description"></a>Описание правила  
 Реализация оператора равенства по умолчанию почти всегда правильно работает для ссылочных типов. По умолчанию две ссылки равны, если они указывают на один объект.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите реализацию оператора равенства.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно отключать предупреждение из этого правила, если ссылочный тип ведет себя как встроенный тип значения. Это может применяться для выполнения сложения или вычитания для экземпляров типа, правильность, возможно, для реализации оператора равенства и отключение нарушение.  
  
## <a name="example"></a>Пример  
 В следующем примере показано поведение по умолчанию при сравнении двух ссылок.  
  
 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем приложении сравниваются несколько ссылок.  
  
 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 В этом примере формируются следующие данные:  
  
 **= новый (2,2) и b = равны новый (2,2)? Нет**  
**c и которых равны? Да**  
**b и являются ==? Нет**  
**c и являются ==? Да**   
## <a name="related-rules"></a>Связанные правила  
 [CA1013: перегружайте оператор равенства при перегрузке сложения и вычитания](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)