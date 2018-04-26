---
title: 'CA2104: не объявляйте изменяемые ссылочные типы, доступные только для чтения'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 025905d77463bfbad59848ec876512dea311f619
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: не объявляйте изменяемые ссылочные типы, доступные только для чтения
|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Видимый извне тип содержит видимое извне и доступное только для чтение поле, являющееся изменяемым ссылочным типом.

## <a name="rule-description"></a>Описание правила
 Изменяемый тип — это тип, экземпляр которого может быть изменен. <xref:System.Text.StringBuilder?displayProperty=fullName> Класса является примером изменяемым ссылочным типом. Он содержит члены, которые могут изменять значение экземпляра класса. Пример неизменяемого ссылочного типа — <xref:System.String?displayProperty=fullName> класса. После его создания, его значение изменить нельзя.

 Модификатор доступа только для чтения ([readonly](/dotnet/csharp/language-reference/keywords/readonly) в C# [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], и [const](/cpp/cpp/const-cpp) в C++) для ссылочного типа поля (указателя в C++) запрещает поля заменены другой экземпляр ссылочного типа. Однако модификатор не запрещает данных экземпляра поля изменяется посредством ссылочного типа.

 Поля-массивы только для чтения будут исключены из этого правила, но вместо этого вызывают нарушение [CA2105: поля массивов не должны считываться только](../code-quality/ca2105-array-fields-should-not-be-read-only.md) правило.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, удалите модификатор доступа только для чтения, или, если допустима критическое изменение, замените поле неизменяемым типом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, если тип является неизменяемым.

## <a name="example"></a>Пример
 Следующий пример показывает объявление поля, которая приводит к нарушению данного правила.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]