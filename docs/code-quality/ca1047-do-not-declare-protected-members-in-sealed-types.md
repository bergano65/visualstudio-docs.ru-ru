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
ms.workload:
- multiple
ms.openlocfilehash: 079d330907981be11e0c07d44c83519975c17560
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897716"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: не объявляйте защищенные элементы в запечатанных типах
|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип имеет `sealed` (`NotInheritable` в Visual basic) и объявляет защищенный элемент или защищенные вложенного типа. Это правило не касается нарушений <xref:System.Object.Finalize%2A> методы, которые должны следовать этому шаблону.

## <a name="rule-description"></a>Описание правила
 Типы объявляют защищенный члены таким образом, чтобы наследующие типы могли получить доступ к члену или переопределить его. По определению не может наследовать от запечатанного типа, что означает, что вызов защищенных методов для запечатанных типов невозможен.

 Компилятор C# выдает предупреждение для этой ошибки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, измените уровень доступа члена на закрытый или сделайте тип наследуемым.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если оставить тип в его текущем состоянии может привести к проблемам в обслуживании и не предоставляет никаких преимуществ.

## <a name="example"></a>Пример
 В следующем примере показано тип, нарушающий это правило.

 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]