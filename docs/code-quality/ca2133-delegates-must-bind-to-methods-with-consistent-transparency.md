---
title: "CA2133: Делегаты должны привязываться к методам с согласованной прозрачностью | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f191c9f67fd09e72d4cb57ded2fa88135c388611
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: делегаты должны привязываться к методам с согласованной прозрачностью
|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
> [!NOTE]
>  Это предупреждение применяется только для кода, выполняющего CoreCLR (версия среды CLR, предназначенную для веб-приложений Silverlight).  
  
## <a name="cause"></a>Причина  
 Это предупреждение вызывается методом, который привязывает делегат, помеченный <xref:System.Security.SecurityCriticalAttribute> в метод, который является прозрачным или помечен с <xref:System.Security.SecuritySafeCriticalAttribute>. Предупреждение также запускает метод, который привязывает прозрачный или безопасный делегат к критическому методу.  
  
## <a name="rule-description"></a>Описание правила  
 Типы делегатов и методы, которые они не привязаны к должны иметь согласованную прозрачность. Прозрачный и критический делегаты привязан только к другим прозрачным или критическим методам. Аналогичным образом критические делегаты может только привязать критически важных методов. Эти правила привязки гарантируют, что только код, который можно вызвать метод через делегат также может вызвать тот же метод непосредственно. Например правила привязки запретить вызов критического кода непосредственно через прозрачный делегат прозрачного кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого предупреждения, измените прозрачность делегата или метода, он выполняет привязку, чтобы прозрачность двух эквивалентны.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
### <a name="code"></a>Код  
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]