---
title: 'CA2137: прозрачные методы должны содержать только проверяемый IL | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: be3732fbf1fc01deb18d2af6a183d47e618db337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602987"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: прозрачные методы должны содержать только проверяемые IL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|транспарентмесодсмустбеверифиабле|
|CheckId|CA2137|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод содержит непроверяемый код или возвращает тип по ссылке.

## <a name="rule-description"></a>Описание правила
 Это правило срабатывает при попытках прозрачного кода безопасности выполнить непроверяемый MSIL. Однако это правило не содержит полную проверку IL, и вместо нее использует эвристику для выявления большинства нарушений проверки MSIL.

 Чтобы убедиться, что код содержит только проверяемый MSIL, запустите сборку с помощью команды [Peverify. exe (peverify)](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) . Выполните PEVerify с параметром **/Транспарент** , который ограничивает выходные данные только непроверяемыми прозрачными методами, которые могут вызвать ошибку. Если параметр/Транспарент не используется, PEVerify также проверяет критические методы, которые могут содержать непроверяемый код.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте метод атрибутом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute> или удалите непроверяемый код.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Метод в этом примере использует непроверяемый код и должен быть помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute>.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
