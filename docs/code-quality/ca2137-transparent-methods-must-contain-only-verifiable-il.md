---
title: 'CA2137: Прозрачные методы должны содержать только проверяемые IL | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83c366bb69e25d128b190a9ee8b192f13cf61013
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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