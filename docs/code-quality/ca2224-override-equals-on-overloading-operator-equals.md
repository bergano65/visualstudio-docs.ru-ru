---
title: "CA2224: Переопределяйте равенство при перегрузке оператора равенства | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4d34acafb4f014b91e4c0f707060ce0442a413e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: переопределяйте равенство при перегрузке оператора равенства
|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Открытый тип реализует оператор равенства, но не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Описание правила  
 Оператор равенства должен быть синтаксически удобный способ доступа к функциям <xref:System.Object.Equals%2A> метод. При реализации оператора равенства логику должен совпадать с <xref:System.Object.Equals%2A>.  
  
 Компилятор C# выдает предупреждение, если код нарушает это правило.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, следует либо удалить реализации оператора равенства, либо переопределить <xref:System.Object.Equals%2A> и имеют те же значения возврата двух методов. Если оператор равенства не вводит непредсказуемому поведению, вы можете исправить нарушение, обеспечив реализацию <xref:System.Object.Equals%2A> , который вызывает <xref:System.Object.Equals%2A> метод в базовом классе.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, если оператор равенства возвращает совпадает со значением в унаследованной реализации <xref:System.Object.Equals%2A>. В разделе включает тип, который может безопасно отключить предупреждение из этого правила.  
  
## <a name="examples-of-inconsistent-equality-definitions"></a>Примеры неоднородных определений равенства  
  
### <a name="description"></a>Описание:  
 В следующем примере показано тип с несогласованными определениями равенства. `BadPoint`изменяет значение равенства, предоставляя пользовательскую реализацию оператора равенства, но не переопределяет <xref:System.Object.Equals%2A> , чтобы он ведет себя идентично.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## <a name="example"></a>Пример  
 Следующий код проверяет поведение `BadPoint`.  
  
 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 В этом примере формируются следующие данные:  
  
 **= ([0] 1,1) и b = ([1] 2,2) равны? Нет**  
**== b? Нет**  
**a1 и которых равны? Да**  
**a1 ==? Да**  
**b и bcopy равны? Нет**  
**b == bcopy? Да**   
## <a name="example"></a>Пример  
 В следующем примере показано тип, который технически нарушает это правило, но его поведение не несогласованно.  
  
 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## <a name="example"></a>Пример  
 Следующий код проверяет поведение `GoodPoint`.  
  
 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 В этом примере формируются следующие данные:  
  
 **= (1,1) и b = (2,2) равны? Нет**  
**== b? Нет**  
**a1 и которых равны? Да**  
**a1 ==? Да**  
**b и bcopy равны? Да**  
**b == bcopy? Да**   
## <a name="class-example"></a>Пример класса  
  
### <a name="description"></a>Описание:  
 В следующем примере класс (ссылочный тип), нарушающий это правило.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере нарушение устраняется путем переопределения <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## <a name="structure-example"></a>Пример структуры  
  
### <a name="description"></a>Описание:  
 В следующем примере показана структура (тип значения), нарушающий это правило.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере нарушение устраняется путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: для перезагрузок оператора существуют дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218: переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)