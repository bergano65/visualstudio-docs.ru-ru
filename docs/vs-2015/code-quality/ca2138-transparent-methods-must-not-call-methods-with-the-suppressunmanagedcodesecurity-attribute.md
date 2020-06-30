---
title: 'CA2138: прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 35cc152998b15a2fd4c4ff02e4730cdfae5366cb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546501"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138. Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|транспарентмесодсмустноткаллсуппрессунманажедкодесекуритимесодс|
|CheckId|CA2138|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный для системы безопасности метод вызывает метод, помеченный <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибутом.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает для любого прозрачного метода, который вызывает непосредственно в машинный код, например с помощью вызова P/Invoke (вызов неуправляемого кода). Методы P/Invoke и COM-взаимодействия, помеченные с помощью атрибута, являются <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> результатом LinkDemand для вызывающего метода. Поскольку прозрачный для системы безопасности код не может удовлетворить требования LinkDemand, код также не может вызывать методы, помеченные атрибутом SuppressUnmanagedCodeSecurity, или методы класса, помеченные атрибутом SuppressUnmanagedCodeSecurity. Метод завершится ошибкой, или требование будет преобразовано в полное требование.

 Нарушение этого правила приводит к тому, что <xref:System.MethodAccessException> в модели прозрачности безопасности уровня 2 и полном требовании для <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> модели прозрачности уровня 1.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибут и пометьте метод <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом или.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
