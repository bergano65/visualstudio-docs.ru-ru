---
title: 'CA1047: не объявляйте защищенные элементы в запечатанных типах'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a19e17c200f36d3edb1cadbab4d573f6a1d3cc0a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550064"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: не объявляйте защищенные элементы в запечатанных типах

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип является `sealed` (`NotInheritable` в Visual basic) и объявляют защищенный член или защищенные вложенного типа. Это правило не касается нарушений <xref:System.Object.Finalize%2A> методы, которые необходимо следовать этому шаблону.

## <a name="rule-description"></a>Описание правила
 Типы объявляют защищенный члены таким образом, чтобы наследующие типы могли получить доступ к члену или переопределить его. По определению не может наследовать от запечатанного типа, что означает, что вызов защищенных методов для запечатанных типов невозможен.

 Компилятор C# выдает предупреждение для этой ошибки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, изменить уровень доступа члена на закрытый или сделайте тип наследуемым.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Тип в ее текущем состоянии может привести к проблемам обслуживания и не предоставляет никаких преимуществ.

## <a name="example"></a>Пример
 В следующем примере тип, который нарушает это правило.

 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]