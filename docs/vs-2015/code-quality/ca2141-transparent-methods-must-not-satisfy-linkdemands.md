---
title: 'CA2141: прозрачные методы не должны соответствовать требованиям LinkDemand | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bee810ed938d316e92095ad47062ed5ad9cd456f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546449"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: прозрачные методы не должны удовлетворять требования LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|транспарентмесодсмустнотсатисфилинкдемандс|
|CheckId|CA2141|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный с помощью безопасности метод вызывает метод в сборке, которая не помечена <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибутом (APTCA), или прозрачный для безопасности метод удовлетворяет <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` типу или методу.

## <a name="rule-description"></a>Описание правила
 Соблюдение требований LinkDemand — это операция, учитывающая безопасность, которая может привести к непреднамеренному повышению привилегий. Прозрачный для системы безопасности код не должен удовлетворять требования LinkDemand, так как он не подчиняется тем же требованиям аудита безопасности, что и критически важный для безопасности код. Прозрачные методы в сборках уровня 1 набора правил безопасности приведут к тому, что все LinkDemands, удовлетворяющие требованиям, будут преобразованы в полные требования во время выполнения, что может вызвать проблемы с производительностью. В сборках набора правил безопасности для сборок уровня 2 прозрачные методы не будут компилироваться в JIT-компиляторе, если они пытаются удовлетворить требования LinkDemand.

 В сборках, Уси безопасность уровня 2, попытки метода, прозрачного для безопасности, для удовлетворения LinkDemand или вызова метода в сборке, не являющейся APTCA, вызывают a <xref:System.MethodAccessException> ; в сборках уровня 1, требование LinkDemand является полным требованием.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте метод доступа <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом или или удалите LinkDemand из метода доступа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В этом примере прозрачный метод пытается вызвать метод, имеющий LinkDemand. Это правило будет срабатывать в этом коде.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
