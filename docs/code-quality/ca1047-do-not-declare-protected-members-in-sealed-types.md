---
title: CA1047. Не объявляйте защищенные члены в запечатанных типах
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5ab7cf2c5a4f17966ed5b4da30657e05a4683738
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922648"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047. Не объявляйте защищенные члены в запечатанных типах

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Открытый тип — `sealed` (`NotInheritable` в Visual Basic) и объявляет защищенный член или защищенный вложенный тип. Это правило не сообщает о нарушениях <xref:System.Object.Finalize%2A> для методов, которые должны следовать этому шаблону.

## <a name="rule-description"></a>Описание правила
Типы объявляют защищенный члены таким образом, чтобы наследующие типы могли получить доступ к члену или переопределить его. По определению нельзя наследовать от запечатанного типа. Это означает, что нельзя вызывать защищенные методы в запечатанных типах.

C# Компилятор выдает предупреждение для этой ошибки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, измените уровень доступа элемента на частный или сделайте тип наследуемым.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует. Если оставить тип в его текущем состоянии, это может вызвать проблемы с обслуживанием и не дает никаких преимуществ.

## <a name="example"></a>Пример
В следующем примере показан тип, нарушающий это правило.

[!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
[!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]