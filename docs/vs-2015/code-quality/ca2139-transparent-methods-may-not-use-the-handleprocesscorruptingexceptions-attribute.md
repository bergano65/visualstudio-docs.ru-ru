---
title: 'CA2139: прозрачные методы не могут использовать атрибут HandleProcessCorruptingExceptions | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 821598d7708fa8681f1dbc5fee65978d7498dbb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602994"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: прозрачные методы могут не использовать атрибут HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|транспарентмесодсмустносандлепроцесскорруптинжексцептионс|
|CheckId|CA2139|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод помечается атрибутом <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает для любого метода, который является прозрачным и пытается обработать поврежденное исключение с помощью атрибута <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>. Исключение, приводящее к повреждению процесса, представляет собой классификацию исключения CLR версии 4,0, например <xref:System.AccessViolationException>. Атрибут HandleProcessCorruptedStateExceptionsAttribute может использоваться только критичными в плане безопасности методами и будет игнорироваться при применении для прозрачного метода. Для обработки исключений при повреждении процесса этот метод должен стать критически важным для безопасности или безопасным.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите атрибут <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> или пометьте метод атрибутом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В этом примере прозрачный метод помечается атрибутом <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> и не приведет к сбою правила. Метод также должен быть помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute>.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]
