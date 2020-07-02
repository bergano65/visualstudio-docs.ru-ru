---
title: 'CA2149: прозрачные методы не должны вызывать машинный код | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c1e254ae7912efbb6773155ed834e54a1db1832
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546332"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149. Прозрачные методы не должны вызывать машинный код
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|транспарентмесодсмустноткаллнативекоде|
|CheckId|CA2149|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод вызывает собственную функцию через заглушку метода, например P/Invoke.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает для любого прозрачного метода, который вызывается непосредственно в машинном коде, например, с помощью вызова P/Invoke. Нарушение этого правила приводит к тому, что <xref:System.MethodAccessException> в модели прозрачности уровня 2 и полное требование для <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> модели прозрачности уровня 1.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте метод, который вызывает машинный код с помощью <xref:System.Security.SecurityCriticalAttribute> атрибута или <xref:System.Security.SecuritySafeCriticalAttribute> .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode/cs/ca2149 - transparentmethodsmustnotcallnativecode.cs#1)]
