---
title: CA2139. Прозрачные методы не могут использовать атрибут HandleProcessCorruptingExceptions | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a05813d01a05c02455d43e74029251e96e4e4580
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154279"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139. Прозрачные методы могут не использовать атрибут HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]
