---
title: "CA2141: прозрачные методы не должны удовлетворять требования LinkDemand | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 938bda4d4b5c96b9627cf11aae81c51d269c0e5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: прозрачные методы не должны удовлетворять требования LinkDemand
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Прозрачный для безопасности метод вызывает метод в сборке, не помеченной атрибутом <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) атрибута или прозрачный для безопасности метод удовлетворяет <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` для типа или метода.  
  
## <a name="rule-description"></a>Описание правила  
 Удовлетворение требования LinkDemand является критически важные для операции безопасности, что может привести к непреднамеренному повышению уровня привилегий. Прозрачный для системы безопасности код не должны удовлетворять требования LinkDemand, так как он не может быть те же требования аудита безопасности, что и критический код безопасности. Прозрачные методы в сборках уровня 1 набора правил безопасности приведет все требования LinkDemand, они удовлетворяют должно быть преобразовано в полные требования во время выполнения, что может привести к снижению производительности. В сборках 2 уровня набора правил безопасности прозрачные методы не компилируется в компилятор just-in-time (JIT), если они пытаются удовлетворяет требованию LinkDemand.  
  
 В сборках, использующих безопасности уровня 2, попытки прозрачный для безопасности метод удовлетворяет требованию LinkDemand или вызвать метод в не APTCA сборки вызывает <xref:System.MethodAccessException>; в сборках уровня 1 LinkDemand, становятся полными требованиями.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, пометьте доступ к метод <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута, либо удалите LinkDemand из метода доступа.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В этом примере прозрачный метод пытается вызвать метод с помощью LinkDemand. Это правило срабатывает на этот код.  
  
 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]