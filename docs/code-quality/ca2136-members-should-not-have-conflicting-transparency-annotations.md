---
title: 'CA2136: элементы не должны иметь конфликтующие пометки прозрачности'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3af665f3a0f59cb1dd8c8c8ee581fc37f9da7e78
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550925"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: элементы не должны иметь конфликтующие пометки прозрачности
|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Это правило срабатывает, когда член типа помечается <xref:System.Security> атрибут безопасности, чем атрибут безопасности контейнера элемента прозрачности.

## <a name="rule-description"></a>Описание правила
 Атрибуты прозрачности применяются из элементов кода большей области к элементам меньшей области. Атрибуты прозрачности элементов кода с большей областью имеют приоритет по сравнению с атрибутами прозрачности элементов кода, которые содержатся в первом элементе. Например, класс, помеченный с <xref:System.Security.SecurityCriticalAttribute> атрибута не может содержать метод, отмеченный атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, удалите атрибут безопасности из элемента кода, с меньшей областью или измените его атрибут должен совпадать с элемент кода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует отключать предупреждения из этого правила.

## <a name="example"></a>Пример
 В следующем примере метод, помеченный атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> атрибут и он является членом класса, который помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> атрибута. Безопасный атрибут должны быть удалены.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]