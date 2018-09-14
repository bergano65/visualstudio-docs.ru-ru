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
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 80d40dd60b0a6b6e507b903fd7a6185c5419422e
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551696"
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
 Изменяемый тип — это тип, экземпляр которого может быть изменен. <xref:System.Text.StringBuilder?displayProperty=fullName> Класс является примером изменяемый ссылочный тип. Он содержит члены, которые можно изменить значение экземпляра класса. Примером неизменяемого ссылочного типа является <xref:System.String?displayProperty=fullName> класса. После его создания экземпляра, его значение изменить нельзя.

 Модификатор доступа только для чтения ([readonly](/dotnet/csharp/language-reference/keywords/readonly) в C# [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], и [const](/cpp/cpp/const-cpp) в C++) на ссылочный тип поля (указатель в C++) позволяет предотвратить поле заменены другой экземпляр ссылочного типа. Однако модификатор не препятствует данных экземпляра поля изменению посредством ссылочного типа.

 Поля только для чтения массивов будут исключены из этого правила, но вместо этого приведет к нарушению [CA2105: поля массивов не должны считываться только](../code-quality/ca2105-array-fields-should-not-be-read-only.md) правило.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите модификатор только для чтения, или, если допустима критическое изменение, замените поле неизменяемый тип.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если тип поля является неизменяемым.

## <a name="example"></a>Пример
 В следующем примере объявление поля, которое вызывает нарушение этого правила.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]