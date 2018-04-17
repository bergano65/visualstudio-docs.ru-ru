---
title: 'CA2226: Операторы должны быть симметричны | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 17ce9653f5763788b8a6988994c379fc885152ad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: перегрузки операторов должны быть симметричны
|||  
|-|-|  
|TypeName|OperatorsShouldHaveSymmetricalOverloads|  
|CheckId|CA2226|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип реализует оператор равенства или неравенства, но не реализует противоположный оператор.  
  
## <a name="rule-description"></a>Описание правила  
 Нет ни в коем случае равенства или неравенства применимо к экземплярам типа, куда противоположный оператор не определен. Обычно типы реализуют оператор неравенства, возвращая инвертированное значение оператора равенства.  
  
 Компилятор C# выдает ошибку нарушения этого правила.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, реализуйте одновременно операторы равенства и неравенства или удалить один, который присутствует.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Тип не будет работать таким способом, который согласуется с [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1046: не перегружайте оператор равенства для ссылочных типов](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: для перезагрузок оператора существуют дополнения с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2224: переопределяйте равенство при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: перегружать равенство операторов следует при перегрузке ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)