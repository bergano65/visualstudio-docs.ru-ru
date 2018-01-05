---
title: "CA1815: следует Переопределение равенства и равенства операторов в типах значений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 927e13266bf308096592fb5714e1247f4b596ca8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: следует переопределять равенства и равенства операторов в типах значений
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Открытого типа значения не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName>, или не реализует оператор равенства (==). Это правило проверки перечислений.  
  
## <a name="rule-description"></a>Описание правила  
 Для типов значений, унаследованной реализации <xref:System.Object.Equals%2A> используется библиотека отражения и сравнивается содержимое всех полей. Отражение является процессом, требующим с точки зрения вычислений больших затрат, и сравнение каждого поля на равенство может быть лишним. Если пользователям потребуется сравнения и сортировки экземпляры или использовать их в качестве ключей хэш-таблиц, тип значения должен реализовывать <xref:System.Object.Equals%2A>. Если язык программирования поддерживает перегрузку операторов, также необходимо предоставить реализацию операторов равенства и неравенства.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, необходимо предоставить реализацию <xref:System.Object.Equals%2A>. Если это возможно, реализуйте оператор равенства.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, если экземпляры типа значения не будут сравниваться друг с другом.  
  
## <a name="example-of-a-violation"></a>Пример нарушения  
  
### <a name="description"></a>Описание:  
 В следующем примере показана структура (тип значения), нарушающий это правило.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>Пример того, как решения по устранению  
  
### <a name="description"></a>Описание:  
 В следующем примере предыдущее нарушение устраняется путем переопределения <xref:System.ValueType.Equals%2A?displayProperty=fullName> и реализации операторов равенства (==,! =).  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: перегрузки операторов должны быть симметричны](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Object.Equals%2A?displayProperty=fullName>