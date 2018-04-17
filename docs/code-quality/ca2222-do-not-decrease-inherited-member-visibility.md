---
title: 'CA2222: Не уменьшайте видимость унаследованных членов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de96b199adf5b282f70207478e4d9ae38c4d00f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: не уменьшайте видимость унаследованных членов
|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Закрытый метод в незапечатанный тип имеет подпись, идентичный открытый метод, объявленный в базовом типе. Закрытый метод не является последней.  
  
## <a name="rule-description"></a>Описание правила  
 Не следует изменять модификатор доступа для унаследованных членов. Если сделать унаследованный член закрытым, то доступ вызывающих объектов к реализации метода базового класса все равно не будет запрещен. Если сделать член закрытым, а незапечатанный тип, наследуемые типы могут вызывать последнюю открытую реализацию метода в иерархии наследования. Если нужно изменить модификатор доступа, метод должен быть помечен как окончательный, или его тип должны быть запечатаны, чтобы исключить возможность переопределения метода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените доступ к быть отличным от private. Кроме того если она поддерживается язык программирования, можно сделать метод конечный.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий это правило.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]