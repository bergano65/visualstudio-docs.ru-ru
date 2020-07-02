---
title: 'CA2142: прозрачный код не должен быть защищен с помощью LinkDemand | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa6bd9dcacc5fb863199c740a71c824f14739052
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546436"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142. Прозрачный код не должен быть защищен проверками LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|транспарентмесодсшаулднотбепротектедвислинкдемандс|
|CheckId|CA2142|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Для прозрачного метода требуется <xref:System.Security.Permissions.SecurityAction> или другое требование безопасности.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает для прозрачных методов, для доступа к которым требуется LinkDemand. Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Поскольку прозрачные методы должны быть нейтральными к безопасности, они не должны принимать никаких решений в отношении безопасности. Кроме того, безопасный критически важный код, который принимает решения по безопасности, не должен полагаться на прозрачный код, чтобы ранее было сделано такое решение.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите требование компоновки для прозрачного метода или пометьте метод <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом, если он выполняет проверки безопасности, например требования безопасности.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере правило срабатывает для метода, так как метод является прозрачным и помечен с помощью LinkDemand <xref:System.Security.PermissionSet> , который содержит <xref:System.Security.Permissions.SecurityAction> .

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 Для этого правила отключать вывод предупреждений не следует.
