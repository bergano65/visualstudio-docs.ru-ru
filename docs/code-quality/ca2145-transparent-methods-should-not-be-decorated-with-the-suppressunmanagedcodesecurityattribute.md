---
title: CA2145. Прозрачные методы не должны быть отмечены атрибутом SuppressUnmanagedCodeSecurityAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cca385c346a7daa8aaddb377f999506ffb1abaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232041"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145. Прозрачные методы не должны быть отмечены атрибутом SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|транспарентмесодсшаулднотусесуппрессунманажедкодесекурити|
|CheckId|CA2145|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:

Прозрачный метод, метод, помеченный <xref:System.Security.SecuritySafeCriticalAttribute> методом, или тип, содержащий метод, помечены <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибутом.

## <a name="rule-description"></a>Описание правила

Методы, отмеченные атрибутом, имеют неявное требование LinkDemand, накладываемое любым методом, который его вызывает. <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> Для этой проверки LinkDemand требуется, чтобы вызывающий код был критическим с точки зрения безопасности. Пометка метода, использующего SuppressUnmanagedCodeSecurity с <xref:System.Security.SecurityCriticalAttribute> атрибутом, делает это требование более очевидным для вызывающих объектов метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, пометьте метод или тип <xref:System.Security.SecurityCriticalAttribute> атрибутом.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]