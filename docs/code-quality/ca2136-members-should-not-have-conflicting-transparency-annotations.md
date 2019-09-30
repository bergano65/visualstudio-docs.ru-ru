---
title: CA2136. Члены не должны иметь противоречащие заметки прозрачности
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f9455e83d7cb128a34696ae5e849fd0901f1891
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232220"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136. Члены не должны иметь противоречащие заметки прозрачности

|||
|-|-|
|TypeName|транспаренцианнотатионсшаулднотконфликт|
|CheckId|CA2136|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Это правило срабатывает, если член типа помечен атрибутом <xref:System.Security> безопасности с разной прозрачностью, чем атрибут безопасности контейнера элемента.

## <a name="rule-description"></a>Описание правила
Атрибуты прозрачности применяются из элементов кода большей области к элементам меньшей области. Атрибуты прозрачности элементов кода с большей областью имеют приоритет по сравнению с атрибутами прозрачности элементов кода, которые содержатся в первом элементе. Например, класс, помеченный <xref:System.Security.SecurityCriticalAttribute> атрибутом, не может содержать метод, помеченный <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить это нарушение, удалите атрибут безопасности из элемента Code с более ранней областью или измените его атрибут так, чтобы он совпадал с содержащим элементом кода.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Не отключайте вывод предупреждений из этого правила.

## <a name="example"></a>Пример
В следующем примере метод помечен <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом и является членом класса, помеченного <xref:System.Security.SecurityCriticalAttribute> атрибутом. Безопасный атрибут безопасности следует удалить.

[!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]