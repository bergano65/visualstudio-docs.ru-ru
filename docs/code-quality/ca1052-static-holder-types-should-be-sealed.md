---
title: 'CA1052: Типы со статическими заполнителями должны быть запечатаны | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fc3954c4c446ff578790e92bc60dd97e42a0d8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: типы со статическими заполнителями должны быть запечатаны
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный тип содержит только статические элементы и не объявлен с [запечатанный](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) модификатор.  
  
## <a name="rule-description"></a>Описание правила  
 В этом правиле предполагается, что тип, который содержит только статические члены не предназначено для наследуется, поскольку тип не предоставляет никаких функциональных возможностей, который может быть переопределен в производном типе. Тип, который не предназначен для наследования должны быть помечены `sealed` модификатор, чтобы запретить его использование в качестве базового типа.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, пометить тип как `sealed`. Если вы используете [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 или более поздней версии, лучшим подходом является пометить тип как `static`. Таким образом можно избежать необходимости объявлять закрытый конструктор для предотвращения создания класса.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила только в том случае, если тип должен наследоваться. Отсутствие `sealed` модификатор предполагает, что тип является полезны в качестве базового типа.  
  
## <a name="example-of-a-violation"></a>Пример нарушения  
  
### <a name="description"></a>Описание  
 В следующем примере показано тип, нарушающий правило.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>Исправьте модификатором Static  
  
### <a name="description"></a>Описание  
 В следующем примере показано, как устранить нарушение этого правила, пометив тип с `static` модификатор.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1053: типы статических владельцев не должны иметь конструкторы](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
