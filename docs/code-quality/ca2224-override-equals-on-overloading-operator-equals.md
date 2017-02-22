---
title: "CA2224: переопределяйте равенство при перегрузке оператора равенства | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
  - "OverrideEqualsOnOverridingOperatorEquals"
helpviewer_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2224: переопределяйте равенство при перегрузке оператора равенства
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Открытый тип реализует оператор равенства, но не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Описание правила  
 Оператор равенства — это синтаксически удобный способ получения доступа к функциональности метода <xref:System.Object.Equals%2A>.  При реализации оператора равенства его логика должна совпадать с логикой метода <xref:System.Object.Equals%2A>.  
  
 Если код нарушает это правило, компилятор C\# выдает предупреждение.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, следует либо удалить реализацию оператора равенства, либо переопределить <xref:System.Object.Equals%2A>, чтобы оба метода возвращали одинаковые значения.  Если оператор равенства не вызывает неоднородного поведения, можно устранить нарушение, предоставив реализацию <xref:System.Object.Equals%2A>, вызывающую метод <xref:System.Object.Equals%2A> в базовом классе.  
  
## Отключение предупреждений  
 Можно отключать предупреждения этого правила, если оператор равенства возвращает такое же значение, как и унаследованная реализация <xref:System.Object.Equals%2A>.  В разделе примера ниже приведен тип, для которого можно безопасно отключать предупреждения этого правила.  
  
## Примеры неоднородных определений равенства  
  
### Описание  
 В следующем примере показан тип с несогласованными определениями равенства.  `BadPoint` изменяет значение равенства, предоставляя пользовательскую реализацию оператора равенства, но не переопределяет <xref:System.Object.Equals%2A>, так что он ведет себя идентично.  
  
### Код  
 [!code-cs[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## Пример  
 В следующем коде проверяется поведение `BadPoint`.  
  
 [!code-cs[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 В результате выполнения примера получается следующий результат:  
  
  **a \=  \(\[0\] 1,1\) и b \= \(\[1\] 2,2\) равны?  Нет**  
**a \=\= b ?  Нет**  
**a1 и a равны?  Да**  
**a1 \=\= a ?  Да**  
**b и bcopy равны ?  Нет**  
**b \=\= bcopy ?  Да**    
## Пример  
 В следующем примере показан тип, который технически нарушает это правило, но его поведение не является неоднородным.  
  
 [!code-cs[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## Пример  
 В следующем коде проверяется поведение `GoodPoint`.  
  
 [!code-cs[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 В результате выполнения примера получается следующий результат:  
  
  **a \=  \(1,1\) и b \= \(2,2\) равны?  Нет**  
**a \=\= b ?  Нет**  
**a1 и a равны?  Да**  
**a1 \=\= a ?  Да**  
**b и bcopy равны ?  Да**  
**b \=\= bcopy ?  Да**    
## Пример класса  
  
### Описание  
 В следующем примере демонстрируется класс \(ссылочный тип\), нарушающий это правило.  
  
### Код  
 [!code-cs[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## Пример  
 В следующем примере нарушение устраняется путем переопределения <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## Пример структуры  
  
### Описание  
 В следующем примере показана структура \(тип значения\), нарушающая это правило.  
  
### Код  
 [!code-cs[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## Пример  
 В следующем примере нарушение устраняется путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## Связанные правила  
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: для перезагрузок оператора существуют дополнения с именами](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218: переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)