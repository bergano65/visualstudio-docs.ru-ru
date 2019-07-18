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
ms.openlocfilehash: a9269a0862dacf928cffb31f722f382271d5f0e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542123"
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