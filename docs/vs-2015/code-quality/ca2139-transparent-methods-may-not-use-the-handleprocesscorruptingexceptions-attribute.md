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
ms.openlocfilehash: ea4f9dc11d2cbb3100ca6e2e0b3177b1acec923a
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173581"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139. Прозрачные методы могут не использовать атрибут HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|транспарентмесодсмустносандлепроцесскорруптинжексцептионс|
|CheckId|CA2139|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
 Прозрачный метод помечается <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибутом.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает для любого метода, который является прозрачным и пытается обработать поврежденное исключение с помощью <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибута. Исключение, приводящее к повреждению процесса, — это классификация CLR версии 4,0 исключений, таких как исключения <xref:System.AccessViolationException> . Атрибут HandleProcessCorruptedStateExceptionsAttribute может использоваться только критичными в плане безопасности методами и будет игнорироваться при применении для прозрачного метода. Для обработки исключений при повреждении процесса этот метод должен стать критически важным для безопасности или безопасным.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибут или пометьте метод <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом или.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В этом примере прозрачный метод помечается <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибутом и не сможет выполнить правило. Метод также должен быть помечен <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом или.

 [!code-csharp[FxCop.Security.CA2139#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139/cs/ca2139.cs#1)]
