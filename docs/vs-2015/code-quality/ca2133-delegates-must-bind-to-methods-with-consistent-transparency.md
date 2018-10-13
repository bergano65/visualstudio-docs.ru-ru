---
title: 'CA2133: Делегаты должны привязываться к методам с согласованной прозрачностью | Документация Майкрософт'
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
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67a03b1038b6f8b2d7ef323e4f48d9c5920f84bb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218696"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: делегаты должны привязываться к методам с согласованной прозрачностью
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

> [!NOTE]
>  Это предупреждение применяется только к коду, на котором работает CoreCLR (версия среды CLR, предназначенную для веб-приложений Silverlight).

## <a name="cause"></a>Причина
 Это предупреждение вызывается методом, который привязывает делегат, помеченный с <xref:System.Security.SecurityCriticalAttribute> в метод, который является прозрачным или помечен с помощью <xref:System.Security.SecuritySafeCriticalAttribute>. Предупреждение также запускает метод, который привязывает прозрачный или безопасный делегат к критическому методу.

## <a name="rule-description"></a>Описание правила
 Типы делегатов и методы, которые они привязаны к должны иметь согласованную прозрачность. Прозрачные и надежными с точки зрения делегаты только может привязываться к другой прозрачный или безопасный методы. Аналогичным образом критические делегатов может только привязать критические методы. Эти правила привязки убедитесь, что единственным кодом, который можно вызвать метод через делегат также может вызвать тот же метод напрямую. Например правила привязки запретить прозрачный код вызова кода critical непосредственно через прозрачный делегат.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого предупреждения, измените прозрачность делегата или метода, который привязывает таким образом, чтобы прозрачность двух эквивалентны.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]



