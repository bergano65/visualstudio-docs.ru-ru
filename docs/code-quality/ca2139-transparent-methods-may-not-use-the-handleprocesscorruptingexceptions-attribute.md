---
title: CA2139. Прозрачные методы могут не использовать атрибут HandleProcessCorruptingExceptions
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48f5e0649b9d59994098622d00c3cf23772a9d81
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987749"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139. Прозрачные методы могут не использовать атрибут HandleProcessCorruptingExceptions

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод помечен атрибутом <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибута.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает, любой метод, который является прозрачным и пытается обработать исключение повреждения процесса с помощью <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибута. Исключение повреждения процесса — это классификация версии 4.0 среды CLR таких исключений <xref:System.AccessViolationException>. Атрибут HandleProcessCorruptedStateExceptionsAttribute может использоваться только критичными в плане безопасности методами и будет игнорироваться при применении для прозрачного метода. Для обработки исключений повреждения процесса, этот метод должен быть критически важным для безопасности или надежным с точки зрения безопасности.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибут, или пометьте метод <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В этом примере помечается прозрачный метод <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибут и правило не удастся. Метод также должен быть помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]