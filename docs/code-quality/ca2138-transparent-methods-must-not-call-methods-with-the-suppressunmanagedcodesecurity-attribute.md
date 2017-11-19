---
title: "CA2138: Прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cf17c69673649ac1f3af64bafcb718e8c84eb213
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: прозрачные методы не должны вызывать методы с атрибутом SuppressUnmanagedCodeSecurity
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Прозрачный для безопасности метод вызывает метод, помеченный <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибута.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило срабатывает для любого прозрачного метода, который вызывается непосредственно в машинном коде, например, с помощью через P/Invoke (неуправляемого) вызова. P/Invoke и COM-взаимодействия методы, помеченные с <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибута приведет к проверки LinkDemand для вызывающего метода. Поскольку прозрачный для системы безопасности код не может удовлетворить требования LinkDemand, код также не может вызывать методы, помеченные атрибутом SuppressUnmanagedCodeSecurity или методы класса, помеченного атрибутом SuppressUnmanagedCodeSecurity. Метод завершится с ошибкой или требования будут преобразованы в полное требование.  
  
 Нарушение этого правила приводит к <xref:System.MethodAccessException> в модели прозрачности безопасности уровня 2 и вызову полного требования <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> в модель прозрачности уровня 1.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибута и пометьте метод <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]