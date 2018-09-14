---
title: 'CA1052: типы со статическими заполнителями должны быть запечатаны'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bc264b9e47fe9169c0b1ad9d3257323c437620f7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550432"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: типы со статическими заполнителями должны быть запечатаны

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип содержит только статические члены и не объявлен с [запечатанный](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) модификатор.

## <a name="rule-description"></a>Описание правила
 В этом правиле предполагается, что тип, который содержит только статические члены не предназначен для наследоваться, так как тип не поддерживает любые функции, которые могут переопределяться в производном типе. Тип, который предназначен не обязан иметь производные классы должны быть помечены `sealed` модификатор, чтобы запретить его использование в качестве базового типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте тип как `sealed`. Если вы ориентируетесь [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 или более поздней, лучшим подходом является пометить тип как `static`. Таким образом вам не потребуется объявить закрытый конструктор для предотвращения создания класса.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, только в том случае, если тип должен наследоваться. Отсутствие `sealed` модификатор предполагает, что тип является полезным в качестве базового типа.

## <a name="example-of-a-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В примере показан тип, который нарушает правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Исправление с модификатором Static

### <a name="description"></a>Описание
 В следующем примере показано, как устранить нарушение этого правила, пометив тип с `static` модификатор.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1053: типы статических владельцев не должны иметь конструкторы](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
