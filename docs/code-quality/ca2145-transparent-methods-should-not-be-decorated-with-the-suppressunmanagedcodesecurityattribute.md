---
title: CA2145. Прозрачные методы не должны быть отмечены атрибутом SuppressUnmanagedCodeSecurityAttribute
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba7926f04f6112b28770110614fa18be88b028a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018167"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145. Прозрачные методы не должны быть отмечены атрибутом SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Прозрачный метод, метод, отмеченный атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> метода или типа, который содержит метод помечается <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибута.

## <a name="rule-description"></a>Описание правила

Методы снабжены атрибутом <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибута имеют неявную проверку LinkDemand, при любой метод, который ее вызывает. Для этой проверки LinkDemand требуется, чтобы вызывающий код был критическим с точки зрения безопасности. Пометка метода, который использует SuppressUnmanagedCodeSecurity с <xref:System.Security.SecurityCriticalAttribute> атрибут, делает это требование более очевидным для метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, пометьте метод или тип с <xref:System.Security.SecurityCriticalAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]