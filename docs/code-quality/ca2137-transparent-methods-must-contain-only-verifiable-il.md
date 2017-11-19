---
title: "CA2137: Прозрачные методы должны содержать только проверяемые IL | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 70a7574e0379c8e4b8dc9a888185efceb480fad4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: прозрачные методы должны содержать только проверяемые IL
|||  
|-|-|  
|TypeName|TransparentMethodsMustBeVerifiable|  
|CheckId|CA2137|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Метод содержит непроверяемый код или возвращает тип по ссылке.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило срабатывает при попытках прозрачного кода безопасности выполнить непроверяемый MSIL. Однако это правило не содержит полную проверку IL, и вместо нее использует эвристику для выявления большинства нарушений проверки MSIL.  
  
 Чтобы быть уверенным, что код содержит только проверяемый код MSIL, запустите [Peverify.exe (средство PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) сборки. Запустите PEVerify с **/ transparent** параметр, который ограничивает выходные данные только непроверяемый прозрачных методов, которым приведет к возникновению ошибки. Если / прозрачный параметр не используется, то PEVerify также проверяет критически важных методов, которые могут содержать непроверяемый код.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, пометьте метод <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута, либо удалите непроверяемый код.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В данном примере метод использует непроверяемый код и должны быть помечены <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.  
  
 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]