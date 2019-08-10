---
title: CA2138. Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 316aef3b0f1f715857fde8eaf2a6e74b1a49e40f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920578"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138. Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity

|||
|-|-|
|TypeName|транспарентмесодсмустноткаллсуппрессунманажедкодесекуритимесодс|
|CheckId|CA2138|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
Прозрачный для системы безопасности метод вызывает метод, помеченный <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибутом.

## <a name="rule-description"></a>Описание правила
Это правило срабатывает для любого прозрачного метода, который вызывает непосредственно в машинный код, например с помощью вызова P/Invoke (вызов неуправляемого кода). Методы P/Invoke и COM-взаимодействия, помеченные с <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> помощью атрибута, являются результатом LinkDemand для вызывающего метода. Поскольку прозрачный для системы безопасности код не может удовлетворить требования LinkDemand, код также не может вызывать методы, помеченные атрибутом SuppressUnmanagedCodeSecurity, или методы класса, помеченные атрибутом SuppressUnmanagedCodeSecurity. Метод завершится ошибкой, или требование будет преобразовано в полное требование.

Нарушение этого правила приводит к <xref:System.MethodAccessException> тому, что в модели прозрачности безопасности уровня 2 и полном требовании для <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> модели прозрачности уровня 1.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, удалите <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибут и пометьте метод <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом или.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
[!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]