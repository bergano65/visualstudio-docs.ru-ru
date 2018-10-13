---
title: 'CA2141: прозрачные методы не должны удовлетворять требования LinkDemand | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b43c907870149d3b54ed3e129d0974f2417d387
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295806"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: прозрачные методы не должны удовлетворять требования LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный с точки безопасности метод вызывает метод в сборке, которая не помечен атрибутом <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибут (APTCA), или прозрачный метод безопасности удовлетворяет <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` для типа или метода.

## <a name="rule-description"></a>Описание правила
 Удовлетворение требования LinkDemand является важной операцией безопасности, что может привести к непреднамеренному повышению уровня привилегий. Прозрачный код безопасности не должны удовлетворять требования LinkDemand, так как он не распространяются те же требования аудита безопасности, что и критический код безопасности. Прозрачные методы в сборках уровня 1 набор правил безопасности приведет все требования LinkDemand, они удовлетворяют для преобразования в полные требования во время выполнения, что может привести к снижению производительности. В сборках уровня 2 набора правил безопасности прозрачные методы не удастся скомпилировать в компилятор just-in-time (JIT), если они пытаются выполнить удовлетворяет требованию LinkDemand.

 В сборках, использующих безопасность уровня 2, попытки прозрачного безопасности метод удовлетворяет требованию LinkDemand или вызвать метод в сборке, отличный от APTCA вызывает <xref:System.MethodAccessException>; в сборках уровня 1 LinkDemand, становятся полными требованиями.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте доступ к метод <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибут, или удалите LinkDemand из метода доступа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В этом примере прозрачный метод пытается вызвать метод, который имеет LinkDemand. Это правило срабатывает на этот код.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]



