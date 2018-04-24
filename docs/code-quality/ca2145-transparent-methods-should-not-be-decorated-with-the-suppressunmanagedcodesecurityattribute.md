---
title: 'CA2145: прозрачные методы не должны быть снабжены атрибутом SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 072aa9a7b77441fbd2d742209e6221cd74fd6bf1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: прозрачные методы не должны быть снабжены атрибутом SuppressUnmanagedCodeSecurityAttribute
|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод, метод, который отмечен атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> метода или типа, содержащего метод помечается <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибута.

## <a name="rule-description"></a>Описание правила
 Методы, имеющие <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибута имеют неявную проверку LinkDemand после любой метод, который вызывает ее. Для этой проверки LinkDemand требуется, чтобы вызывающий код был критическим с точки зрения безопасности. Пометка метода, который использует SuppressUnmanagedCodeSecurity с <xref:System.Security.SecurityCriticalAttribute> атрибут, делает это требование более очевидным для метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, пометьте метод или тип с <xref:System.Security.SecurityCriticalAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]

### <a name="comments"></a>Комментарии